<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

import {
  Sparkle,
  Tag,
  Paintbrush,
  Blocks,
  LineChart,
  Wallet,
  ShieldCheck,
  Workflow,
} from "lucide-vue-next";

interface BenefitsProps {
  icon: string;
  title: string;
  description: string;
}

const benefitList: BenefitsProps[] = [
  {
    icon: "blocks",
    title: "Comprehensive Study Resources",
    description:
      "Access a vast collection of MBBS notes and study materials, meticulously organized for easy navigation.",
  },
  {
    icon: "lineChart",
    title: "Efficient Learning Tools",
    description:
      "Streamline your study process with tools designed to help you learn faster and retain more information.",
  },
  {
    icon: "wallet",
    title: "Affordable Education",
    description:
      "Enjoy high-quality resources at no additional cost, making education accessible for every student.",
  },
  {
    icon: "sparkle",
    title: "Enhanced Study Experience",
    description:
      "Utilize interactive notes and materials that simplify complex topics, making your learning journey enjoyable.",
  },
  {
    icon: "shieldCheck",
    title: "Secure Access",
    description:
      "Your data and resources are safeguarded with top-notch security measures, ensuring a worry-free experience.",
  },
  {
    icon: "workflow",
    title: "Collaborative Environment",
    description:
      "Engage with a community of learners by sharing notes and insights, fostering a collaborative learning space.",
  },
];


const iconMap: Record<
  string,
  | typeof Sparkle
  | typeof Workflow
  | typeof Tag
  | typeof Paintbrush
  | typeof Blocks
  | typeof LineChart
  | typeof Wallet
  | typeof ShieldCheck
> = {
  sparkle: Sparkle,
  workflow: Workflow,
  shieldCheck: ShieldCheck,
  tag: Tag,
  paintbrush: Paintbrush,
  blocks: Blocks,
  lineChart: LineChart,
  wallet: Wallet,
};
</script>

<template>
  <section
    id="benefits"
    class="container py-24 sm:py-32 relative overflow-hidden"
  >
    <!-- Remove the blob background div entirely -->
    
    <div class="grid lg:grid-cols-2 place-items-center lg:gap-24">
      <!-- Left side content with faster animations -->
      <div class="benefits-content animate-fade-in" style="animation-duration: 0.5s;">
        <h2 class="text-lg text-primary mb-2 tracking-wider animate-slide-up" style="animation-delay: 50ms; animation-duration: 0.5s;">
          Why Choose Us
        </h2>

        <h2 class="text-3xl md:text-4xl font-bold mb-4 gradient-text animate-slide-up" style="animation-delay: 100ms; animation-duration: 0.5s;">
          Simplify Your MBBS Journey
        </h2>
        
        <p class="text-xl text-muted-foreground mb-8 animate-slide-up" style="animation-delay: 150ms; animation-duration: 0.5s;">
          Discover a platform tailored to meet the needs of MBBS students, offering structured resources, efficient tools, and a collaborative community to enhance your medical education experience.
        </p>
      </div>

      <!-- Benefits cards with improved animations -->
      <div class="grid lg:grid-cols-2 gap-4 w-full benefits-grid">
        <Card
          v-for="({ icon, title, description }, index) in benefitList"
          :key="title"
          class="benefit-card bg-card/50 backdrop-blur-sm border-muted/30 hover:border-primary/20 dark:bg-card dark:hover:bg-card/80 transition-all group/card animate-fade-in"
          :style="{ animationDelay: `${(index * 75)}ms`, animationDuration: '0.4s' }"
        >
          <CardHeader>
            <div class="flex justify-between">
              <component
                class="size-8 mb-6 benefit-icon"
                :class="`gradient-icon-${index % 5}`"
                :is="iconMap[icon]"
              />

              <span
                class="text-5xl text-muted-foreground/10 font-medium transition-all group-hover/card:text-muted-foreground/20"
                >0{{ index + 1 }}</span
              >
            </div>

            <CardTitle>{{ title }}</CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Remove the blob background styling entirely */

/* Gradient text styling from Hero - keep this */
.gradient-text {
  background: linear-gradient(90deg, #8c38ea 0%, #5c50eb 50%, #395deb 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
}

/* Improved benefit card styling */
.benefit-card {
  border-width: 1px;
  transition: all 0.3s cubic-bezier(0.22, 1, 0.36, 1);
  position: relative;
  overflow: hidden;
}

.benefit-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 25px -5px rgba(92, 80, 235, 0.05),
              0 8px 10px -6px rgba(92, 80, 235, 0.01);
}

.benefit-card::after {
  content: '';
  position: absolute;
  inset: 0;
  z-index: -1;
  opacity: 0;
  transform-origin: bottom;
  transform: scaleY(0);
  background: linear-gradient(to bottom, rgba(140, 56, 234, 0.02), rgba(92, 80, 235, 0.03));
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.benefit-card:hover::after {
  opacity: 1;
  transform: scaleY(1);
}

/* Gradient icon styling to match hero section colors - keep these */
.gradient-icon-0 {
  color: transparent;
  background: linear-gradient(45deg, #8c38ea, #5c50eb);
  background-clip: text;
  -webkit-background-clip: text;
  transition: transform 0.3s ease, filter 0.3s ease;
}

.gradient-icon-1 {
  color: transparent;
  background: linear-gradient(45deg, #395deb, #03a9f4);
  background-clip: text;
  -webkit-background-clip: text;
  transition: transform 0.3s ease, filter 0.3s ease;
}

.gradient-icon-2 {
  color: transparent;
  background: linear-gradient(45deg, #4caf50, #8bc34a);
  background-clip: text;
  -webkit-background-clip: text;
  transition: transform 0.3s ease, filter 0.3s ease;
}

.gradient-icon-3 {
  color: transparent;
  background: linear-gradient(45deg, #e91e63, #f06292);
  background-clip: text;
  -webkit-background-clip: text;
  transition: transform 0.3s ease, filter 0.3s ease;
}

.gradient-icon-4 {
  color: transparent;
  background: linear-gradient(45deg, #ff9800, #ffb300);
  background-clip: text;
  -webkit-background-clip: text;
  transition: transform 0.3s ease, filter 0.3s ease;
}

/* Faster animation keyframes */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(15px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Animation classes */
.animate-fade-in {
  opacity: 0;
  animation: fadeIn forwards;
}

.animate-slide-up {
  opacity: 0;
  animation: slideUp forwards;
}

/* Better icon hover effect */
.benefit-icon {
  transform-origin: center;
  transition: transform 0.2s cubic-bezier(0.22, 1, 0.36, 1);
}

.benefit-card:hover .benefit-icon {
  transform: scale(1.15) rotate(5deg);
  filter: drop-shadow(0 4px 8px rgba(92, 80, 235, 0.25));
}

/* Grid animation for staggered card appearance */
.benefits-grid {
  perspective: 1000px;
}

/* Mobile optimization */
@media (max-width: 768px) {
  .benefits-grid {
    margin-top: 2rem;
  }
  
  .benefit-card {
    margin-bottom: 0.5rem;
  }
}
</style>
