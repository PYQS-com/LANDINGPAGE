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
    question: "What exams does PYQS support?",
    answer: "PYQS supports NEET PG, INI-CET, FMGE, and other major medical entrance exams with comprehensive previous year question banks and study materials.",
    value: "item-1",
  },
  {
    question: "How does the AI Assistant help with studies?",
    answer: "Our AI Assistant provides instant answers to medical queries, generates personalized quizzes, explains complex concepts, and offers study recommendations based on your performance.",
    value: "item-2",
  },
  {
    question: "What is Gamified Learning on PYQS?",
    answer: "Gamified Learning makes studying fun with XP points, achievement badges, leaderboards, and streak counters. You level up as you master medical topics and compete with peers.",
    value: "item-3",
  },
  {
    question: "How does Smart Analytics track my progress?",
    answer: "Smart Analytics monitors your performance across subjects, identifies weak areas, tracks study time, and provides insights to optimize your preparation strategy.",
    value: "item-4",
  },
  {
    question: "Can I access previous year questions from multiple years?",
    answer: "Yes, PYQS provides comprehensive question banks from the last 20+ years for NEET PG, with detailed explanations and topic-wise categorization for better preparation.",
    value: "item-5",
  },
  {
    question: "Is PYQS available 24/7?",
    answer: "Absolutely! PYQS is available round the clock, so you can study anytime, anywhere. Our AI Assistant and all features work 24/7 to support your medical exam preparation.",
    value: "item-6",
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
