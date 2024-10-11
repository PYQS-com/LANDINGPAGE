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
    title: "Faster Project Completion",
    description:
      "Reduce project timelines by automating routine tasks with AI agents, allowing your teams to focus on strategic, high-impact activities.",
  },
  {
    icon: "lineChart",
    title: "Scalable Automation",
    description:
      "Effortlessly scale your operations with AI agents that grow with your business, minimizing the need for additional human resources as demand increases.",
  },
  {
    icon: "wallet",
    title: "Cost Reduction",
    description:
      "Significantly lower operational expenses by automating repetitive tasks, reducing errors, and cutting down on the need for additional hires.",
  },
  {
    icon: "sparkle",
    title: "Improved Efficiency",
    description:
      "Streamline workflows with AI agents that handle tasks 24/7, ensuring consistent performance, reducing bottlenecks, and increasing overall efficiency.",
  },
  {
    icon: "shieldCheck",
    title: "Enhanced Security",
    description:
      "Protect sensitive company data with AI agents that ensure compliance with security protocols, safeguarding against data breaches and cyber threats.",
  },
  {
    icon: "workflow",
    title: "Boosted Productivity",
    description:
      "Allow your human employees to focus on high-value tasks while AI agents manage routine operations, resulting in a marked increase in team productivity.",
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
  workflow:Workflow,
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
    Empower Your Business with AI
  </h2>
  <p class="text-xl text-muted-foreground mb-8">
    Transform your operations with cutting-edge autonomous AI agents designed to streamline processes, boost efficiency, and scale effortlessly. Our platform is your gateway to a smarter, faster, and more cost-effective future.
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
