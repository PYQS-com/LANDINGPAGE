<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

interface HowItWorksProps {
  badgeTitle: string;
  title: string;
  description: string;
  image: string;
}

const HowItWorksList: HowItWorksProps[] = [
  {
    badgeTitle: "Start Your Learning",
    title: "Access MBBS Notes",
    description:
      "Begin your journey by exploring a vast collection of MBBS notes tailored to your syllabus. Our intuitive platform makes it easy to find the resources you need.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1735316949/14_pklxoy.png",
  },
  {
    badgeTitle: "Gamification",
    title: "Personalised experience",
    description:
      "Experience the incredible benefits of gamification, making learning fun and engaging. Earn rewards and track your progress as you learn.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1735316950/16_wi9uhm.png",
  },
  {
    badgeTitle: "Enhance Your Learning",
    title: "Interactive Tools",
    description:
      "Utilize interactive features to test your knowledge and refine your understanding of complex topics, ensuring better retention.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1735316949/17_pbztvs.png",
  },
  {
    badgeTitle: "Achieve Your Goals",
    title: "Stay Updated",
    description:
      "Stay ahead with regular updates to our content library. Access the latest notes and resources to ensure you are always prepared.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1735316950/15_dthjvc.png",
  },
];

</script>

<template>
  <section
    id="features"
    class="container py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
        How It Works
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Step-by-Step Process
      </h2>
    </div>

    <div class="lg:w-[80%] mx-auto relative">
      <div
        v-for="(
          { badgeTitle, title, description, image }, index
        ) in HowItWorksList"
        :key="title"
        :class="[
          'flex mb-8 items-center',
          { ' flex-row-reverse': index % 2 !== 0 },
        ]"
      >
        <Card class="h-full bg-transparent border-0 shadow-none">
          <CardHeader>
            <div class="pb-4">
              <Badge>{{ badgeTitle }}</Badge>
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground w-[80%]">
            {{ description }}
          </CardContent>
        </Card>

        <img
          :src="image"
          :alt="`Image describing ${title} `"
          className="w-[150px]  md:w-[250px] lg:w-[300px] mx-auto scale-x-100 rounded-[20px]"
        />
        <div
          :class="[
            '-z-10 absolute right-0 w-44 h-72  lg:w-64 lg:h-80 rounded-full bg-primary/15 dark:bg-primary/10 blur-3xl',
            {
              'left-0': index % 2 !== 0,
            },
          ]"
        ></div>
      </div>
    </div>
  </section>
</template>
