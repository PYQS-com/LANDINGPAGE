<script setup lang="ts">
import {
  Card,
  CardHeader,
  CardTitle,
  CardFooter,
  CardContent,
} from "@/components/ui/card";

import { Button } from "@/components/ui/button";

import { Send } from "lucide-vue-next";
</script>

<template>
  <section
    id="community"
    class="py-12"
  >
    <hr />
    <div class="container py-20 sm:py-20">
      <div class="lg:w-[60%] mx-auto">
        <Card
          class="bg-background shadow-none text-center flex flex-col items-center justify-center border-0"
        >
          <CardHeader>
            <CardTitle class="text-4xl md:text-5xl font-bold">
              <div class="telegram-icon-container mb-4">
                <Send class="telegram-icon" />
              </div>
              Ready to join our
              <span
                class="text-transparent bg-gradient-to-r from-[#0088cc] to-[#229ED9] bg-clip-text"
              >
                Telegram Community?
              </span>
            </CardTitle>
          </CardHeader>
          <CardContent class="lg:w-[80%] text-xl text-muted-foreground">
            Join our active Telegram community! Get instant updates, share resources, and connect with fellow NEET PG aspirants. Let's learn together! 📚✨
          </CardContent>

          <CardFooter>
            <Button as-child class="telegram-button">
              <a
                href="https://t.me/pyqscom"
                target="_blank"
              >
                Join Telegram
              </a>
            </Button>
          </CardFooter>
        </Card>
      </div>
    </div>
    <hr />
  </section>
</template>

<style scoped>
.telegram-icon-container {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
  margin: 0 auto;
  background: linear-gradient(135deg, #0088cc, #229ED9);
  border-radius: 50%;
  box-shadow: 0 4px 15px rgba(0, 136, 204, 0.3);
  transition: all 0.3s ease;
}

.telegram-icon {
  width: 40px;
  height: 40px;
  color: white;
  transform: rotate(-45deg);
}

.telegram-icon-container:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(0, 136, 204, 0.4);
}

.telegram-button {
  background: linear-gradient(135deg, #0088cc, #229ED9) !important;
  border: none !important;
  color: white !important;
  padding: 12px 24px;
  font-weight: 600;
  transition: all 0.3s ease;
}

.telegram-button:hover {
  background: linear-gradient(135deg, #0077b3, #1e8bc3) !important;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(0, 136, 204, 0.3);
}
</style>
