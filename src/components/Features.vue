<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

import {
  Paintbrush,
  MessageCircle,
  TabletSmartphone,
  BadgeCheck,
  Goal,
  PictureInPicture,
  MousePointerClick,
  Newspaper,
} from "lucide-vue-next";

interface FeaturesProps {
  icon: string;
  title: string;
  description: string;
}

const featureList: FeaturesProps[] = [
  {
    icon: "tabletSmartphone",
    title: "Instant AI Deployment",
    description:
      "Deploy fully functional AI agents within seconds, providing immediate automation solutions that reduce human dependency and errors.",
  },
  {
    icon: "badgeCheck",
    title: "Autonomous Workforce",
    description:
      "Empower your operations with AI agents that work independently, handling complex tasks without requiring constant supervision or intervention.",
  },
  {
    icon: "goal",
    title: "Agents Marketplace",
    description:
      "Easily scale your business by deploying additional AI agents as your operations grow, without the need for hiring or training new employees.",
  },
  {
    icon: "pictureInPicture",
    title: "Customizable Templates",
    description:
      "Leverage a wide range of AI templates that are fully customizable, allowing you to tailor AI solutions to your specific business needs.",
  },
  {
    icon: "mousePointerClick",
    title: "Seamless Workflow Integration",
    description:
      "Integrate AI agents seamlessly into your existing workflows, ensuring minimal disruption while maximizing productivity and efficiency.",
  },
  {
    icon: "newspaper",
    title: "Real-Time Adaptation",
    description:
      "AI agents continuously learn and adapt to evolving environments, ensuring that your business stays ahead of market changes and operational demands.",
  },
];

const iconMap: Record<
  string,
  | typeof TabletSmartphone
  | typeof BadgeCheck
  | typeof Goal
  | typeof PictureInPicture
  | typeof Paintbrush
  | typeof MousePointerClick
  | typeof MessageCircle
  | typeof Newspaper
> = {
  tabletSmartphone: TabletSmartphone,
  badgeCheck: BadgeCheck,
  goal: Goal,
  pictureInPicture: PictureInPicture,
  paintbrush: Paintbrush,
  mousePointerClick: MousePointerClick,
  messageCircle: MessageCircle,
  newspaper: Newspaper,
};
</script>

<template>
  <section
    id="features"
    class="container py-24 sm:py-32"
  >
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Features
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      What Makes Us Different
    </h2>

    <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      Unlock the potential of AI-driven automation with cutting-edge tools that set us apart from traditional competitors. Our platform delivers unmatched scalability, integration, and efficiency to revolutionize your business.
    </h3>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4">
      <div
        v-for="{ icon, title, description } in featureList"
        :key="title"
      >
        <Card class="h-full bg-background border-0 shadow-none">
          <CardHeader class="flex justify-center items-center">
            <div
              class="bg-primary/20 p-2 rounded-full ring-8 ring-primary/10 mb-4"
            >
              <component
                :is="iconMap[icon]"
                class="size-6 text-primary"
              />
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground text-center">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div>
  </section>
</template>

<style lang="less" scoped></style>
