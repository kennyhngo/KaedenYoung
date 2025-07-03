<script setup lang="ts">
import { ref, reactive } from "vue";
import { Button } from "./ui/button";
import { Card, CardHeader, CardContent, CardFooter } from "./ui/card";
import { Label } from "./ui/label";
import { Input } from "./ui/input";
import {
  Select,
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "./ui/select";
import { Textarea } from "./ui/textarea";
import { Alert, AlertDescription, AlertTitle } from "@/components/ui/alert";

import { AlertCircle, Building2, Phone, Mail, Clock } from "lucide-vue-next";
import { toast } from "vue-sonner";

interface ContactFormeProps {
  firstName: string;
  lastName: string;
  email: string;
  message: string;
}

const contactForm = reactive<ContactFormeProps>({
  firstName: "",
  lastName: "",
  email: "",
  message: "",
});

const invalidInputForm = ref<boolean>(false);

const handleSubmit = async () => {
  const { firstName, lastName, email, message } = contactForm;
  if (!firstName || !lastName || !email || !message) {
    invalidInputForm.value = true;
    toast.error("Please fill in all fields correctly.");
    return;
  }
  invalidInputForm.value = false;

  fetch("https://formsubmit.co/ajax/fcf6a021d59596218fa38bc27dfcea3c", {
      method: "POST",
      headers: { 
        "Content-Type": "application/json",
        "Accept": "application/json",
       },
      body: JSON.stringify({
        name: `${firstName} ${lastName}`,
        email,
        message,
        _subject: "New Pickleball Inquiry",
        _template: "box",
        _cc: "kennyngodev@gmail.com",
        _captcha: true,
      }),
    })
      .then((res) => res.json().then((data) => ({ status: res.status, data})))
      .then(({ status, data}) => {
        if (status !== 200) {
          console.error("FormSubmit error", data);
          toast.error("Failed to send message. Please try again.")
          return;
        }
        toast.success("Message sent! We'll get back to you soon.");
        Object.assign(contactForm, {
          firstName: "",
          lastName: "",
          email: "",
          message: "",
        });
      })
      .catch((err) => {
        console.error("Network or server error: ", err);
        toast.error("Something went wrong. Please try again later.");
      });
};
</script>

<template>
  <section
    id="contact"
    class="container py-24 sm:py-32"
  >
    <!-- <section class="grid grid-cols-1 md:grid-cols-2 gap-8"> -->
    <section class="grid grid-cols-1 md:grid-cols-1 gap-8">
      <div>
        <div class="mb-4">
          <h2 class="text-lg text-primary mb-2 tracking-wider">Contact</h2>
          <h2 class="text-3xl md:text-4xl font-bold">Get in touch</h2>
        </div>
        <!-- <p class="mb-8 text-muted-foreground lg:w-5/6">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum
          ipsam sint enim exercitationem ex autem corrupti quas tenetur
        </p> -->

        <!-- <div class="flex flex-col gap-4">
          <div>
            <div class="flex gap-2 mb-1">
              <Building2 />
              <div class="font-bold">Find Us</div>
            </div>

            <div>742 Evergreen Terrace, Springfield, IL 62704</div>
          </div>

          <div>
            <div class="flex gap-2 mb-1">
              <Phone />
              <div class="font-bold">Call Us</div>
            </div>

            <div>+1 (619) 123-4567</div>
          </div>

          <div>
            <div class="flex gap-2 mb-1">
              <Mail />
              <div class="font-bold">Mail Us</div>
            </div>

            <div>leomirandadev@gmail.com</div>
          </div>

          <div>
            <div class="flex gap-2">
              <Clock />
              <div class="font-bold">Visit Us</div>
            </div>

            <div>
              <div>Monday - Friday</div>
              <div>8AM - 4PM</div>
            </div>
          </div>
        </div> -->
      </div>

      <!-- form -->
      <Card class="bg-muted/60 dark:bg-card">
        <CardHeader class="text-primary text-2xl"> </CardHeader>
        <CardContent>
          <form
            @submit.prevent="handleSubmit"
            class="grid gap-4"
          >
            <div class="flex flex-col md:flex-row gap-8">
              <div class="flex flex-col w-full gap-1.5">
                <Label for="first-name">First Name</Label>
                <Input
                  id="first-name"
                  type="text"
                  placeholder=""
                  v-model="contactForm.firstName"
                />
              </div>

              <div class="flex flex-col w-full gap-1.5">
                <Label for="last-name">Last Name</Label>
                <Input
                  id="last-name"
                  type="text"
                  placeholder=""
                  v-model="contactForm.lastName"
                />
              </div>
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="email">Email</Label>
              <Input
                id="email"
                type="email"
                placeholder=""
                v-model="contactForm.email"
              />
            </div>

            <!-- <div class="flex flex-col gap-1.5">
              <Label for="subject">Subject</Label>

              <Select v-model="contactForm.subject">
                <SelectTrigger>
                  <SelectValue placeholder="Select a subject" />
                </SelectTrigger>
                <SelectContent>
                  <SelectGroup>
                    <SelectItem value="Web Development">
                      Web Development
                    </SelectItem>
                    <SelectItem value="Mobile Development">
                      Mobile Development
                    </SelectItem>
                    <SelectItem value="Figma Design"> Figma Design </SelectItem>
                    <SelectItem value="REST API "> REST API </SelectItem>
                    <SelectItem value="FullStack Project">
                      FullStack Project
                    </SelectItem>
                  </SelectGroup>
                </SelectContent>
              </Select>
            </div> -->

            <div class="flex flex-col gap-1.5">
              <Label for="message">Message</Label>
              <Textarea
                id="message"
                placeholder="Message"
                rows="5"
                v-model="contactForm.message"
              />
            </div>

            <Alert
              v-if="invalidInputForm"
              variant="destructive"
            >
              <AlertCircle class="w-4 h-4" />
              <AlertTitle>Error</AlertTitle>
              <AlertDescription>
                There is an error in the form. Please check your input.
              </AlertDescription>
            </Alert>

            <Button class="mt-4">Send message</Button>
          </form>
        </CardContent>

        <CardFooter></CardFooter>
      </Card>
    </section>
  </section>
</template>
