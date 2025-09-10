<script setup lang="ts">
import { ref } from 'vue';
import { MessageSquare, Search, Zap, BookOpen, Trophy, Target } from 'lucide-vue-next';

interface TabFeature {
  id: string;
  title: string;
  icon: any;
  description: string;
  content: {
    title: string;
    subtitle: string;
    features: string[];
  };
}

const activeTab = ref('ai');

const tabFeatures: TabFeature[] = [
  {
    id: 'ai',
    title: 'AI Assistant',
    icon: MessageSquare,
    description: 'Smart Study Companion',
    content: {
      title: 'Your Personal AI Tutor',
      subtitle: 'Get instant help with medical concepts, practice questions, and study guidance.',
      features: [
        'Instant answers to medical queries',
        'Personalized study recommendations',
        'Doubt clarification and explanations',
        'Custom quiz generation based on topics'
      ]
    }
  },
  {
    id: 'gamified',
    title: 'Gamified Learning',
    icon: Zap,
    description: 'Level Up Your Studies',
    content: {
      title: 'Turn Study Into Play',
      subtitle: 'Earn points, unlock achievements, and compete with peers while mastering medical concepts.',
      features: [
        'XP points for every topic mastered',
        'Achievement badges and milestones',
        'Leaderboards and friendly competition',
        'Streak counters to build study habits'
      ]
    }
  },
  {
    id: 'pyqs',
    title: 'PYQS Database',
    icon: BookOpen,
    description: 'AI first PYQS.com',
    content: {
      title: 'Master Exam Patterns',
      subtitle: 'Access comprehensive previous year questions with detailed solutions and analysis.',
      features: [
        'NEET PG questions from last 20 years',
        'INI-CET and FMGE question banks',
        'Topic-wise and year-wise filtering',
        'Detailed explanations for every answer'
      ]
    }
  },
  {
    id: 'analytics',
    title: 'Smart Analytics',
    icon: Search,
    description: 'Track Your Progress',
    content: {
      title: 'Data-Driven Learning',
      subtitle: 'Monitor your progress with detailed analytics and insights to optimize your studies.',
      features: [
        'Performance tracking across subjects',
        'Time spent analysis and optimization',
        'Weak area identification and improvement',
        'Progress comparison with peer groups'
      ]
    }
  }
];

const setActiveTab = (tabId: string) => {
  activeTab.value = tabId;
};

const getActiveTabStyle = (tabId: string) => {
  const styles: Record<string, string> = {
    gamified: 'bg-gradient-to-r from-[#ff6b6b] via-[#ff7961] to-[#ff8e53] text-white border-transparent shadow-2xl ring-1 ring-red-300/40 glow-red glassmorphism-red',
    pyqs: 'bg-gradient-to-r from-[#4ecdc4] via-[#4dd0c7] to-[#44a08d] text-white border-transparent shadow-2xl ring-1 ring-teal-300/40 glow-teal glassmorphism-teal',
    ai: 'bg-gradient-to-r from-[#667eea] via-[#6b73ff] to-[#764ba2] text-white border-transparent shadow-2xl ring-1 ring-purple-300/40 glow-purple glassmorphism-purple',
    analytics: 'bg-gradient-to-r from-[#f093fb] via-[#f472b6] to-[#f5576c] text-white border-transparent shadow-2xl ring-1 ring-pink-300/40 glow-pink glassmorphism-pink'
  };
  return styles[tabId] || 'bg-gradient-to-r from-[#8c38ea] to-[#5c50eb] text-white border-transparent shadow-2xl glow-default glassmorphism-default';
};


const getButtonStyle = (tabId: string) => {
  const styles: Record<string, string> = {
    gamified: 'bg-gradient-to-r from-[#ff6b6b] to-[#ff8e53] hover:from-[#ff5252] hover:to-[#ff7043]',
    pyqs: 'bg-gradient-to-r from-[#4ecdc4] to-[#44a08d] hover:from-[#26c6da] hover:to-[#388e3c]',
    ai: 'bg-gradient-to-r from-[#667eea] to-[#764ba2] hover:from-[#5a67d8] hover:to-[#6b46c1]',
    analytics: 'bg-gradient-to-r from-[#f093fb] to-[#f5576c] hover:from-[#ec4899] hover:to-[#f43f5e]'
  };
  return styles[tabId] || 'bg-gradient-to-r from-[#8c38ea] to-[#5c50eb] hover:from-[#9945f6] hover:to-[#6a5ef7]';
};

