<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount, computed } from 'vue';

const mouseX = ref(0);
const mouseY = ref(0);
const cursorX = ref(0);
const cursorY = ref(0);
const isHovering = ref(false);
const isClicking = ref(false);
const isVisible = ref(false);
const cursorText = ref('');

// Smoothing factor for cursor movement
const smoothFactor = 0.16;

// Cursor state classes
const cursorClasses = computed(() => ({
  'cursor-visible': isVisible.value,
  'cursor-hovering': isHovering.value,
  'cursor-clicking': isClicking.value,
}));

// Smooth animation loop
const updateCursorPosition = () => {
  const diffX = mouseX.value - cursorX.value;
  const diffY = mouseY.value - cursorY.value;
  
  cursorX.value += diffX * smoothFactor;
  cursorY.value += diffY * smoothFactor;
  
  requestAnimationFrame(updateCursorPosition);
};

// Mouse tracking
const handleMouseMove = (e: MouseEvent) => {
  mouseX.value = e.clientX;
  mouseY.value = e.clientY;
  
  if (!isVisible.value) {
    isVisible.value = true;
  }
};

const handleMouseDown = () => {
  isClicking.value = true;
};

const handleMouseUp = () => {
  isClicking.value = false;
};

// Interactive element tracking
const setupHoverListeners = () => {
  const interactiveElements = document.querySelectorAll(
    'a, button, [role="button"], input, select, textarea, .clickable, [tabindex="0"]'
  );
  
  interactiveElements.forEach(element => {
    element.addEventListener('mouseenter', () => {
      isHovering.value = true;
      
      const customText = element.getAttribute('data-cursor-text');
      if (customText) {
        cursorText.value = customText;
      }
    });
    
    element.addEventListener('mouseleave', () => {
      isHovering.value = false;
      cursorText.value = '';
    });
  });
};

// Hide system cursor on all elements
const hideSystemCursor = () => {
  // Create a style element
  const styleEl = document.createElement('style');
  styleEl.textContent = `
    * {
      cursor: none !important;
    }
    
    /* Ensure links and buttons don't show default cursor */
    a, button, [role="button"], input, select, textarea, .clickable, [tabindex="0"] {
      cursor: none !important;
    }
  `;
  document.head.appendChild(styleEl);
  
  return () => {
    document.head.removeChild(styleEl);
  };
};

onMounted(() => {
  const removeStyle = hideSystemCursor();
  
  window.addEventListener('mousemove', handleMouseMove);
  window.addEventListener('mousedown', handleMouseDown);
  window.addEventListener('mouseup', handleMouseUp);
  
  setupHoverListeners();
  updateCursorPosition();
  
  // Store cleanup function
  onBeforeUnmount(() => {
    removeStyle();
    
    window.removeEventListener('mousemove', handleMouseMove);
    window.removeEventListener('mousedown', handleMouseDown);
    window.removeEventListener('mouseup', handleMouseUp);
  });
});
</script>

<template>
  <div class="cursor-container">
    <!-- Main cursor with simple circle -->
    <div
      class="cursor-circle"
      :class="cursorClasses"
      :style="{ transform: `translate(${cursorX}px, ${cursorY}px)` }"
    >
      <!-- Text tooltip -->
      <span v-if="cursorText" class="cursor-text">{{ cursorText }}</span>
    </div>
    
    <!-- Small dot for precise pointing -->
    <div
      class="cursor-dot"
      :class="cursorClasses"
      :style="{ transform: `translate(${cursorX}px, ${cursorY}px)` }"
    ></div>
    
    <!-- Pulse effect -->
    <div
      class="cursor-pulse"
      :class="cursorClasses"
      :style="{ transform: `translate(${cursorX}px, ${cursorY}px)` }"
    ></div>
  </div>
</template>

<style scoped>
.cursor-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 9999;
  overflow: hidden;
}

/* Simple circular cursor */
.cursor-circle {
  position: fixed;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  background: rgba(140, 56, 234, 0.3);
  border: 2px solid rgba(140, 56, 234, 0.8);
  transition: width 0.3s ease, height 0.3s ease, opacity 0.2s ease;
  will-change: transform, opacity;
  backdrop-filter: blur(5px);
}

/* Small central dot */
.cursor-dot {
  position: fixed;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: #ffffff;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: opacity 0.25s ease;
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.8);
  will-change: transform;
  z-index: 2;
}

/* Pulse effect */
.cursor-pulse {
  position: fixed;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  background: rgba(140, 56, 234, 0.2);
  animation: pulse-fade 1.5s ease-out infinite;
  will-change: transform, opacity;
}

@keyframes pulse-fade {
  0% {
    opacity: 0.3;
    transform: translate(-50%, -50%) scale(0.5);
  }
  100% {
    opacity: 0;
    transform: translate(-50%, -50%) scale(2);
  }
}

/* Visibility and interaction states */
.cursor-visible {
  opacity: 1;
}

.cursor-hovering.cursor-circle {
  width: 30px;
  height: 30px;
  background: rgba(140, 56, 234, 0.2);
  border-color: rgba(140, 56, 234, 1);
  transition: all 0.3s ease;
}

.cursor-clicking.cursor-circle {
  width: 15px;
  height: 15px;
  background: rgba(140, 56, 234, 0.5);
  border-color: rgba(140, 56, 234, 1);
  transition-duration: 0.1s;
}

/* Text that appears when hovering over interactive elements */
.cursor-text {
  position: absolute;
  top: -30px;
  font-size: 11px;
  font-weight: 600;
  color: white;
  text-transform: uppercase;
  letter-spacing: 1px;
  white-space: nowrap;
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
  background: rgba(140, 56, 234, 0.9);
  padding: 4px 10px;
  border-radius: 8px;
  transform: translateY(0);
  animation: float 2s ease-in-out infinite;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

@keyframes float {
  0% { transform: translateY(0); }
  50% { transform: translateY(-5px); }
  100% { transform: translateY(0); }
}

/* Disable on mobile/touch devices */
@media (max-width: 768px) {
  .cursor-container {
    display: none;
  }
}
</style>