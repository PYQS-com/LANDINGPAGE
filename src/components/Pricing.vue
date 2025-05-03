<script setup lang="ts">
import { ref } from 'vue';

// Toggle between monthly and yearly pricing
const billingCycle = ref<'monthly' | 'yearly'>('yearly');
</script>

<template>
  <section id="pricing" class="container relative py-24 sm:py-32 overflow-hidden font-sans">
    <!-- Grid background with fade effects - light mode only -->
    <div class="fixed inset-0 -z-20 pointer-events-none dark:hidden" 
      style="background-image: linear-gradient(#f0f0ff 1.5px, transparent 1.5px), linear-gradient(to right, #f0f0ff 1.5px, transparent 1.5px); background-size: 38px 38px; background-color: #ffffff; opacity: 0.7;">
    </div>
    
    <!-- Dark mode grid background -->
    <div class="fixed inset-0 -z-20 pointer-events-none hidden dark:block" 
      style="background-image: linear-gradient(rgba(75, 85, 99, 0.3) 1.5px, transparent 1.5px), linear-gradient(to right, rgba(75, 85, 99, 0.3) 1.5px, transparent 1.5px); background-size: 38px 38px; background-color: #000000; opacity: 0.5;">
    </div>
    
    <!-- Radial fade overlay for the grid - light mode only -->
    <div class="fixed inset-0 -z-10 pointer-events-none dark:hidden" 
      style="background: radial-gradient(circle at center, transparent 0%, rgba(255,255,255,0.6) 50%, rgba(255,255,255,1) 100%), linear-gradient(to right, rgba(255,255,255,1) 0%, rgba(255,255,255,0.2) 15%, rgba(255,255,255,0.2) 85%, rgba(255,255,255,1) 100%)">
    </div>
    
    <!-- Dark mode radial fade overlay -->
    <div class="fixed inset-0 -z-10 pointer-events-none hidden dark:block" 
      style="background: radial-gradient(circle at center, transparent 0%, rgba(0,0,0,0.6) 50%, rgba(0,0,0,1) 100%), linear-gradient(to right, rgba(0,0,0,1) 0%, rgba(0,0,0,0.2) 15%, rgba(0,0,0,0.2) 85%, rgba(0,0,0,1) 100%)">
    </div>
    
    <!-- Simple elegant background effect - light mode only -->
    <div class="fixed top-0 left-0 right-0 h-1/2 bg-gradient-to-b from-white to-transparent -z-10 pointer-events-none dark:hidden"></div>
    
    <!-- Dark mode top gradient -->
    <div class="fixed top-0 left-0 right-0 h-1/2 bg-gradient-to-b from-black to-transparent -z-10 pointer-events-none hidden dark:block"></div>
        
    <!-- Rest of the background elements with dark mode support -->
    <div class="fixed -top-20 -right-20 w-96 h-96 rounded-full opacity-[0.08] dark:opacity-[0.15] blur-[80px] -z-10 pointer-events-none"
         style="background: linear-gradient(108deg, #8c38ea, #5c50eb)"></div>
    <div class="fixed -bottom-20 -left-20 w-96 h-96 rounded-full opacity-[0.08] dark:opacity-[0.15] blur-[80px] -z-10 pointer-events-none"
         style="background: linear-gradient(108deg, #e91e63, #f06292)"></div>
    
    <!-- Clean header - responsive text sizing -->
    <div class="max-w-5xl mx-auto text-center mb-10 md:mb-16 pt-8 sm:pt-2">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider animate-fade-in">
        Pricing
      </h2>

      <h2 class="text-3xl md:text-5xl text-center font-extrabold gradient-text mb-4">
        Choose Your Perfect Plan
      </h2>

      <p class="text-base sm:text-lg text-gray-600 max-w-lg mx-auto px-4">
        Get unlimited access to past year question papers and excel in your exams
      </p>
      
      <!-- Toggle for Monthly/Yearly billing -->
      <div class="mt-8 inline-flex items-center bg-gray-100 rounded-full p-1">
        <button 
          @click="billingCycle = 'monthly'" 
          :class="[
            'px-4 py-2 rounded-full text-sm font-medium transition-all duration-200',
            billingCycle === 'monthly' 
              ? 'bg-white shadow text-primary-600' 
              : 'text-gray-600 hover:text-gray-900'
          ]"
        >
          Monthly
        </button>
        <button 
          @click="billingCycle = 'yearly'" 
          :class="[
            'px-4 py-2 rounded-full text-sm font-medium transition-all duration-200 flex items-center',
            billingCycle === 'yearly' 
              ? 'bg-white shadow text-primary-600' 
              : 'text-gray-600 hover:text-gray-900'
          ]"
        >
          Yearly
          <span class="ml-1.5 inline-flex items-center px-1.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800">
            Save 16%
          </span>
        </button>
      </div>
    </div>
    
    <!-- Responsive card layout -->
    <div class="max-w-5xl mx-auto flex flex-wrap justify-center gap-6 md:gap-8">
      <!-- Freemium Plan -->
      <div class="w-full sm:max-w-[340px] md:max-w-md bg-white rounded-2xl overflow-hidden transition-all duration-300 
        border border-gray-100
        shadow-[0_10px_30px_-10px_rgba(0,0,0,0.05),0_1px_3px_rgba(0,0,0,0.05),inset_0_0_0_1px_rgba(255,255,255,0.2)]
        hover:shadow-[0_20px_40px_-10px_rgba(140,56,234,0.1),0_10px_10px_-5px_rgba(140,56,234,0.04)]
        hover:-translate-y-1">
        
        <div class="py-6 px-6 md:py-8 md:px-8 text-center bg-gradient-to-b from-gray-50/60 to-white relative">
          <div class="absolute -bottom-px left-0 right-0 h-px bg-gradient-to-r from-transparent via-purple-100 to-transparent"></div>
          <h2 class="text-xl font-bold text-gray-800 mb-2">Freemium</h2>
          <p class="text-gray-500 text-sm mb-4 md:mb-5">For students getting started</p>
          <div class="flex items-baseline justify-center">
            <span class="text-xl md:text-2xl font-bold text-gray-700"></span>
            <span class="text-4xl md:text-5xl font-black text-gray-800 mx-1 leading-none"></span>
            <span class="text-gray-500">Free</span>
          </div>
        </div>
        
        <div class="p-6 md:p-8">
          <ul class="space-y-3 md:space-y-4">
            <li class="flex items-center text-gray-600">
              <div class="w-5 h-5 mr-3 rounded-full bg-blue-50 flex items-center justify-center flex-shrink-0">
                <svg class="w-3 h-3 text-[#8c38ea]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                </svg>
              </div>
              <span class="text-sm sm:text-base">Access to last 5 years PYQs</span>
            </li>
            <li class="flex items-center text-gray-600">
              <div class="w-5 h-5 mr-3 rounded-full bg-blue-50 flex items-center justify-center flex-shrink-0">
                <svg class="w-3 h-3 text-[#8c38ea]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                </svg>
              </div>
              <span class="text-sm sm:text-base">Basic search functionality</span>
            </li>
            <li class="flex items-center text-gray-600">
              <div class="w-5 h-5 mr-3 rounded-full bg-blue-50 flex items-center justify-center flex-shrink-0">
                <svg class="w-3 h-3 text-[#8c38ea]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                </svg>
              </div>
              <span class="text-sm sm:text-base">Download up to 10 papers/month</span>
            </li>
            <li class="flex items-center text-gray-600">
              <div class="w-5 h-5 mr-3 rounded-full bg-blue-50 flex items-center justify-center flex-shrink-0">
                <svg class="w-3 h-3 text-[#8c38ea]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                </svg>
              </div>
              <span class="text-sm sm:text-base">Email support</span>
            </li>
          </ul>
          
          <button class="w-full mt-6 md:mt-8 py-3.5 md:py-4 px-6 rounded-xl text-gray-700 font-semibold
            bg-gradient-to-br from-gray-50 to-gray-100
            shadow-[0_2px_3px_-1px_rgba(0,0,0,0.1),0_1px_2px_-1px_rgba(0,0,0,0.06),inset_0_1px_1px_white]
            hover:shadow-[0_10px_15px_-3px_rgba(0,0,0,0.1),0_4px_6px_-2px_rgba(0,0,0,0.05)]
            transition duration-300">
            Get Started
          </button>
        </div>
      </div>

      <!-- Premium Plan - With enhanced glossy shadow effect -->
      <div class="w-full sm:max-w-[340px] md:max-w-md relative transition-all duration-300 hover:-translate-y-1 group mt-8 sm:mt-0">
        <!-- Enhanced multi-layered glossy shadow effect -->
        <div class="absolute -inset-[3px] rounded-2xl opacity-75 blur-[5px] group-hover:opacity-85 group-hover:blur-[8px] transition-all duration-300"
             style="background: linear-gradient(108deg, #8c38ea 20%, #5c50eb 50%, #395deb 75%, #5461f2 100%)"></div>
        <div class="absolute -inset-[1px] rounded-2xl opacity-90 blur-[1px] group-hover:opacity-95"
             style="background: linear-gradient(108deg, #8c38ea, #5c50eb 34%, #395deb 68%, #5461f2 100%)"></div>
        
        <div class="relative bg-white rounded-2xl overflow-hidden
          shadow-[0_15px_30px_-10px_rgba(140,56,234,0.3),0_10px_20px_-10px_rgba(84,97,242,0.2),inset_0_0_0_1px_rgba(255,255,255,0.2)]
          group-hover:shadow-[0_25px_40px_-12px_rgba(140,56,234,0.4),0_18px_25px_-15px_rgba(84,97,242,0.3),inset_0_0_0_1px_rgba(255,255,255,0.3)] 
          transition-all duration-300">
          
          <div class="absolute top-0 left-0 right-0 h-1"
               style="background: linear-gradient(to right, #8c38ea, #5c50eb, #395deb, #5461f2)"></div>
          
          <!-- Updated "Most Popular" tag -->
          <div class="absolute top-3 sm:top-5 right-3 sm:right-5">
            <span class="inline-flex items-center px-2.5 sm:px-3 py-1 rounded-full text-xs font-medium text-white
              shadow-[0_2px_5px_-1px_rgba(140,56,234,0.3)]"
              style="background: linear-gradient(to right, #8c38ea, #5c50eb)">
              Most Popular
            </span>
          </div>
          
          <div class="py-6 px-6 md:py-8 md:px-8 text-center bg-gradient-to-b from-gray-50/40 to-white relative">
            <div class="absolute -bottom-px left-0 right-0 h-px bg-gradient-to-r from-transparent via-purple-100 to-transparent"></div>
            <h2 class="text-xl font-bold text-gray-800 mb-2">Premium</h2>
            <p class="text-gray-500 text-sm mb-4 md:mb-5">For serious exam preparation</p>
            <div class="flex items-baseline justify-center">
              <span class="text-xl md:text-2xl font-bold text-gray-700">₹</span>
              <span class="text-4xl md:text-5xl font-black text-gray-800 mx-1 leading-none">
                {{ billingCycle === 'monthly' ? '99' : '999' }}
              </span>
              <span class="text-gray-500">/{{ billingCycle === 'monthly' ? 'month' : 'year' }}</span>
            </div>
          </div>
          
          <div class="p-6 md:p-8">
            <ul class="space-y-3 md:space-y-4">
              <!-- AI-focused features -->
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">AI-powered MCQ chat assistance</span>
              </li>
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">Personalized AI analytics</span>
              </li>
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">AI-driven study recommendations</span>
              </li>
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">Access to all historical PYQs</span>
              </li>
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">Unlimited downloads</span>
              </li>
              <li class="flex items-center text-gray-600">
                <div class="w-5 h-5 mr-3 rounded-full flex items-center justify-center flex-shrink-0"
                     style="background: linear-gradient(to bottom right, rgba(140, 56, 234, 0.1), rgba(92, 80, 235, 0.1))">
                  <svg class="w-3 h-3 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <polyline points="20 6 9 17 4 12" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"></polyline>
                  </svg>
                </div>
                <span class="text-sm sm:text-base">Topic-wise sorted questions</span>
              </li>
            </ul>
            
            <div class="relative w-full mt-6 md:mt-8 overflow-hidden rounded-xl">
              <button class="w-full py-3.5 md:py-4 px-6 rounded-xl text-white font-semibold
                relative z-10 overflow-hidden transition duration-300 gradient-button">
                <span class="relative z-10">Get Premium</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Simple guarantee - responsive -->
    <div class="max-w-5xl mx-auto flex justify-center mt-10 md:mt-12">
      <div class="flex items-center space-x-2 text-gray-500 bg-white/80 backdrop-blur-sm py-2 px-4 rounded-full shadow-sm border border-gray-100/50">
        <svg class="w-4 h-4 text-[#5c50eb]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
        </svg>
        <p class="text-xs sm:text-sm">30-day money back guarantee</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Gradient text styling */
.gradient-text {
  background: linear-gradient(90deg, #8c38ea 0%, #5c50eb 50%, #395deb 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
}

/* Gradient button styling */
.gradient-button {
  background: linear-gradient(90deg, #8c38ea, #5c50eb, #395deb);
  box-shadow: 0 10px 15px -3px rgba(140, 56, 234, 0.2), 0 4px 6px -2px rgba(92, 80, 235, 0.1);
}

.gradient-button:hover {
  box-shadow: 0 15px 20px -5px rgba(140, 56, 234, 0.25), 0 10px 10px -5px rgba(92, 80, 235, 0.15);
}

.gradient-button::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to right, transparent, rgba(255, 255, 255, 0.2), transparent);
  transform: translateX(-100%);
  transition: transform 1s ease;
}

.gradient-button:hover::after {
  transform: translateX(100%);
}

/* Animations */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fade-in {
  opacity: 0;
  animation: fadeIn 0.6s ease-out forwards;
}

/* Media queries for smaller screens */
@media (max-width: 640px) {
  .gradient-text {
    font-size: 2rem;
  }
}
</style>