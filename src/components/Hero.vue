<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useColorMode } from "@vueuse/core";
const mode = useColorMode();

import { Badge } from "@/components/ui/badge";
import { Button } from "@/components/ui/button";
import { ArrowRight } from "lucide-vue-next";
import sunglassesEmoji from "@/assets/GIFS/SUNGLASS.png"
import desktopScreenshot from "@/assets/DESKTOPSS.png"

const platformFeatures = ref([
  { text: "Mock Tests", color: "purple-gradient" },
  { text: "Study Notes", color: "green-gradient" },
  { text: "Quick Reviews", color: "blue-gradient" },
  { text: "PYQs", color: "pink-gradient" },
  { text: "One-Shots", color: "one-shot-gradient" }
]);
const currentFeatureIndex = ref(0);

const examTypes = ref([
  { text: "NEET PG", color: "gradient-text" },
  { text: "INI-CET", color: "gradient-text" },
  { text: "FMGE", color: "gradient-text" }
]);
const currentExamIndex = ref(0);

onMounted(() => {
  setInterval(() => {
    currentFeatureIndex.value = (currentFeatureIndex.value + 1) % platformFeatures.value.length;
  }, 2000);
  
  setInterval(() => {
    currentExamIndex.value = (currentExamIndex.value + 1) % examTypes.value.length;
  }, 3000);
});
</script>

<template>
  <section class="container">
    <div class="grid place-items-center lg:max-w-screen-xl gap-8 mx-auto py-20 md:py-32">
      <!-- Hero section with improved radial gradient background -->
      <div class="text-center space-y-8 relative overflow-visible">
        <!-- Soft, spread, elliptical radial gradient, hidden in dark mode -->
        <div
          class="absolute inset-0 pointer-events-none -z-10"
          v-if="mode === 'light'"
        >
          <div class="hero-blob-bg"></div>
        </div>

        <Badge variant="outline" class="text-sm py-2 relative z-10 bg-white dark:bg-black">
          <span> ✨ Welcome to PYQS.com </span>
        </Badge>

        <div class="max-w-screen-md mx-auto text-center font-bold relative z-10">
          <h1 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl xl:text-7xl font-extrabold leading-tight">
            Ace 
            <span class="gradient-text rotating-text-inline" :key="currentExamIndex">
              {{ examTypes[currentExamIndex].text }}
            </span>
            <img :src="sunglassesEmoji" alt="Sunglasses Emoji" class="sunglasses-emoji ml-2"/>
            <br class="block" />
            <span class="gradient-text-opp text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl"> Previous Year Questions</span>
          </h1>
        </div>

        <p class="max-w-screen-sm mx-auto text-lg sm:text-xl md:text-2xl font-medium text-muted-foreground relative z-10">
          Your all-in-one learning platform for 
          <span class="font-semibold" :class="platformFeatures[currentFeatureIndex].color">
            {{ platformFeatures[currentFeatureIndex].text }}
          </span>
        </p>

        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center relative z-10">
          <Button as-child class="w-full sm:w-auto px-8 py-3 font-bold group/arrow gradient-button">
            <a href="https://tally.so/r/wM0azk" target="_blank" rel="noopener noreferrer">
              Start Learning
              <ArrowRight class="size-5 ml-2 group-hover/arrow:translate-x-1 transition-transform" />
            </a>
          </Button>
          <Button as-child variant="secondary" class="w-full sm:w-auto px-8 py-3 font-bold bg-white border-black dark:bg-grey dark:border-white dark:text-black">
            <a href="#contact">Get in Touch</a>
          </Button>
        </div>
        
        <!-- Reviews section - Now positioned right after the buttons -->
        <div class="reviews-section mt-12 md:mt-16 w-full animate-fade-in">
          <div class="reviews-card">
            <div class="flex flex-col md:flex-row justify-between items-center gap-8">
              <!-- Left side - Customer avatars with staggered animation -->
              <div class="customer-avatars flex">
                <div class="avatar-circle animate-avatar" style="animation-delay: 100ms; background-image: url('https://images.unsplash.com/photo-1612349317150-e413f6a5b16d?w=120&h=120&fit=crop&crop=face&auto=format')"></div>
                <div class="avatar-circle animate-avatar" style="animation-delay: 200ms; background-image: url('https://images.unsplash.com/photo-1622253692010-333f2da6031d?w=120&h=120&fit=crop&crop=face&auto=format')"></div>
                <div class="avatar-circle animate-avatar" style="animation-delay: 300ms; background-image: url('https://images.unsplash.com/photo-1582750433449-648ed127bb54?w=120&h=120&fit=crop&crop=face&auto=format')"></div>
                <div class="avatar-circle animate-avatar" style="animation-delay: 400ms; background-image: url('https://img.freepik.com/free-photo/young-doctor-getting-ready-work_23-2149393691.jpg'); background-size: cover; background-position: center top;"></div>
                <div class="avatar-circle animate-avatar" style="animation-delay: 500ms; background-image: url('https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=120&h=120&fit=crop&crop=face&auto=format')"></div>
              </div>
              
              <!-- Right side - Rating text with fade-in animation -->
              <div class="rating-content text-center md:text-right animate-slide-up" style="animation-delay: 300ms;">
                <div class="stars-container mb-2">
                  <span class="star animate-star animate-wave" style="animation-delay: 100ms; --wave-delay: 0s;">★</span>
                  <span class="star animate-star animate-wave" style="animation-delay: 200ms; --wave-delay: 0.2s;">★</span>
                  <span class="star animate-star animate-wave" style="animation-delay: 300ms; --wave-delay: 0.4s;">★</span>
                  <span class="star animate-star animate-wave" style="animation-delay: 400ms; --wave-delay: 0.6s;">★</span>
                  <span class="star animate-star animate-wave" style="animation-delay: 500ms; --wave-delay: 0.8s;">★</span>
                </div>
                <h3 class="text-xl md:text-xl text-foreground">Rated by hundreds of students</h3>
                <p class="text-lg md:text-lg text-muted-foreground">Loved by many!</p>
              </div>
            </div>
          </div>
        </div>
      </div>

    
      <!-- Simple bordered screenshot -->
      <div class="relative group mt-14 screenshot-container">
        <div class="screenshot-frame">
          <img
            class="w-full h-auto"
            :src="desktopScreenshot"
            alt="PYQS Dashboard"
          />
          
          <!-- Hover Overlay -->
          <div class="screenshot-overlay">
            <div class="overlay-content">
              <span class="text-white text-2xl font-bold">Experience PYQS</span><br>
              <Button variant="outline" class="mt-4 bg-white/20 backdrop-blur-sm text-white border-white hover:bg-white/30">
                Explore Dashboard
              </Button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Replace the hero-blob-bg style with this enhanced version */
