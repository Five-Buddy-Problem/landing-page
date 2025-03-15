<script setup lang="ts">
import {
  Card,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import { Badge } from "@/components/ui/badge";

enum ProService {
  YES = 1,
  NO = 0,
}

interface ServiceProps {
  title: string;
  pro: ProService;
  description: string;
}

const serviceList: ServiceProps[] = [
  {
    title: "Custom Domain Integration",
    description:
      "Integrate your custom domain seamlessly to access your agricultural insights directly through your own branded platform.",
    pro: 0,
  },
  {
    title: "Drone Integration",
    description:
      "Leverage AI-assisted drones for real-time pest detection, field monitoring, and automated scanning. Drones are fully integrated with the platform, providing efficient and solar-powered solutions for high-priority agricultural areas.",
    pro: 1,
  },
  {
    title: "AI Model Integration",
    description:
      "Enable the integration of custom AI models for tailored insights, allowing you to enhance your platform with specific agricultural analytics.",
    pro: 0,
  },
  {
    title: "Blockchain Integration",
    description:
      "Integrate blockchain technology for secure, immutable data verification and provenance tracking across all your agricultural data.",
    pro: 1,
  },
];
</script>

<template>
  <section id="services" class="container py-24 sm:py-32">
    <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
      Services
    </h2>

    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Elevate Your Agricultural Operations
    </h2>
    <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      Our platform empowers farmers, governments, and agricultural companies
      with cutting-edge tools, AI-driven insights, and secure blockchain
      technology for smarter, sustainable agricultural practices.
    </h3>
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4"></div>

    <div
      class="grid sm:grid-cols-2 lg:grid-cols-2 gap-4 w-full lg:w-[60%] mx-auto"
    >
      <div v-for="{ title, description, pro } in serviceList" :key="title">
        <Card class="bg-muted/60 dark:bg-card h-full relative">
          <CardHeader>
            <CardTitle>{{ title }}</CardTitle>
            <CardDescription>{{ description }}</CardDescription>
          </CardHeader>
          <Badge
            v-if="pro === ProService.YES"
            variant="secondary"
            class="absolute -top-2 -right-3"
            >PRO</Badge
          >
        </Card>
      </div>
    </div>
  </section>
</template>
