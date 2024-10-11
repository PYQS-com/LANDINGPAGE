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
    badgeTitle: "Kickstart Your Journey",
    title: "Create New AI Agent",
    description:
      "Begin by defining your project’s objectives and requirements. Our intuitive interface guides you through creating a tailored project that aligns with your business goals.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1728667300/1_wwcwkh.png",
  },
  {
    badgeTitle: "Personalization",
    title: "Customize Your AI Agent",
    description:
      "Utilize our extensive library of templates and tools to customize your AI agent. Tailor its functionalities to address your specific operational needs and enhance performance.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1728669795/222_zkfqjl.png",
  },
  {
    badgeTitle: "Refine your agent",
    title: "Test and Optimize",
    description:
      "Run simulations and tests to ensure your AI agent operates seamlessly. Make adjustments as needed to optimize its performance before deployment.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1728670155/333_o1bvby.png",
  },
  {
    badgeTitle: "Deploy with Confidence",
    title: "Launch Your AI Agent",
    description:
      "Deploy your AI agent with a single click. Monitor its performance in real-time and make data-driven adjustments to maximize efficiency and impact.",
    image: "https://res.cloudinary.com/tesalab/image/upload/v1728670422/444_uvzh8x.gif",
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
