<!-- components/ui/text-animate.vue -->
<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useIntersectionObserver } from '@vueuse/core'

const props = defineProps({
  as: {
    type: String,
    default: 'p',
  },
  by: {
    type: String,
    default: 'word',
    validator: (value: string) => ['text', 'word', 'character', 'line'].includes(value),
  },
  children: {
    type: String,
    required: true,
  },
  animation: {
    type: String,
    default: 'fadeIn', // not used now, but kept for reference
  },
  delay: {
    type: Number,
    default: 0,
  },
  duration: {
    type: Number,
    default: 0.5, // half-second fade
  },
  startOnView: {
    type: Boolean,
    default: true,
  },
  once: {
    type: Boolean,
    default: false,
  },
  className: {
    type: String,
    default: '',
  },
})

const target = ref<HTMLElement | null>(null)
const isInView = ref(false)

// Split text
const elements = computed(() => {
  if (props.by === 'text') return [props.children]
  if (props.by === 'word') return props.children.split(' ')
  if (props.by === 'character') return props.children.split('')
  if (props.by === 'line') return props.children.split('\n')
  return [props.children]
})

const animatedElements = ref(elements.value.map(() => false))

const { stop } = useIntersectionObserver(
  target,
  ([{ isIntersecting }]) => {
    if (isIntersecting) {
      isInView.value = true
      if (props.once) stop()
    } else if (!props.once) {
      isInView.value = false
    }
  },
  { threshold: 0.1 }
)

// For each piece of text, we update animatedElements after a delay
function triggerAnimation(index: number) {
  setTimeout(() => {
    animatedElements.value[index] = true
  }, props.delay * 1000 + index * (props.duration * 400)) // More consistent timing between words
}

// Function to set data-text attribute for gradient effect
function setDataAttributes() {
  if (target.value) {
    // Set the data-text attribute to match the text content
    const spans = target.value.querySelectorAll('span');
    spans.forEach((span: HTMLElement) => {
      span.setAttribute('data-text', span.textContent || '');
    });
  }
}

// If startOnView = false, animate immediately
onMounted(() => {
  if (!props.startOnView) {
    elements.value.forEach((_, i) => triggerAnimation(i))
  }
  
  // Set data attributes for SVG gradient effect
  setDataAttributes();
})

// Returns dynamic classes to handle fade/slide
function getAnimationClasses(index: number) {
  if (props.startOnView && isInView.value && !animatedElements.value[index]) {
    triggerAnimation(index)
  }

  const marginRight = props.by === 'character' ? '' : 'mr-1'
  
  // Improve transition with better easing - use cubic-bezier for smoother effect
  const baseTransition = `inline-block transition-all duration-500 ease-[cubic-bezier(0.25,0.1,0.25,1)] ${marginRight}`
  
  // Better transformation for smoother animation
  return animatedElements.value[index]
    ? `${baseTransition} translate-y-0 opacity-100` 
    : `${baseTransition} translate-y-2 opacity-0` // Smaller offset for more subtle effect
}
</script>

<template>
  <component
    :is="as"
    ref="target"
    :class="props.className" 
  >
    <template v-if="by === 'word'">
      <span
        v-for="(word, index) in elements"
        :key="index"
        :class="getAnimationClasses(index)" 
      >
        {{ word }}&nbsp;
      </span>
    </template>

    <template v-else-if="by === 'character'">
      <span
        v-for="(char, index) in elements"
        :key="index"
        :class="getAnimationClasses(index)"
      >
        {{ char }}
      </span>
    </template>

    <template v-else-if="by === 'line'">
      <div
        v-for="(line, index) in elements"
        :key="index"
        :class="getAnimationClasses(index)"
      >
        {{ line }}
      </div>
    </template>

    <template v-else>
      <!-- fallback for 'text' or any other -->
      <span
        :class="getAnimationClasses(0)" 
      >
        {{ children }}
      </span>
    </template>
  </component>
</template>
