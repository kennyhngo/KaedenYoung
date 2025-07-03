<script setup lang="ts">
import { Avatar, AvatarFallback, AvatarImage } from "@/components/ui/avatar";

import {
  Card,
  CardContent,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import {
  Carousel,
  CarouselContent,
  CarouselItem,
  // CarouselNext,
  // CarouselPrevious,
} from "@/components/ui/carousel";

import { Star } from "lucide-vue-next";

interface ReviewProps {
  image: string;
  name: string;
  userName?: string;
  comment: string;
}

const reviewList: ReviewProps[] = [
  {
    image: "chloe.jpg",
    name: "Jibby",
    comment: "One of the 2.5 players of all time.",
  },
  {
    image: "https://www.ppatour.com/wp-content/uploads/2025/03/Ben-Johns.png",
    name: "Ben Johns",
    comment: "Training with Kaeden has completely changed my approach to pickleball. His attention to detail and real-time feedback during group play has helped me improve my strategy and shot selection. Plus, his positive energy makes every session fun and productive.",
  },
  {
    image: "https://imageio.forbes.com/specials-images/imageserve/6372abd4275c87dec8a8fb83/0x0.jpg?format=jpg&height=1200&width=400&fit=bounds",
    name: "Anna Leigh Waters",
    comment: "I started working with Kaeden after seeing him compete at a local tournament. His ability to spot small adjustments in my technique made a huge difference in my game. He's approachable, knowledgeable, and genuinely invested in helping his students succeed.",
  }
];
</script>

<template>
  <section
    id="testimonials"
    class="container py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
        Testimonials
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
        Hear What Our Clients Say
      </h2>
    </div>

    <Carousel
      :opts="{ align: 'start', active: false }"
      class="relative w-[80%] sm:w-[90%] lg:max-w-screen-xl mx-auto"
    >
      <CarouselContent>
        <CarouselItem
          v-for="review in reviewList"
          :key="review.name"
          class="md:basis-1/2 lg:basis-1/3"
        >
          <Card class="bg-muted/50 dark:bg-card">
            <CardContent class="pt-6 pb-0">
              <div class="flex gap-1 pb-6">
                <Star class="size-4 fill-primary text-primary" />
                <Star class="size-4 fill-primary text-primary" />
                <Star class="size-4 fill-primary text-primary" />
                <Star class="size-4 fill-primary text-primary" />
                <Star class="size-4 fill-primary text-primary" />
              </div>

              "{{ review.comment }}"
            </CardContent>

            <CardHeader>
              <div class="flex flex-row items-center gap-4">
                <Avatar>
                  <AvatarImage
                    :src="review.image"
                    alt="@radix-vue"
                  />
                  <AvatarFallback>SV</AvatarFallback>
                </Avatar>

                <div class="flex flex-col">
                  <CardTitle class="text-lg">{{ review.name }}</CardTitle>
                  <CardDescription>{{ review.userName }}</CardDescription>
                </div>
              </div>
            </CardHeader>
          </Card>
        </CarouselItem>
      </CarouselContent>
      <!-- <CarouselPrevious />
      <CarouselNext /> -->
    </Carousel>
  </section>
</template>