.hero-blob-bg {
  position: absolute;
  width: 250%; /* Increased from 100% */ /* Increased from 100% */
  height: 250%; /* Increased from 100% */ /* Increased from 100% */
  left: 40%;
  top: 40%; /* Adjusted from 45% to center it better */ /* Adjusted from 45% to center it better */
  transform: translate(-50%, -50%);
  background: url("data:image/svg+xml,%3Csvg viewBox='0 0 800 500' xmlns='http://www.w3.org/2000/svg'%3E%3Cdefs%3E%3ClinearGradient id='a' gradientTransform='rotate(90)'%3E%3Cstop offset='0%' stop-color='%23fdfcff'/%3E%3Cstop offset='16.67%' stop-color='%23f7f5fe'/%3E%3Cstop offset='33.33%' stop-color='%23f1f1fe'/%3E%3Cstop offset='50%' stop-color='%23f5f5ff'/%3E%3Cstop offset='66.67%' stop-color='%23f1f1fe'/%3E%3Cstop offset='83.33%' stop-color='%23f3f2ff'/%3E%3Cstop offset='100%' stop-color='%23ffffff'/%3E%3C/linearGradient%3E%3C/defs%3E%3Cpath fill='url(%23a)' d='M424,308Q388,366,326.5,383Q265,400,199,384.5Q133,369,95,314Q57,259,58.5,184Q60,109,128.5,84Q197,59,262.5,64Q328,69,384.5,106Q441,143,450.5,196.5Q460,250,424,308Z' transform='translate(150, 50)'/%3E%3C/svg%3E") 
    no-repeat center center;
  background-size: contain;
  opacity: 0.95; /* Slightly increased from 0.9 */; /* Slightly increased from 0.9 */
  filter: blur(50px); /* Slightly increased from 40px */ /* Slightly increased from 40px */
  z-index: 0;
  pointer-events: none;
}

/* Media query for responsive sizing - also updated */
@media (max-width: 768px) {
  .hero-blob-bg {
    width: 180%; /* Increased from 140% */ /* Increased from 140% */
    height: 180%; /* Increased from 140% */ /* Increased from 140% */
    filter: blur(35px); /* Slightly increased from 30px */ /* Slightly increased from 30px */
  }
}

