<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

interface HowItWorksProps {
  badgeTitle: string;
  title: string;
  description: string;
  image: string;
}

const HowItWorksList: HowItWorksProps[] = [
  {
    badgeTitle: "Log In",
    title: "Access Your Agricultural Insights",
    description:
      "Easily log in to the platform using secure authentication methods and gain access to the full suite of agricultural data and tools.",
    image: "login-icon.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Define Area",
    title: "Select Your Area of Interest",
    description:
      "Define your area of interest by uploading GeoJSON files or selecting your region on the Cesium.js map for accurate, targeted data collection.",
    image: "map-selection.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Select Insights",
    title: "Choose the Insights You Want to Monitor",
    description:
      "Select key insights like pest infestations, drought risks, or crop health to monitor, customized to the needs of your agricultural operation.",
    image: "insights-selection.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Initiate Data Collection",
    title: "Collect Data via Satellites and Drones",
    description:
      "Trigger data collection from Sentinel-2 satellites or drone hubs, ensuring real-time and precise monitoring of your land and crops.",
    image: "data-collection.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Process with AI",
    title: "AI-Driven Data Analysis",
    description:
      "Let our AI models process and analyze the collected data, identifying key agricultural risks and providing valuable insights for decision-making.",
    image: "ai-analysis.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Visualize & Compare",
    title: "Compare Insights and View Results",
    description:
      "Compare the collected data against historical trends, and view it through interactive 3D visualizations on the platform's dashboard.",
    image: "visualize-results.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Store & Secure",
    title: "Store Results on Blockchain",
    description:
      "Ensure the integrity and authenticity of your data by securely storing the results on the platform's blockchain for transparent and verifiable records.",
    image: "blockchain-security.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Generate Reports",
    title: "Get Detailed Reports",
    description:
      "Generate comprehensive reports on pest infestations, drought risks, and crop health, with options for downloading or integrating via API for enterprise use.",
    image: "generate-reports.png", // Replace with a relevant image
  },
  {
    badgeTitle: "Monitor Continuously",
    title: "Continuous Monitoring and Updates",
    description:
      "Stay informed with continuous monitoring and automatic updates, ensuring you always have the latest insights at your fingertips.",
    image: "continuous-monitoring.png", // Replace with a relevant image
  },
];
</script>

<template>
  <section id="features" class="container py-24 sm:py-32">
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
        How It Works
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Step-by-Step Process
      </h2>
    </div>

    <div class="lg:w-[80%] mx-auto relative">
      <div
        v-for="(
          { badgeTitle, title, description, image }, index
        ) in HowItWorksList"
        :key="title"
        :class="[
          'flex mb-8 items-center',
          { ' flex-row-reverse': index % 2 !== 0 },
        ]"
      >
        <Card class="h-full bg-transparent border-0 shadow-none">
          <CardHeader>
            <div class="pb-4">
              <Badge>{{ badgeTitle }}</Badge>
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground w-[80%]">
            {{ description }}
          </CardContent>
        </Card>

        <img
          :src="image"
          :alt="`Image describing ${title}`"
          className="w-[100px] md:w-[200px] lg:w-[200px] mx-auto -scale-x-100 
             dark:invert dark:contrast-100"
        />
        <div
          :class="[
            '-z-10 absolute right-0 w-44 h-72  lg:w-64 lg:h-80 rounded-full bg-primary/15 dark:bg-primary/10 blur-3xl',
            {
              'left-0': index % 2 !== 0,
            },
          ]"
        ></div>
      </div>
    </div>
  </section>
</template>
