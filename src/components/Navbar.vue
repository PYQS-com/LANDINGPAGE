<script lang="ts" setup>
import { ref } from "vue";

import { useColorMode } from "@vueuse/core";
const mode = useColorMode();
// mode.value = "dark";

import {
  NavigationMenu,
  NavigationMenuContent,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
  NavigationMenuTrigger,
} from "@/components/ui/navigation-menu";
import {
  Sheet,
  SheetContent,
  SheetFooter,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
} from "@/components/ui/sheet";

import { Button } from "@/components/ui/button";
import { Separator } from "@/components/ui/separator";

import { Menu, Moon, ArrowRight } from "lucide-vue-next";
import ToggleTheme from "./ToggleTheme.vue";

import FLECTRA_TRANSPARENT from "@/assets/logo.png";

interface RouteProps {
  href: string;
  label: string;
}

interface FeatureProps {
  title: string;
  description: string;
}

const routeList: RouteProps[] = [
  {
    href: "#features",
    label: "Features",
  },
  // {
  //   href: "#team",
  //   label: "Team",
  // },
  {
    href: "#contact",
    label: "Contact",
  },
  {
    href: "#faq",
    label: "FAQ",
  },
];

const featureList: FeatureProps[] = [
  {
    title: "PDF Notes Sharing",
    description: "Access shared MBBS class notes and PDF materials to enhance your study experience effortlessly.",
  },
  {
    title: "Organized Content",
    description: "Find materials sorted by subjects and topics for quick and easy access to what you need.",
  },
  {
    title: "User-Friendly Interface",
    description: "Navigate seamlessly through the platform designed specifically for student convenience.",
  },
  {
    title: "Collaborative Learning",
    description: "Share your own notes and help create a thriving community of learners.",
  },
  {
    title: "24/7 Availability",
    description: "Access your study materials anytime, anywhere, ensuring uninterrupted learning.",
  },
];

const isOpen = ref<boolean>(false);
</script>

<template>
  <header :class="{
    'shadow-light': mode === 'light',
    'shadow-dark': mode === 'dark',
    'w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto sticky border z-40 rounded-[60px] flex justify-between items-center p-2 bg-card shadow-md': true,
  }">
   <!-- <img :src="FLECTRA_TRANSPARENT" alt="Flectra Logo" height="36px" width="36px" /> -->
    <a href="/" class="font-bold text-lg flex items-center ml-3">
      PYQS</a>
    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Button variant="outline" class="mr-2">
        <span v-if="mode === 'light'" class="flex items-center gap-2">
          <div class="w-6 h-6 rounded-full bg-gradient-to-r from-orange-300 to-amber-300"></div>
          Light
        </span>
        <span v-else class="flex items-center gap-2">
          <Moon class="size-5" />
          Dark
        </span>
      </Button>

      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu @click="isOpen = true" class="cursor-pointer" />
        </SheetTrigger>

        <SheetContent side="left" class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card">
          <div>
            <SheetHeader class="mb-4 ml-4">
              <SheetTitle class="flex items-center">
                <a href="/" class="flex items-center">
                  <img :src="FLECTRA_TRANSPARENT" alt="Flectra Logo" height="36px" width="36px" />
                  PYQS
                </a>
              </SheetTitle>
            </SheetHeader>

            <div class="flex flex-col gap-2">
              <Button v-for="{ href, label } in routeList" :key="label" as-child variant="ghost"
                class="justify-start text-base">
                <a @click="isOpen = false" :href="href">
                  {{ label }}
                </a>
              </Button>
            </div>
          </div>

          <SheetFooter class="flex-col sm:flex-col justify-start items-start">
            <Separator class="mb-2" />

            <ToggleTheme />
          </SheetFooter>
        </SheetContent>
      </Sheet>
    </div>

    <!-- Desktop -->
    <NavigationMenu class="hidden lg:block">
      <NavigationMenuList>
        <NavigationMenuItem>
          <NavigationMenuTrigger class="bg-card text-base">
            Features
          </NavigationMenuTrigger>
          <NavigationMenuContent>
            <div class="grid w-[250px] p-4">
              <ul class="flex flex-col gap-2">
                <li v-for="{ title, description } in featureList" :key="title"
                  class="rounded-md p-3 text-sm hover:bg-muted">
                  <p class="mb-1 font-semibold leading-none text-foreground">
                    {{ title }}
                  </p>
                  <p class="line-clamp-2 text-muted-foreground">
                    {{ description }}
                  </p>
                </li>
              </ul>
            </div>

          </NavigationMenuContent>
        </NavigationMenuItem>

        <NavigationMenuItem>
          <NavigationMenuLink asChild>
            <Button v-for="{ href, label } in routeList" :key="label" as-child variant="ghost"
              class="justify-start text-base">
              <a :href="href">
                {{ label }}
              </a>
            </Button>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>

    <div class="hidden lg:flex items-center gap-2">
      <Button variant="outline" @click="mode = mode === 'dark' ? 'light' : 'dark'">
        <span v-if="mode === 'light'" class="flex items-center gap-2">
          <div class="w-6 h-6 rounded-full bg-gradient-to-r from-orange-300 to-amber-300"></div>
          Light
        </span>
        <span v-else class="flex items-center gap-2">
          <Moon class="size-5" />
          Dark
        </span>
      </Button>

      <Button variant="outline" class="flex items-center gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24">
          <path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4" />
          <path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853" />
          <path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z" fill="#FBBC05" />
          <path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335" />
        </svg>
        Sign In
        <ArrowRight class="size-4" />
      </Button>
    </div>
  </header>
</template>

<style scoped>
.shadow-light {
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.085);
}

.shadow-dark {
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.141);
}
</style>
