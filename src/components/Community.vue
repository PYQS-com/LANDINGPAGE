<script setup lang="ts">
import {
  Card,
  CardHeader,
  CardTitle,
  CardFooter,
  CardContent,
} from "@/components/ui/card";

import { Button } from "@/components/ui/button";

// Telegram icon will be created as SVG directly in template
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
                <svg class="telegram-icon" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.64 6.8c-.15 1.58-.8 5.42-1.13 7.19-.14.75-.42 1-.68 1.03-.58.05-1.02-.38-1.58-.75-.88-.58-1.38-.94-2.23-1.5-.99-.65-.35-1.01.22-1.59.15-.15 2.71-2.48 2.76-2.69a.2.2 0 0 0-.05-.18c-.06-.05-.14-.03-.21-.02-.09.02-.15.04-.15.04s-1.7 1.08-4.81 3.15c-.45.31-.86.46-1.23.45-.4-.01-1.18-.23-1.76-.42-.7-.23-1.26-.35-1.21-.74.03-.2.36-.4.98-.6 3.76-1.65 6.26-2.73 7.51-3.26 3.58-1.51 4.32-1.78 4.81-1.78.11 0 .35.03.51.17.13.12.17.27.19.38-.01.06-.01.24-.01.24z"/>
                </svg>
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
                href="https://t.me/pyqs_com"
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
  width: 60px;
  height: 60px;
  margin: 0 auto;
  background: linear-gradient(135deg, #0088cc, #229ED9);
  border-radius: 50%;
  box-shadow: 0 4px 15px rgba(0, 136, 204, 0.3);
  transition: all 0.3s ease;
}

@media (min-width: 768px) {
  .telegram-icon-container {
    width: 80px;
    height: 80px;
  }
  
  .telegram-icon {
    width: 40px;
    height: 40px;
  }
}

.telegram-icon {
  width: 30px;
  height: 30px;
  color: white;
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
