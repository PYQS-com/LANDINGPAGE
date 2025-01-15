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
    title: "Quick Access to Notes",
    description:
      "Get instant access to MBBS class notes and study materials, organized for your convenience.",
  },
  {
    icon: "badgeCheck",
    title: "Verified Content",
    description:
      "All materials are curated and verified to ensure accuracy and reliability for students.",
  },
  {
    icon: "goal",
    title: "Diverse Subjects",
    description:
      "Access notes and resources across various MBBS subjects, tailored for comprehensive learning.",
  },
  {
    icon: "pictureInPicture",
    title: "User-Friendly Interface",
    description:
      "Navigate through the platform effortlessly with an intuitive and simple design.",
  },
  {
    icon: "mousePointerClick",
    title: "Interactive Features",
    description:
      "Engage with interactive tools that enhance understanding and retention of complex topics.",
  },
  {
    icon: "newspaper",
    title: "Regular Updates",
    description:
      "Stay updated with the latest additions and improvements to the resources available on the platform.",
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
      Experience a seamless and enriching study platform designed specifically for MBBS students, offering verified, diverse, and interactive resources.
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
