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
  gear,
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
    class="container py-24 sm:py-32"
  >
    <div class="grid lg:grid-cols-2 place-items-center lg:gap-24">
      <div>
  <h2 class="text-lg text-primary mb-2 tracking-wider">Why Choose Us</h2>

  <h2 class="text-3xl md:text-4xl font-bold mb-4">
    Simplify Your MBBS Journey
  </h2>
  <p class="text-xl text-muted-foreground mb-8">
    Discover a platform tailored to meet the needs of MBBS students, offering structured resources, efficient tools, and a collaborative community to enhance your medical education experience.
  </p>
</div>


      <div class="grid lg:grid-cols-2 gap-4 w-full">
        <Card
          v-for="({ icon, title, description }, index) in benefitList"
          :key="title"
          class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background transition-all delay-75 group/number"
        >
          <CardHeader>
            <div class="flex justify-between">
              <component
                class="size-8 mb-6 text-primary"
                :is="iconMap[icon]"
              />

              <span
                class="text-5xl text-muted-foreground/15 font-medium transition-all delay-75 group-hover/number:text-muted-foreground/30"
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
