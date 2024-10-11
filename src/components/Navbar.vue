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

import { ChevronsDown, Menu } from "lucide-vue-next";
import GithubIcon from "@/icons/GithubIcon.vue";
import ToggleTheme from "./ToggleTheme.vue";

import FLECTRA_TRANSPARENT from "@/assets/FLECTRA_TRANSPARENT.png";
import NAV_IMG from "@/assets/NAV_IMG.gif";

interface RouteProps {
  href: string;
  label: string;
}

interface FeatureProps {
  title: string;
  description: string;
}

const routeList: RouteProps[] = [
  // {
  //   href: "#testimonials",
  //   label: "Testimonials",
  // },
  {
    href: "#features",
    label: "Features",
  },
  {
    href: "#team",
    label: "Team",
  },
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
    title: "AI Agents",
    // description: "Deploy intelligent agents instantly to handle repetitive tasks, improve operational efficiency, and reduce human error.",
  },
  {
    title: "Agentic Workforce",
    // description:
    //   "Create a fully autonomous workforce capable of making decisions, performing tasks, and adapting to workflows without human intervention.",
  },
  {
    title: "AI Tools",
    // description:
    //   "Access an array of pre-built AI tools that can be customized and deployed in minutes to automate various business processes.",
  },
  {
    title: "Templates & Marketplace",
    // description:
    //   "Choose from a variety of pre-built templates and AI models available in the marketplace to accelerate your AI development process.",
  },
  {
    title: "AI Dashboard",
    // description:
    //   "Moniter every aspect of your AI agents, workforce, and tools from a centralized dashboard that provides real-time insights and analytics.",
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
    <a href="/" class="font-bold text-lg flex items-center">
      <!-- <ChevronsDown
        class="bg-gradient-to-tr from-primary via-primary/70 to-primary rounded-lg w-9 h-9 mr-2 border text-white"
      /> -->
      <img :src="FLECTRA_TRANSPARENT" alt="Flectra Logo" height="36px" width="36px" />
      Flectra.ai</a>
    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
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
                  Flectra.ai
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
            Products
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

    <div class="hidden lg:flex">
      <ToggleTheme />

      <!-- <Button as-child size="sm" variant="ghost" aria-label="View on GitHub">
        <a aria-label="View on GitHub" href="https://github.com/leoMirandaa/shadcn-vue-landing-page.git"
          target="_blank">
          <GithubIcon class="size-5" />
        </a>
      </Button> -->
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