const getCurrentTab = () => {
  return tabFeatures.find(tab => tab.id === activeTab.value) || tabFeatures[0];
};

const getIconBackground = (tabId: string) => {
  const backgrounds: Record<string, string> = {
    gamified: 'bg-gradient-to-r from-[#ff6b6b] to-[#ff8e53]',
    pyqs: 'bg-gradient-to-r from-[#4ecdc4] to-[#44a08d]',
    ai: 'bg-gradient-to-r from-[#667eea] to-[#764ba2]',
    analytics: 'bg-gradient-to-r from-[#f093fb] to-[#f5576c]'
  };
  return backgrounds[tabId] || 'bg-gradient-to-r from-[#8c38ea] to-[#5c50eb]';
};

const getTextColor = (tabId: string) => {
  const colors: Record<string, string> = {
    gamified: 'text-red-600',
    pyqs: 'text-teal-600',
    ai: 'text-purple-600',
    analytics: 'text-pink-600'
  };
  return colors[tabId] || 'text-primary';
};

const getDotColor = (tabId: string) => {
  const colors: Record<string, string> = {
    gamified: 'bg-red-500',
    pyqs: 'bg-teal-500',
    ai: 'bg-purple-500',
    analytics: 'bg-pink-500'
  };
  return colors[tabId] || 'bg-primary';
};
</script>

