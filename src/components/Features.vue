<script setup lang="ts">
import { FunctionalComponent } from "vue";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

import {
  Gem,
  Goal,
  LucideProps,
  Presentation,
  Trophy,
  Zap,
} from "lucide-vue-next";

interface FeaturesProps {
  icon: FunctionalComponent<LucideProps> | string;
  title: string;
  description: string;
}

const featureList: FeaturesProps[] = [
  {
    icon: Zap,
    title: "Unique Athletic Background",
    description: "Former combat sports athlete with elite agility, reflexes, and a fresh approach to pickleball.",
  },
  {
    icon: Trophy,
    title: "Pro-Level Experience",
    description: "Competes on the PPA & APP tours with a 5.6 DUPR - real insight from the pro circuit.",
  },
  {
    icon: Goal,
    title: "Relatable Coaching Style",
    description: "Understands what it's like to start from scratch and makes improvement approachable for all levels.",
  },
  {
    icon: Gem,
    title: "Selkirk-Sponsored",
    description: "Backed by one of the top brands in pickleball - a mark of quality and professionalism.",
  },
  {
    icon: Presentation,
    title: "Custom-Tailored Lessons",
    description: "Every session is personalized to your skill level, goals, and learning style."
  },
];

const topRow = featureList.slice(0, 3);
const botRow = featureList.slice(3);
</script>

<template>
  <section
    id="features"
    class="container py-24 sm:py-32"
  >
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Features
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      What Makes Kaeden Different
    </h2>

    <!-- <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      🤣🤣
    </h3> -->

    <!-- <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4">
      <div
        v-for="{ icon, title, description } in featureList"
        :key="title"
      >
        <Card class="h-full bg-background border-0 shadow-none">
          <CardHeader class="flex justify-center items-center">
            <div
              class="bg-primary/20 p-2 rounded-full ring-8 ring-primary/10 mb-4"
            >
              <component
                :is="icon"
                class="size-6 text-primary"
              />
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground text-center">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div> -->

    <!-- First row: 3 columns -->
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
      <div v-for="{ icon, title, description } in topRow" :key="title">
        <Card class="h-full bg-background border-0 shadow-none">
          <CardHeader class="flex justify-center items-center">
            <div class="bg-primary/20 p-2 rounded-full ring-8 ring-primary/10 mb-4">
              <component :is="icon" class="size-6 text-primary" />
            </div>
            <CardTitle>{{ title }}</CardTitle>
          </CardHeader>
          <CardContent class="text-muted-foreground text-center">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div>

    <!-- Second row: 2 columns -->
    <div class="grid sm:grid-cols-2 gap-4">
      <div v-for="{ icon, title, description } in botRow" :key="title">
        <Card class="h-full bg-background border-0 shadow-none">
          <CardHeader class="flex justify-center items-center">
            <div class="bg-primary/20 p-2 rounded-full ring-8 ring-primary/10 mb-4">
              <component :is="icon" class="size-6 text-primary" />
            </div>
            <CardTitle>{{ title }}</CardTitle>
          </CardHeader>
          <CardContent class="text-muted-foreground text-center">
            {{ description }}
          </CardContent>
        </Card>
      </div>
    </div>

  </section>
</template>