/* Gradient text styling */
.gradient-text {
  background: linear-gradient(90deg, #8c38ea 0%, #5c50eb 50%, #395deb 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.05);
}

/* Inline rotating text animation */
.rotating-text-inline {
  display: inline;
  animation: slideUpStickDown 3s ease-in-out;
  font-size: 0.85em; /* Make the rotating text slightly smaller */
}

@keyframes slideUpStickDown {
  0% {
    opacity: 0;
    transform: translateY(50px);
  }
  20% {
    opacity: 1;
    transform: translateY(0);
  }
  80% {
    opacity: 1;
    transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(-50px);
  }
}

@media (max-width: 768px) {
  .rotating-text-inline {
    font-size: 0.8em;
  }
}

@media (max-width: 480px) {
  .rotating-text-inline {
    font-size: 0.75em;
  }
}

.gradient-text-opp {
  background: linear-gradient(45deg,#395deb 0%,  #5c50eb 50%, #8c38ea 100% );
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.05);
}

/* Gradient button styling */
.gradient-button {
  background: linear-gradient(90deg, #8c38ea 0%, #5c50eb 50%, #395deb 100%) !important;
  border: none !important;
  color: white !important;
  transition: all 0.3s ease;
}

.gradient-button:hover {
  background: linear-gradient(90deg, #9945f6 0%, #6a5ef7 50%, #4a6ff7 100%) !important;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(90, 64, 226, 0.25);
}

/* Sunglasses emoji animation */
.sunglasses-emoji {
  display: inline-block;
  vertical-align: middle;
  height: 40px;
  width: 40px;
  animation: emoji-bounce 2.5s ease-in-out infinite;
}

@media (min-width: 640px) {
  .sunglasses-emoji {
    height: 60px;
    width: 60px;
  }
}

@media (min-width: 768px) {
  .sunglasses-emoji {
    height: 80px;
    width: 80px;
  }
}

@media (min-width: 1024px) {
  .sunglasses-emoji {
    height: 100px;
    width: 100px;
  }
}

@keyframes emoji-bounce {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  25% { transform: translateY(-5px) rotate(5deg); }
  75% { transform: translateY(-3px) rotate(-5deg); }
}

/* Feature rotation gradient styles */
.one-shot-gradient {
  background: linear-gradient(90deg, #ff9800, #ffb300);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.green-gradient {
  background: linear-gradient(90deg, #4caf50, #8bc34a);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.blue-gradient {
  background: linear-gradient(90deg, #03a9f4, #00bcd4);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.pink-gradient {
  background: linear-gradient(90deg, #e91e63, #f06292);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.purple-gradient {
  background: linear-gradient(90deg, #9c27b0, #673ab7);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

/* Customer avatars styling */
.customer-avatars {
  display: flex;
  align-items: center;
}

.avatar-circle {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-size: cover;
  background-position: center;
  border: 3px solid white;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  margin-right: -20px; /* Creates overlapping effect */
  transition: transform 0.3s ease;
}

.avatar-circle:hover {
  transform: translateY(-5px);
  z-index: 10;
}

/* Star rating styling */
.stars-container {
  display: flex;
  justify-content: center;
  justify-content: flex-end;
  gap: 4px;
}

.star {
  color: #F9A825; /* Gold/yellow color for stars */
  font-size: 1.75rem;
  line-height: 1;
  filter: drop-shadow(0 2px 4px rgba(249, 168, 37, 0.4));
  opacity: 0; /* Start invisible for animation */
  display: inline-block;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .gradient-text {
    font-size: 2.5rem;
  }
  .sunglasses-emoji {
    height: 40px;
    width: 40px;
  }
  .hero-radial-bg {
    width: 220vw;
    height: 180vw;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -60%);
    filter: blur(32px);
  }

  .reviews-section {
    padding: 0 1rem;
  }
  
  .avatar-circle {
    width: 50px;
    height: 50px;
    margin-right: -15px;
  }
  
  .stars-container {
    justify-content: center;
  }
  
  .star {
    font-size: 1.5rem;
  }
}

/* Add these animations and enhanced styling to your existing styles */

/* Reviews section styling - updated without background */
.reviews-section {
  position: relative;
  z-index: 10;
}

.reviews-card {
  padding: 1.5rem;
  /* Background styling removed */
  transition: transform 0.3s ease;
}

.reviews-card:hover {
  transform: translateY(-3px);
}

/* Dark mode styles for reviews card - removed empty ruleset */

/* Customer avatars styling - enhanced */
.customer-avatars {
  display: flex;
  align-items: center;
}

.avatar-circle {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-size: cover;
  background-position: center;
  border: 3px solid white;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.12);
  margin-right: -20px; /* Creates overlapping effect */
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  opacity: 0; /* Start invisible for animation */
}

.avatar-circle:hover {
  transform: translateY(-5px) scale(1.1);
  z-index: 10;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

/* Star rating styling - enhanced */
.stars-container {
  display: flex;
  justify-content: center;
  justify-content: flex-end;
  gap: 4px;
}

.star {
  color: #F9A825; /* Gold/yellow color for stars */
  font-size: 1.75rem;
  line-height: 1;
  filter: drop-shadow(0 2px 4px rgba(249, 168, 37, 0.4));
  opacity: 0; /* Start invisible for animation */
  display: inline-block;
}

/* Keep existing twinkle animation but set it to complete */
.animate-star {
  animation: twinkle 0.7s ease-out forwards;
}

/* Add the continuous wave animation */
.animate-wave {
  animation: twinkle 0.7s ease-out forwards, 
             wave 2s ease-in-out var(--wave-delay) infinite;
}

/* Animation keyframes */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes popIn {
  0% { opacity: 0; transform: scale(0.8); }
  70% { opacity: 1; transform: scale(1.1); }
  100% { opacity: 1; transform: scale(1); }
}

@keyframes twinkle {
  0% { opacity: 0; transform: scale(0.5); filter: drop-shadow(0 0 3px rgba(249, 168, 37, 0.8)); }
  50% { opacity: 1; transform: scale(1.2); filter: drop-shadow(0 0 8px rgba(249, 168, 37, 0.8)); }
  100% { opacity: 1; transform: scale(1); filter: drop-shadow(0 2px 4px rgba(249, 168, 37, 0.4)); }
}

/* New wave animation */
@keyframes wave {
  0%, 100% { 
    transform: translateY(0) scale(1);
    filter: drop-shadow(0 2px 4px rgba(249, 168, 37, 0.4)); 
  }
  25% { 
    transform: translateY(-5px) scale(1.05);
    filter: drop-shadow(0 4px 8px rgba(249, 168, 37, 0.5)); 
  }
  50% { 
    transform: translateY(0) scale(1);
    filter: drop-shadow(0 2px 4px rgba(249, 168, 37, 0.4)); 
  }
  75% { 
    transform: translateY(2px) scale(0.95);
    filter: drop-shadow(0 1px 2px rgba(249, 168, 37, 0.3)); 
  }
}

/* Animation classes */
.animate-fade-in {
  animation: fadeIn 0.8s ease-out forwards;
}

.animate-slide-up {
  animation: slideUp 0.8s ease-out forwards;
}

.animate-avatar {
  animation: popIn 0.6s ease-out forwards;
}

.animate-star {
  animation: twinkle 0.7s ease-out forwards;
}

.animate-wave {
  animation: twinkle 0.7s ease-out forwards, 
             wave 2s ease-in-out var(--wave-delay) infinite;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .reviews-card {
    padding: 1.25rem;
  }
  
  .avatar-circle {
    width: 50px;
    height: 50px;
    margin-right: -15px;
  }
  
  .stars-container {
    justify-content: center;
  }
  
  .star {
    font-size: 1.5rem;
  }
}

/* Simple Screenshot Frame Styling */
.screenshot-container {
  max-width: 1200px;
  margin: 0 auto;
  transition: transform 0.3s ease;
}

.screenshot-container:hover {
  transform: translateY(-5px);
}

.screenshot-frame {
  position: relative;
  border-radius: 20px;
  overflow: hidden;
  border: 10px solid #c0c0c0; /* Silver theme based color */
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1), 
              0 4px 15px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}

.dark .screenshot-frame {
  border-color: #666666; /* Darker silver for dark mode */
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3), 
              0 4px 15px rgba(0, 0, 0, 0.1);
}

.screenshot-frame img {
  display: block;
  width: 100%;
  height: auto;
}

/* Hover Overlay */
.screenshot-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(rgba(80, 70, 220, 0.7), rgba(140, 56, 234, 0.7));
  opacity: 0;
  transition: opacity 0.4s ease;
  display: flex;
  justify-content: center;
  align-items: center;
}

.screenshot-container:hover .screenshot-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  transform: translateY(20px);
  opacity: 0;
  transition: all 0.4s ease 0.1s;
}

.screenshot-container:hover .overlay-content {
  transform: translateY(0);
  opacity: 1;
}

/* Responsive styles for the screenshot frame */
@media (max-width: 768px) {
  .screenshot-frame {
    border-width: 6px;
    border-radius: 15px;
  }
  
  .overlay-content {
    font-size: 0.9rem;
  }
}
</style>
