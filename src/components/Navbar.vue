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

import { Menu, Moon, ArrowRight, UserPlus } from "lucide-vue-next";
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
    title: "PYQS AI Assistant",
    description: "Get personalized study guidance and instant answers to your questions with our intelligent AI assistant.",
  },
  {
    title: "Gamification",
    description: "Earn points, unlock achievements, and compete with peers to make learning more engaging and fun.",
  },
  {
    title: "AI Analytics",
    description: "Track your learning progress with smart analytics that provide insights into your study patterns and performance.",
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
      PYQs.com</a>
    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Button variant="outline" class="mr-2" @click="mode = mode === 'dark' ? 'light' : 'dark'">
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
                  PYQs.com
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

      <Button as-child variant="outline" class="join-waitlist-button">
        <a href="https://tally.so/r/wM0azk" target="_blank" rel="noopener noreferrer" class="flex items-center gap-2">
          <UserPlus class="size-4 flex-shrink-0" />
          <span>Join</span>
          <ArrowRight class="size-4 flex-shrink-0" />
        </a>
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
