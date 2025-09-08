<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

defineProps({
  content: {
    type: String,
    required: true
  },
  speed: {
    type: Number,
    default: 50 // pixels per second
  },
  alternateRows: {
    type: Boolean,
    default: true
  },
  className: {
    type: String,
    default: ''
  }
})

const container = ref<HTMLElement | null>(null)
const scrollDirection = ref(1) // 1 for down, -1 for up
const lastScrollTop = ref(0)
const sections = ref<{ direction: number; element: HTMLElement | null }[]>([
  { direction: 1, element: null }, // left to right
  { direction: -1, element: null } // right to left
])

// Track scroll direction
function handleScroll() {
  const st = window.scrollY
  if (st > lastScrollTop.value) {
    scrollDirection.value = 1 // scrolling down
  } else {
    scrollDirection.value = -1 // scrolling up
  }
  lastScrollTop.value = st
  
  // Update scroll animations based on direction
  updateScrollAnimation()
}

// Update scroll positions based on current direction
function updateScrollAnimation() {
  sections.value.forEach((section) => {
    if (!section.element) return
    
    // Base direction for the section
    let effectiveDirection = section.direction
    
    // If scrolling up, reverse the direction
    if (scrollDirection.value === -1) {
      effectiveDirection *= -1
    }
    
    // Apply the animation with the correct direction
    section.element.style.animationDirection = effectiveDirection > 0 ? 'normal' : 'reverse'
  })
}

onMounted(() => {
  // Set up scroll detection
  window.addEventListener('scroll', handleScroll)
  
  // Get the section elements
  if (container.value) {
    const sectionElements = container.value.querySelectorAll('.infinite-scroll-section')
    sections.value.forEach((section, index) => {
      if (sectionElements[index]) {
        section.element = sectionElements[index] as HTMLElement
      }
    })
  }
  
  // Initialize animations
  updateScrollAnimation()
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div ref="container" :class="['infinite-scroll-container', className]">
    <!-- First row: left to right by default -->
    <div class="infinite-scroll-section">
      <div class="infinite-scroll-content">
        <div class="scroll-item" v-for="i in 10" :key="'row1-'+i">{{ content }}</div>
      </div>
      <div class="infinite-scroll-content" aria-hidden="true">
        <div class="scroll-item" v-for="i in 10" :key="'row1-copy-'+i">{{ content }}</div>
      </div>
    </div>
    
    <!-- Second row: right to left by default -->
    <div class="infinite-scroll-section reverse">
      <div class="infinite-scroll-content">
        <div class="scroll-item" v-for="i in 10" :key="'row2-'+i">{{ content }}</div>
      </div>
      <div class="infinite-scroll-content" aria-hidden="true">
        <div class="scroll-item" v-for="i in 10" :key="'row2-copy-'+i">{{ content }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.infinite-scroll-container {
  width: 100%;
  overflow: hidden;
}

.infinite-scroll-section {
  display: flex;
  width: 100%;
  overflow: hidden;
}

.infinite-scroll-section.reverse {
  flex-direction: row-reverse;
}

.infinite-scroll-content {
  display: flex;
  white-space: nowrap;
  animation: scroll 20s linear infinite;
}

.scroll-item {
  padding: 1rem;
  display: inline-block;
}

.infinite-scroll-section.reverse .infinite-scroll-content {
  animation-direction: reverse;
}

@keyframes scroll {
  from {
    transform: translateX(0%);
  }
  to {
    transform: translateX(-100%);
  }
}
</style>