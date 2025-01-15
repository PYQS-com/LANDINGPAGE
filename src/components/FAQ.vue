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
    question: "How can I access MBBS notes?",
    answer: "Simply log in to the platform and browse through the organized categories to find the notes you need.",
    value: "item-1",
  },
  {
    question: "Is the platform free to use?",
    answer:
      "Yes, pyqs offers both freemium and premium plans, with the basic features available for free to all users.",
    value: "item-2",
  },
  {
    question: "Can I contribute my own notes?",
    answer:
      "Absolutely! The platform encourages students to upload and share their notes to help others in the community.",
    value: "item-3",
  },
  {
    question: "Are the notes verified for accuracy?",
    answer:
      "Yes, all notes undergo a verification process to ensure their accuracy and relevance to the MBBS syllabus.",
    value: "item-4",
  },
  {
    question: "How often are new notes added?",
    answer:
      "New notes and resources are added regularly to ensure the platform stays up-to-date with the latest syllabus and study materials.",
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