<template>
  <section id="features" class="container py-24 sm:py-32">
    <div class="text-center mb-16">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider animate-fade-in">Features</h2>
      <h2 class="text-3xl md:text-4xl text-center font-bold mb-4 gradient-text animate-slide-up">
        Meet PYQS - Your AI Study Partner
      </h2>
      <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8 animate-slide-up" style="animation-delay: 100ms;">
        Instant help, custom quizzes, and answers that adapt to how you learn best
      </h3>
    </div>

    <div class="max-w-6xl mx-auto">
      <!-- Tab Navigation -->
      <div class="flex flex-wrap justify-center gap-2 mb-12 animate-fade-in" style="animation-delay: 200ms;">
        <button
          v-for="tab in tabFeatures"
          :key="tab.id"
          @click="setActiveTab(tab.id)"
          :class="[
            'flex items-center rounded-full transition-all duration-500 ease-out',
            'border font-medium transform hover:scale-105 relative overflow-hidden backdrop-blur-sm',
            // Mobile: circular buttons, expand when active
            'w-12 h-12 p-0 justify-center md:w-auto md:px-6 md:py-3 md:gap-2',
            // Add gap and padding when active on mobile
            activeTab === tab.id ? 'gap-2 px-4 py-3 w-auto' : '',
            activeTab === tab.id
              ? getActiveTabStyle(tab.id)
              : 'bg-white/10 border-white/20 text-muted-foreground hover:bg-white/20 hover:border-white/30 hover:text-foreground hover:shadow-xl'
          ]"
        >
          <component :is="tab.icon" class="w-5 h-5" />
          <span :class="[
            // Show text on desktop always, on mobile only when active
            'md:inline',
            activeTab === tab.id ? 'inline' : 'hidden md:inline'
          ]">{{ tab.title }}</span>
        </button>
      </div>

      <!-- Tab Content -->
      <div class="grid lg:grid-cols-2 gap-12 items-center animate-slide-up" style="animation-delay: 300ms;">
        <!-- Left Content -->
        <div class="space-y-6">
          <div class="space-y-6" :key="activeTab">
            <div class="flex items-center gap-3">
              <div :class="getIconBackground(activeTab)" class="p-2 rounded-lg">
                <component :is="getCurrentTab().icon" class="w-6 h-6 text-white" />
              </div>
              <span class="text-sm font-medium uppercase tracking-wider" :class="getTextColor(activeTab)">{{ getCurrentTab().description }}</span>
            </div>
            
            <h3 class="text-3xl md:text-4xl font-bold text-foreground">
              {{ getCurrentTab().content.title }}
            </h3>
            
            <p class="text-xl text-muted-foreground leading-relaxed">
              {{ getCurrentTab().content.subtitle }}
            </p>
            
            <ul class="space-y-3">
              <li v-for="feature in getCurrentTab().content.features" :key="feature" class="flex items-start gap-3">
                <div :class="getDotColor(activeTab)" class="w-2 h-2 rounded-full mt-2 flex-shrink-0"></div>
                <span class="text-muted-foreground">{{ feature }}</span>
              </li>
            </ul>

            <button :class="getButtonStyle(activeTab)" class="inline-flex items-center px-6 py-3 text-white rounded-lg font-medium hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
              Try {{ getCurrentTab().title }} for Free
            </button>
          </div>
        </div>

        <!-- Clean Dashboard Design -->
        <div class="relative">
          <div class="bg-white dark:bg-gray-900 rounded-2xl md:rounded-3xl p-4 md:p-8 shadow-lg">
            
            <!-- Header -->
            <div class="flex items-center gap-3 mb-6 md:mb-8">
              <div class="w-8 h-8 rounded-lg flex items-center justify-center" :class="getCurrentTab().id === 'gamified' ? 'bg-red-100 dark:bg-red-900/30' : getCurrentTab().id === 'pyqs' ? 'bg-teal-100 dark:bg-teal-900/30' : getCurrentTab().id === 'ai' ? 'bg-purple-100 dark:bg-purple-900/30' : 'bg-pink-100 dark:bg-pink-900/30'">
                <component :is="getCurrentTab().icon" class="w-4 h-4" :class="getCurrentTab().id === 'gamified' ? 'text-red-600 dark:text-red-400' : getCurrentTab().id === 'pyqs' ? 'text-teal-600 dark:text-teal-400' : getCurrentTab().id === 'ai' ? 'text-purple-600 dark:text-purple-400' : 'text-pink-600 dark:text-pink-400'" />
              </div>
              <h3 class="font-semibold text-gray-900 dark:text-white">{{ getCurrentTab().title }}</h3>
            </div>

            <!-- Content -->
            <div class="space-y-6">
              
              <!-- Gamified Content -->
              <div v-if="activeTab === 'gamified'" key="gamified" class="animate-fade-in space-y-6">
                <div class="text-center">
                  <div class="text-4xl font-bold text-red-600 dark:text-red-400 mb-2">2,450</div>
                  <div class="text-sm text-gray-600 dark:text-gray-400 mb-4">XP Points Earned</div>
                  <div class="inline-flex items-center gap-2 px-4 py-2 bg-red-50 dark:bg-red-900/20 rounded-full">
                    <div class="text-lg font-bold text-red-700 dark:text-red-300">Level 15</div>
                    <div class="text-sm text-red-600 dark:text-red-400">Cardiology Master</div>
                  </div>
                </div>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                  <div class="bg-gradient-to-r from-yellow-50 to-orange-50 dark:from-yellow-900/20 dark:to-orange-900/20 rounded-xl md:rounded-2xl p-3 md:p-4 text-center">
                    <Trophy class="w-6 h-6 md:w-8 md:h-8 text-yellow-600 dark:text-yellow-400 mx-auto mb-2" />
                    <div class="font-semibold text-sm text-gray-900 dark:text-white">7 Day Streak</div>
                    <div class="text-xs text-gray-600 dark:text-gray-400">Keep going!</div>
                  </div>
                  <div class="bg-gradient-to-r from-green-50 to-blue-50 dark:from-green-900/20 dark:to-blue-900/20 rounded-xl md:rounded-2xl p-3 md:p-4 text-center">
                    <Target class="w-6 h-6 md:w-8 md:h-8 text-green-600 dark:text-green-400 mx-auto mb-2" />
                    <div class="font-semibold text-sm text-gray-900 dark:text-white">Expert Badge</div>
                    <div class="text-xs text-gray-600 dark:text-gray-400">Anatomy</div>
                  </div>
                </div>
              </div>

              <!-- PYQS Content -->
              <div v-if="activeTab === 'pyqs'" key="pyqs" class="animate-fade-in space-y-6">
                <div class="text-center">
                  <div class="text-2xl font-bold text-gray-900 dark:text-white mb-1">NEET PG 2023</div>
                  <div class="text-sm text-gray-600 dark:text-gray-400">Question 45 of 180 • Cardiology</div>
                </div>
                
                <div class="bg-gradient-to-r from-teal-50 to-green-50 dark:from-teal-900/20 dark:to-green-900/20 rounded-xl md:rounded-2xl p-4 md:p-6">
                  <div class="text-center mb-4">
                    <div class="text-base md:text-lg font-bold text-teal-700 dark:text-teal-300">Previous Year Trend</div>
                    <div class="text-sm text-gray-600 dark:text-gray-400">This topic appeared 12 times in last 5 years</div>
                  </div>
                </div>

                <div class="grid grid-cols-3 gap-2 md:gap-3">
                  <div class="text-center p-3 md:p-4 bg-gray-50 dark:bg-gray-800 rounded-lg md:rounded-xl">
                    <div class="text-lg md:text-2xl font-bold text-teal-600 dark:text-teal-400">85%</div>
                    <div class="text-xs text-gray-500 dark:text-gray-400 mt-1">Accuracy</div>
                  </div>
                  <div class="text-center p-3 md:p-4 bg-gray-50 dark:bg-gray-800 rounded-lg md:rounded-xl">
                    <div class="text-lg md:text-2xl font-bold text-blue-600 dark:text-blue-400">2.5m</div>
                    <div class="text-xs text-gray-500 dark:text-gray-400 mt-1">Avg Time</div>
                  </div>
                  <div class="text-center p-3 md:p-4 bg-gray-50 dark:bg-gray-800 rounded-lg md:rounded-xl">
                    <div class="text-lg md:text-2xl font-bold text-green-600 dark:text-green-400">High</div>
                    <div class="text-xs text-gray-500 dark:text-gray-400 mt-1">Priority</div>
                  </div>
                </div>
              </div>

              <!-- AI Content -->
              <div v-if="activeTab === 'ai'" key="ai" class="animate-fade-in space-y-6">
                <div class="flex flex-col sm:flex-row items-center justify-center gap-3 mb-6">
                  <div class="text-lg md:text-xl font-bold text-gray-900 dark:text-white">PYQS Assistant</div>
                  <div class="flex items-center gap-1">
                    <div class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
                    <span class="text-sm text-green-600 dark:text-green-400 font-medium">Online</span>
                  </div>
                </div>
                
                <div class="bg-gradient-to-r from-purple-50 to-blue-50 dark:from-purple-900/20 dark:to-blue-900/20 rounded-xl md:rounded-2xl p-4 md:p-6">
                  <div class="flex flex-col sm:flex-row items-start gap-3">
                    <div class="w-8 h-8 bg-gradient-to-r from-purple-500 to-blue-500 rounded-full flex items-center justify-center flex-shrink-0 mt-1">
                      <Zap class="w-4 h-4 text-white" />
                    </div>
                    <div class="flex-1">
                      <div class="font-semibold text-purple-700 dark:text-purple-300 mb-2">AI Recommendation</div>
                      <div class="text-sm text-gray-600 dark:text-gray-400 mb-4">Based on your performance, focus more on Pharmacology this week.</div>
                      <div class="flex gap-2 flex-wrap">
                        <span class="px-3 py-1 bg-white dark:bg-gray-700 text-purple-700 dark:text-purple-300 rounded-full text-xs font-medium">Quick Quiz</span>
                        <span class="px-3 py-1 bg-white dark:bg-gray-700 text-blue-700 dark:text-blue-300 rounded-full text-xs font-medium">Explain</span>
                        <span class="px-3 py-1 bg-white dark:bg-gray-700 text-indigo-700 dark:text-indigo-300 rounded-full text-xs font-medium">Study Plan</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Analytics Content -->
              <div v-if="activeTab === 'analytics'" key="analytics" class="animate-fade-in space-y-6">
                <div class="text-center mb-6">
                  <div class="text-lg md:text-xl font-bold text-gray-900 dark:text-white mb-1">Weekly Performance</div>
                  <div class="text-sm text-gray-600 dark:text-gray-400">Your study analytics overview</div>
                </div>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-6">
                  <div class="text-center p-4 md:p-6 bg-gradient-to-r from-pink-50 to-rose-50 dark:from-pink-900/20 dark:to-rose-900/20 rounded-xl md:rounded-2xl">
                    <div class="text-2xl md:text-3xl font-bold text-pink-600 dark:text-pink-400 mb-1">78%</div>
                    <div class="text-sm text-gray-600 dark:text-gray-400">Overall Accuracy</div>
                  </div>
                  <div class="text-center p-4 md:p-6 bg-gradient-to-r from-blue-50 to-indigo-50 dark:from-blue-900/20 dark:to-indigo-900/20 rounded-xl md:rounded-2xl">
                    <div class="text-2xl md:text-3xl font-bold text-blue-600 dark:text-blue-400 mb-1">156</div>
                    <div class="text-sm text-gray-600 dark:text-gray-400">Questions Solved</div>
                  </div>
                </div>

                <div class="bg-gradient-to-r from-yellow-50 to-orange-50 dark:from-yellow-900/20 dark:to-orange-900/20 rounded-xl md:rounded-2xl p-4 md:p-6">
                  <div class="flex items-center gap-2 mb-4">
                    <Target class="w-4 h-4 md:w-5 md:h-5 text-orange-600 dark:text-orange-400" />
                    <span class="font-semibold text-sm md:text-base text-orange-700 dark:text-orange-300">Focus Areas Progress</span>
                  </div>
                  <div class="flex h-2 md:h-3 bg-gray-200 dark:bg-gray-700 rounded-full overflow-hidden">
                    <div class="bg-red-400 flex-1"></div>
                    <div class="bg-yellow-400 flex-1"></div>
                    <div class="bg-green-400 flex-2"></div>
                  </div>
                  <div class="flex justify-between text-xs text-gray-500 dark:text-gray-400 mt-2">
                    <span>Weak</span>
                    <span>Average</span>
                    <span>Strong</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
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
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.05);
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

