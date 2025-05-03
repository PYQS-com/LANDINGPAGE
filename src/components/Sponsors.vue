<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { useColorMode } from "@vueuse/core";

// Use the same theme system as the rest of the app
const mode = useColorMode();

// Store direction state
const direction1 = ref('rtl'); // 'rtl' or 'ltr'
const direction2 = ref('ltr'); // 'ltr' or 'rtl'
const isScrolling = ref(false);
const lastScrollY = ref(0);

// Animation speed controls
const speed1 = ref(30); // seconds to complete one cycle
const speed2 = ref(30); // seconds to complete one cycle
const baseSpeed = 30; // base speed when not scrolling
const scrollingSpeed = 15; // faster speed when scrolling

// Handle scroll direction detection
function handleScroll() {
  const currentScrollY = window.scrollY;
  const scrollingDown = currentScrollY > lastScrollY.value;
  
  // Change directions based on scroll direction
  if (scrollingDown) {
    direction1.value = 'ltr';
    direction2.value = 'rtl';
  } else {
    direction1.value = 'rtl';
    direction2.value = 'ltr';
  }
  
  // Speed up animation while scrolling
  speed1.value = scrollingSpeed;
  speed2.value = scrollingSpeed;
  
  // Update last scroll position
  lastScrollY.value = currentScrollY;
  
  // Set scrolling state
  clearTimeout(window.scrollTimeout);
  isScrolling.value = true;
  window.scrollTimeout = setTimeout(() => {
    isScrolling.value = false;
    // Reset to base speed when not scrolling
    speed1.value = baseSpeed;
    speed2.value = baseSpeed;
  }, 200);
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  lastScrollY.value = window.scrollY;
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
  clearTimeout(window.scrollTimeout);
});
</script>

<template>
  <section class="w-full py-8 bg-background">
    <div class="overflow-hidden flex flex-col gap-4">
      <!-- First marquee -->
      <div class="marquee-container">
        <div class="marquee-track" :class="direction1" :style="{ animationDuration: `${speed1}s` }">
          <!-- First copy of content -->
          <div class="marquee-content">
            <span class="marquee-item">NEET PG <span class="marquee-emoji">🔥</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">SMART PREPARATION <span class="marquee-emoji">🐧</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">NEET PG <span class="marquee-emoji">🔥</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">SMART PREPARATION <span class="marquee-emoji">🐧</span></span>
            <span class="marquee-sep">•</span>
          </div>
          <!-- Second copy of same content for seamless loop -->
          <div class="marquee-content">
            <span class="marquee-item">NEET PG <span class="marquee-emoji">🔥</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">SMART PREPARATION <span class="marquee-emoji">🐧</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">NEET PG <span class="marquee-emoji">🔥</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">SMART PREPARATION <span class="marquee-emoji">🐧</span></span>
            <span class="marquee-sep">•</span>
          </div>
        </div>
      </div>

      <!-- Second marquee -->
      <div class="marquee-container">
        <div class="marquee-track" :class="direction2" :style="{ animationDuration: `${speed2}s` }">
          <!-- First copy of content -->
          <div class="marquee-content">
            <span class="marquee-item">AI POWERED <span class="marquee-emoji">🤖</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">MCQS <span class="marquee-emoji">❓</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">AI POWERED <span class="marquee-emoji">🤖</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">MCQS <span class="marquee-emoji">❓</span></span>
            <span class="marquee-sep">•</span>
          </div>
          <!-- Second copy of same content for seamless loop -->
          <div class="marquee-content">
            <span class="marquee-item">AI POWERED <span class="marquee-emoji">🤖</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">MCQS <span class="marquee-emoji">❓</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">AI POWERED <span class="marquee-emoji">🤖</span></span>
            <span class="marquee-sep">•</span>
            <span class="marquee-item">MCQS <span class="marquee-emoji">❓</span></span>
            <span class="marquee-sep">•</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.marquee-container {
  width: 100vw;
  overflow: hidden;
  position: relative;
}

.marquee-track {
  display: flex;
  width: fit-content;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-name: scroll-rtl;
}

.marquee-track.rtl {
  animation-name: scroll-rtl;
}

.marquee-track.ltr {
  animation-name: scroll-ltr;
}

.marquee-content {
  display: flex;
  align-items: center;
  white-space: nowrap;
  flex-shrink: 0;
}

.marquee-item {
  font-weight: 700;
  font-size: 130px;
  line-height: 1;
  letter-spacing: 0.01em;
  margin: 0 2.5rem;
  color: hsl(var(--foreground));
  user-select: none;
}

.marquee-emoji {
  font-size: 1.2em;
  vertical-align: middle;
  margin-left: 0.2em;
}

.marquee-sep {
  color: hsl(var(--muted-foreground));
  font-size: 1.5em;
  margin: 0 1.5rem;
  vertical-align: middle;
}

@keyframes scroll-rtl {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

@keyframes scroll-ltr {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(0);
  }
}

@media (max-width: 640px) {
  .marquee-item {
    font-size: 70px;
    margin: 0 1rem;
  }
  .marquee-sep {
    margin: 0 0.7rem;
  }
}
</style>
