<script setup lang="ts">
import {
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from "@/components/ui/accordion";

interface FAQProps {
  question: string;
  answer: string;
  value: string;
}

const FAQList: FAQProps[] = [
  {
    question: "How fast can I deploy an AI agent?",
    answer: "With our platform, you can deploy an AI agent in just a few minutes, thanks to our streamlined, no-code process.",
    value: "item-1",
  },
  {
    question: "Do I need any technical skills to use the platform?",
    answer:
      "No. Our platform is designed for ease of use, requiring no coding or technical knowledge. Everything is intuitive, with templates and customization options to guide you.",
    value: "item-2",
  },
  {
    question: "Can I scale my AI agents as my business grows?",
    answer:
      "Yes! Our platform allows you to scale effortlessly by adding more AI agents as your business needs grow, without additional infrastructure or complexity.",
    value: "item-3",
  },
  {
    question: "What kind of tasks can AI agents automate?",
    answer:
      "AI agents can automate a wide range of tasks, from customer support and data processing to marketing automation and operational workflows.",
    value: "item-4",
  },
  {
    question: "Is the platform secure for handling sensitive data?",
    answer:
      "Absolutely. We prioritize security with robust protocols to ensure data protection and compliance with industry standards.",
    value: "item-5",
  },
];

</script>

<template>
  <section
    id="faq"
    class="container md:w-[700px] py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">FAQS</h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Common Questions
      </h2>
    </div>

    <Accordion
      type="single"
      collapsible
      class="AccordionRoot"
    >
      <AccordionItem
        v-for="{ question, answer, value } in FAQList"
        :key="value"
        :value="value"
      >
        <AccordionTrigger class="text-left"> {{ question }} </AccordionTrigger>

        <AccordionContent>{{ answer }}</AccordionContent>
      </AccordionItem>
    </Accordion>

    <h3 class="font-medium mt-4">
      Still have questions?
      <a
        href="#"
        class="text-muted-foreground"
      >
        <a
          href="#"
          class="underline"
          >Contact us</a
        >
      </a>
    </h3>
  </section>
</template>