/* Animation classes */
.animate-fade-in {
  opacity: 0;
  animation: fadeIn 0.8s ease-out forwards;
}

.animate-slide-up {
  opacity: 0;
  animation: slideUp 0.8s ease-out forwards;
}

/* Enhanced glow effects for tabs */
.glow-red {
  box-shadow: 
    0 0 30px rgba(255, 107, 107, 0.5),
    0 0 60px rgba(255, 107, 107, 0.3),
    0 8px 32px rgba(255, 107, 107, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

.glow-teal {
  box-shadow: 
    0 0 30px rgba(78, 205, 196, 0.5),
    0 0 60px rgba(78, 205, 196, 0.3),
    0 8px 32px rgba(78, 205, 196, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

.glow-purple {
  box-shadow: 
    0 0 30px rgba(102, 126, 234, 0.5),
    0 0 60px rgba(102, 126, 234, 0.3),
    0 8px 32px rgba(102, 126, 234, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

.glow-pink {
  box-shadow: 
    0 0 30px rgba(240, 147, 251, 0.5),
    0 0 60px rgba(240, 147, 251, 0.3),
    0 8px 32px rgba(240, 147, 251, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

.glow-default {
  box-shadow: 
    0 0 30px rgba(140, 56, 234, 0.5),
    0 0 60px rgba(140, 56, 234, 0.3),
    0 8px 32px rgba(140, 56, 234, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

/* Glassmorphism effects */
.glassmorphism-red {
  backdrop-filter: blur(16px);
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.9), rgba(255, 142, 83, 0.9));
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.glassmorphism-teal {
  backdrop-filter: blur(16px);
  background: linear-gradient(135deg, rgba(78, 205, 196, 0.9), rgba(68, 160, 141, 0.9));
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.glassmorphism-purple {
  backdrop-filter: blur(16px);
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.9), rgba(118, 75, 162, 0.9));
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.glassmorphism-pink {
  backdrop-filter: blur(16px);
  background: linear-gradient(135deg, rgba(240, 147, 251, 0.9), rgba(245, 87, 108, 0.9));
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.glassmorphism-default {
  backdrop-filter: blur(16px);
  background: linear-gradient(135deg, rgba(140, 56, 234, 0.9), rgba(92, 80, 235, 0.9));
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* Enhanced hover effects */
button:hover.glow-red,
button:hover.glow-teal,
button:hover.glow-purple,
button:hover.glow-pink,
button:hover.glow-default {
  transform: scale(1.05) translateY(-2px);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .gradient-text {
    font-size: 2rem;
  }
}
</style>