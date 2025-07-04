<script setup lang="ts">
import { Card } from "@/components/ui/card";
</script>

<template>
  <section
    id="benefits"
    class="container py-24 sm:py-32"
  >
    <div class="grid lg:grid-cols-2 place-items-center lg:gap-24">

      <div class="grid lg:grid-cols-1 gap-4 w-full">
        <Card class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background transition-all delay-75 group/number p-4 flex justify-center border-0">
          <img 
            :src="'kaeden-fish.jpg'" 
            alt="Kaeden with a fish he caught."
            class="rounded-full object-cover"
          />
        </Card>
      </div>

      <!-- <div class="grid lg:grid-cols-2 gap-4 w-full">
        <Card
          v-for="({ icon, title, description }, index) in benefitList"
          :key="title"
          class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background transition-all delay-75 group/number"
        >
          <CardHeader>
            <div class="flex justify-between">
              <component
                class="size-8 mb-6 text-primary"
                :is="iconMap[icon]"
              />

              <span
                class="text-5xl text-muted-foreground/15 font-medium transition-all delay-75 group-hover/number:text-muted-foreground/30"
                >0{{ index + 1 }}</span
              >
            </div>

            <CardTitle>{{ title }}</CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground">
            {{ description }}
          </CardContent>
        </Card>
      </div> -->


      <div>
        <!-- <h2 class="text-lg text-primary mb-2 tracking-wider">Benefits</h2> -->

        <h2 class="text-3xl md:text-4xl font-bold mb-4">
          Meet Coach Kaeden
        </h2>
        <p class="text-xl text-muted-foreground mb-8">
          Kaeden Young is a professional pickleball player based out of Grand Rapids, Michigan. With a background in combat sports rather than racquet sports, Kaeden brings a unique perspective and athleticism to the game. Over the past two years, he has competed on both the PPA and APP tours, earning a reputation as one of the pros in Michigan. 
        </p>
        <p class="text-xl text-muted-foreground mb-8">
          Kaeden's matches have been featured on YouTube, and he currently holds a DUPR rating of 5.6. Sponsored by Selkirk Sports, Kaeden combines his competitive experience with a passion for teaching, offering expert instruction and personalized coaching. When he's not on the court, Kaeden enjoys fishing and exploring the outdoors. Kaeden is dedicated to helping players of all levels reach their full potential.
        </p>
      </div>

    </div>
  </section>
</template>
