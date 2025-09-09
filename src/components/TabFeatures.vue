<script setup lang="ts">
import { ref } from 'vue';
import { MessageSquare, Search, Zap, BookOpen, Trophy, Target, BarChart3 } from 'lucide-vue-next';

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
    gamified: 'bg-gradient-to-r from-[#ff6b6b] to-[#ff8e53] text-white border-transparent shadow-lg shadow-red-200',
    pyqs: 'bg-gradient-to-r from-[#4ecdc4] to-[#44a08d] text-white border-transparent shadow-lg shadow-teal-200',
    ai: 'bg-gradient-to-r from-[#667eea] to-[#764ba2] text-white border-transparent shadow-lg shadow-purple-200',
    analytics: 'bg-gradient-to-r from-[#f093fb] to-[#f5576c] text-white border-transparent shadow-lg shadow-pink-200'
  };
  return styles[tabId] || 'bg-gradient-to-r from-[#8c38ea] to-[#5c50eb] text-white border-transparent shadow-lg';
};

const getVisualBackground = (tabId: string) => {
  const backgrounds: Record<string, string> = {
    gamified: 'bg-gradient-to-br from-red-50/80 to-orange-50/80',
    pyqs: 'bg-gradient-to-br from-teal-50/80 to-green-50/80',
    ai: 'bg-gradient-to-br from-purple-50/80 to-blue-50/80',
    analytics: 'bg-gradient-to-br from-pink-50/80 to-rose-50/80'
  };
  return backgrounds[tabId] || 'bg-gradient-to-br from-[#8c38ea]/5 to-[#5c50eb]/5';
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
            'flex items-center rounded-full transition-all duration-300',
            'border-2 font-medium transform hover:scale-105',
            // Mobile: circular buttons, expand when active
            'w-12 h-12 p-0 justify-center md:w-auto md:px-6 md:py-3 md:gap-2',
            // Add gap and padding when active on mobile
            activeTab === tab.id ? 'gap-2 px-4 py-3 w-auto' : '',
            activeTab === tab.id
              ? getActiveTabStyle(tab.id)
              : 'bg-background text-muted-foreground border-border hover:border-primary/50 hover:text-foreground hover:shadow-md'
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

        <!-- Right Visual -->
        <div class="relative">
          <div :class="getVisualBackground(activeTab)" class="rounded-2xl p-8 border border-border">
            <!-- Mock Gamified Interface -->
            <div v-if="activeTab === 'gamified'" class="space-y-4">
              <div class="bg-background rounded-xl p-6 border shadow-sm">
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-12 h-12 bg-gradient-to-r from-[#ff6b6b] to-[#ff8e53] rounded-full flex items-center justify-center">
                      <Zap class="w-6 h-6 text-white" />
                    </div>
                    <div>
                      <div class="font-bold text-lg">Level 15</div>
                      <div class="text-sm text-muted-foreground">Cardiology Master</div>
                    </div>
                  </div>
                  <div class="text-right">
                    <div class="text-2xl font-bold text-[#ff6b6b]">2,450</div>
                    <div class="text-xs text-muted-foreground">XP Points</div>
                  </div>
                </div>
                <div class="space-y-3">
                  <div class="flex items-center gap-3">
                    <div class="w-8 h-8 bg-gradient-to-r from-yellow-400 to-orange-400 rounded-lg flex items-center justify-center">
                      <Trophy class="w-4 h-4 text-white" />
                    </div>
                    <span class="text-sm font-medium">7-day study streak!</span>
                  </div>
                  <div class="flex items-center gap-3">
                    <div class="w-8 h-8 bg-gradient-to-r from-green-400 to-blue-400 rounded-lg flex items-center justify-center">
                      <Target class="w-4 h-4 text-white" />
                    </div>
                    <span class="text-sm font-medium">Achievement unlocked: Anatomy Expert</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Mock PYQS Interface -->
            <div v-if="activeTab === 'pyqs'" class="space-y-4">
              <div class="bg-background rounded-xl p-6 border shadow-sm">
                <div class="flex items-center gap-3 mb-4">
                  <div class="w-10 h-10 bg-gradient-to-r from-[#4ecdc4] to-[#44a08d] rounded-lg flex items-center justify-center">
                    <span class="text-white font-bold text-sm">PYQ</span>
                  </div>
                  <div>
                    <div class="font-bold">NEET PG 2023</div>
                    <div class="text-sm text-muted-foreground">Cardiology • Question 45/180</div>
                  </div>
                </div>
                <div class="space-y-3">
                  <div class="p-3 bg-gradient-to-r from-teal-50 to-green-50 rounded-lg border-l-4 border-teal-400">
                    <div class="text-sm font-medium mb-1">Previous Year Trend</div>
                    <div class="text-xs text-muted-foreground">This topic appeared 12 times in last 5 years</div>
                  </div>
                  <div class="grid grid-cols-3 gap-2 text-center">
                    <div class="p-2 bg-teal-100 rounded text-xs">
                      <div class="font-bold text-teal-700">85%</div>
                      <div class="text-teal-600">Accuracy</div>
                    </div>
                    <div class="p-2 bg-blue-100 rounded text-xs">
                      <div class="font-bold text-blue-700">2.5min</div>
                      <div class="text-blue-600">Avg Time</div>
                    </div>
                    <div class="p-2 bg-green-100 rounded text-xs">
                      <div class="font-bold text-green-700">High</div>
                      <div class="text-green-600">Priority</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Mock AI Interface -->
            <div v-if="activeTab === 'ai'" class="space-y-4">
              <div class="bg-background rounded-xl p-6 border shadow-sm">
                <div class="flex items-center gap-3 mb-4">
                  <div class="w-10 h-10 bg-gradient-to-r from-[#667eea] to-[#764ba2] rounded-full flex items-center justify-center">
                    <span class="text-white text-sm font-bold">AI</span>
                  </div>
                  <div>
                    <div class="font-bold">PYQS Assistant</div>
                    <div class="text-sm text-green-500 flex items-center gap-1">
                      <div class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
                      Online
                    </div>
                  </div>
                </div>
                <div class="space-y-3">
                  <div class="p-3 bg-gradient-to-r from-purple-50 to-blue-50 rounded-lg">
                    <div class="text-sm font-medium mb-2 flex items-center gap-2">
                      <Zap class="w-4 h-4 text-purple-600" />
                      AI Suggestion
                    </div>
                    <div class="text-xs text-muted-foreground">Based on your performance, focus more on Pharmacology this week.</div>
                  </div>
                  <div class="flex gap-2 flex-wrap">
                    <span class="px-2 py-1 bg-purple-100 text-purple-700 rounded-full text-xs">Quick Quiz</span>
                    <span class="px-2 py-1 bg-blue-100 text-blue-700 rounded-full text-xs">Explain Concept</span>
                    <span class="px-2 py-1 bg-indigo-100 text-indigo-700 rounded-full text-xs">Study Plan</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Mock Analytics Interface -->
            <div v-if="activeTab === 'analytics'" class="space-y-4">
              <div class="bg-background rounded-xl p-6 border shadow-sm">
                <div class="flex items-center gap-3 mb-4">
                  <div class="w-10 h-10 bg-gradient-to-r from-[#f093fb] to-[#f5576c] rounded-lg flex items-center justify-center">
                    <BarChart3 class="w-5 h-5 text-white" />
                  </div>
                  <div>
                    <div class="font-bold">Weekly Analytics</div>
                    <div class="text-sm text-muted-foreground">Performance Overview</div>
                  </div>
                </div>
                <div class="space-y-3">
                  <div class="grid grid-cols-2 gap-3">
                    <div class="p-3 bg-gradient-to-r from-pink-50 to-rose-50 rounded-lg">
                      <div class="text-2xl font-bold text-pink-600 mb-1">78%</div>
                      <div class="text-xs text-muted-foreground">Overall Accuracy</div>
                    </div>
                    <div class="p-3 bg-gradient-to-r from-blue-50 to-indigo-50 rounded-lg">
                      <div class="text-2xl font-bold text-blue-600 mb-1">156</div>
                      <div class="text-xs text-muted-foreground">Questions Solved</div>
                    </div>
                  </div>
                  <div class="p-3 bg-gradient-to-r from-yellow-50 to-orange-50 rounded-lg">
                    <div class="text-sm font-medium mb-2 flex items-center gap-2">
                      <Target class="w-4 h-4 text-orange-600" />
                      Focus Areas
                    </div>
                    <div class="flex gap-1">
                      <div class="h-2 bg-red-400 rounded flex-1"></div>
                      <div class="h-2 bg-yellow-400 rounded flex-1"></div>
                      <div class="h-2 bg-green-400 rounded flex-2"></div>
                    </div>
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

/* Responsive adjustments */
@media (max-width: 768px) {
  .gradient-text {
    font-size: 2rem;
  }
}
</style>