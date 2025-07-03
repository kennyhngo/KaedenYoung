<script setup lang="ts">
import { Button } from "@/components/ui/button";
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import { Check } from "lucide-vue-next";

enum PopularPlan {
  NO = 0,
  YES = 1,
}

interface PlanProps {
  title: string;
  popular: PopularPlan;
  price: number;
  pricingDetails?: [number, number][];
  description: string;
  buttonText: string;
  buttonLink: string;
  benefitList: string[];
}

const plans: PlanProps[] = [
  {
    title: "Private Lessons",
    popular: 0,
    price: 75,
    description:
      "60 minute private session",
    buttonText: "Book private session",
    buttonLink: "https://calendly.com/camelbacks45/30min",
    benefitList: [
      "60-minute individualized session with a pro",
      "Tailored to your unique goals and skill level",
      "Improve serves, returns, drops, and more",
      "Targeted instruction with actionable feedback",
      "Build technique, strategy, and on-court confidence",
    ],
  },
  {
    title: "Group Play",
    popular: 0,
    price: 0,
    pricingDetails: [
      [30, 3],
      [40, 2],
    ],
    description:
      "60 minute group session",
    buttonText: "Book group session",
    buttonLink: "https://calendly.com/camelbacks45/group-play-with-kaeden",
    benefitList: [
      "60-minute live session with a pro",
      "Play alongside Kaeden with real-time coaching",
      "Perfect for groups of 2 or 3 players",
      "Focus on strategy, positioning, and gameplay",
      "Boost your skills in a fun, competitive environment",
    ],
  },
  {
    title: "Film Analysis",
    popular: 0,
    price: 30,
    description:
      "30 minute film analysis",
    buttonText: "Book review session",
    buttonLink: "https://calendly.com/camelbacks45/analyze-film",
    benefitList: [
      "30-minute personalized film analysis session",
      "Get expert feedback on your recorded gameplay",
      "Identify strengths and key areas for improvement",
      "Break down technique, strategy, and decisions",
      "Gain insights to elevate your performance",
    ],
  },
];

// const validCalendlyMap = ref<Record<string, boolean>>({});
// onMounted(async () => {
//   for (const plan of plans) {
//     const isValid = await isValidCalendlyUrl(plan.buttonLink);
//     validCalendlyMap.value[plan.buttonLink] = isValid;
//   }
// });
</script>

<template>
  <section 
    id="pricing" 
    class="container py-24 sm:py-32"
  >
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Service &amp; Rates
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Learn from a pro
    </h2>

    <h3
      class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground pb-14"
    >
      Both card & cash are accepted as forms of payment
    </h3>

    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 lg:gap-4">
      <Card
        v-for="{
          title,
          popular,
          price,
          pricingDetails,
          description,
          buttonText,
          buttonLink,
          benefitList,
        } in plans"
        :key="title"
        :class="{
          'drop-shadow-xl shadow-black/10 dark:shadow-white/10 border-[1.5px] border-primary lg:scale-[1.1]':
            popular === PopularPlan?.YES,
        }"
      >
        <CardHeader>
          <CardTitle class="pb-2">
            {{ title }}
          </CardTitle>

          <CardDescription class="pb-4">{{ description }}</CardDescription>

          <div v-if="pricingDetails?.length">
            <div
              v-for="[price, groupSize] in pricingDetails"
              :key="`${price}-${groupSize}`"
            >
              <span class="text-3xl font-bold">${{ price }}</span>
              <span class="text-xl text-muted-foreground">/person (Group of {{ groupSize }})</span>
            </div>
          </div>
          <div v-else>
            <span class="text-3xl font-bold">${{ price }}</span>
          </div>
        </CardHeader>

        <CardContent class="flex">
          <div class="space-y-4">
            <span
              v-for="benefit in benefitList"
              :key="benefit"
              class="flex"
            >
              <Check class="text-primary mr-2" />
              <h3>{{ benefit }}</h3>
            </span>
          </div>
        </CardContent>

        <CardFooter>
          <!-- <template v-if="validCalendlyMap[buttonLink] !== false"> -->
            <a
              :href="buttonLink"
              target="_blank"
              rel="noopener noreferrer"
              class="w-full"
            >
              <Button
                variant="default"
                class="w-full"
              >
                {{ buttonText }}
              </Button>
            </a>
          <!-- </template> -->
          <!-- <template v-else>
            <Button
              variant="secondary"
              class="w-full"
              disabled
            >
              Link Not Available
            </Button>
          </template> -->
        </CardFooter>
      </Card>
    </div>
  </section>
</template>
