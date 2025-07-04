<script setup lang="ts">
import { ref } from 'vue';
import { Card, CardContent } from '@/components/ui/card'
import { 
  Dialog,
  DialogContent,
  DialogTrigger,
  DialogClose,
  DialogTitle,
  DialogDescription,
} from '@/components/ui/dialog';
import {
  Carousel,
  CarouselContent,
  CarouselItem,
  CarouselNext,
  CarouselPrevious,
} from "@/components/ui/carousel";

const selectedImage = ref<string | null>(null);
</script>

<template>
  <section class="container">
    <div
      class="grid place-items-center lg:max-w-screen-xl gap-8 mx-auto py-20 md:py-32"
    >
      <div class="text-center space-y-8">
        <div
          class="max-w-screen-md mx-auto text-center text-5xl md:text-6xl font-bold"
        >
          <h1>
            <span
              class="text-transparent bg-gradient-to-r from-[#D247BF] to-primary bg-clip-text"
              >Kaeden Young
            </span>
          </h1>
        </div>

        <p class="max-w-screen-sm mx-auto text-xl text-muted-foreground">
          Professional pickleball player & coach based in Grand Rapids, Michigan.
        </p>

        <!-- <div class="space-y-4 md:space-y-0 md:space-x-4">
          <Button class="w-5/6 md:w-1/4 font-bold group/arrow">
            Get Started
            <ArrowRight
              class="size-5 ml-2 group-hover/arrow:translate-x-1 transition-transform"
            />
          </Button>

          <Button
            as-child
            variant="secondary"
            class="w-5/6 md:w-1/4 font-bold"
          >
            <a
              href="https://github.com/leoMirandaa/shadcn-vue-landing-page.git"
              target="_blank"
              >Github respository</a
            >
          </Button>
        </div> -->
      </div>

      <div class="relative group mt-14">
        <!-- gradient shadow -->
        <div
          class="absolute -top-6 right-12 w-[90%] h-12 lg:h-[80%] bg-primary/50 blur-3xl rounded-full img-shadow-animation"
        ></div>

        <!-- <img
          class="w-full md:w-[1200px] mx-auto rounded-lg relative rouded-lg leading-none flex items-center border border-t-2 border-t-primary/30 img-border-animation"
          :src="
            mode == 'light' ? 'hero-image-light.jpg' : 'hero-image-dark.jpg'
          "
          alt="dashboard using shadcn-vue"
        /> -->

        <img
          class="w-full md:w-[1200px] mx-auto rounded-lg relative rouded-lg leading-none flex items-center border border-t-2 border-t-primary/30 img-border-animation"
          :src="'kaeden-hero.jpg'"
          alt="Kaeden Young"
        />

        <!-- gradient effect img -->
        <div
          class="absolute bottom-0 left-0 w-full h-20 md:h-28 bg-gradient-to-b from-background/0 via-background/50 to-background rounded-lg"
        ></div>
      </div>

      <Carousel
        :opts="{ align: 'start', loop: true }"
        class="relative w-[80%] sm:w-[90%] lg:max-w-screen-xl mx-auto"
      >
        <CarouselContent class="-ml-4">
          <CarouselItem
            v-for="i in Array.from({ length: 5 }, (_, j) => j + 1)"
            :key="i"
            class="p-3 basis-1/3"
          >
            <Dialog>
              <DialogTrigger as-child>
                <Card class="h-full cursor-pointer">
                  <CardContent 
                    class="flex aspect-square justify-center p-4 rounded-lg shadow"
                    @click="selectedImage = `img${i}.jpg`"
                  >
                    <img 
                      :src="`img${i}.jpg`"
                      class="w-auto object-contain"
                      alt="Kaeden Young"
                    />
                  </CardContent>
                </Card>
              </DialogTrigger>

              <DialogContent
                class="fixed z-50 flex items-center justify-center bg-black/80 p-0 w-[100vw] bg-black/80 rounded-lg"
                @close="selectedImage = null"
              >
                <DialogTitle class="sr-only">Image Viewer</DialogTitle>
                <DialogDescription class="sr-only">
                  Enlarged view of image
                </DialogDescription>
                <img
                  v-if="selectedImage"
                  :src="selectedImage"
                  class="max-w-full max-h-full object-contain"
                  alt="Fullscreen"
                />
                <DialogClose
                  class="absolute top-4 right-4 text-white text-4xl font-bold"
                >
                </DialogClose>
              </DialogContent>

            </Dialog>

          </CarouselItem>
        </CarouselContent>
        <CarouselPrevious />
        <CarouselNext />
      </Carousel>

    </div>
  </section>
</template>

<style scoped>
.img-shadow-animation {
  animation-name: img-shadow-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

.img-border-animation {
  animation-name: img-border-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

@keyframes img-shadow-animation {
  from {
    opacity: 0.5;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0px);
  }
}
@keyframes img-border-animation {
  from {
    @apply border-t-primary/10;
  }

  to {
    @apply border-t-primary/60;
  }
}
</style>
