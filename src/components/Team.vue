<script setup lang="ts">
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
  CardFooter,
} from "@/components/ui/card";

import LinkedInIcon from "@/icons/LinkedInIcon.vue";
import GithubIcon from "@/icons/GithubIcon.vue";
import XIcon from "@/icons/XIcon.vue";

interface TeamProps {
  imageUrl: string;
  firstName: string;
  lastName: string;
  positions: string[];
  socialNetworks: SocialNetworkProps[];
}

interface SocialNetworkProps {
  name: string;
  url: string;
}

const teamList: TeamProps[] = [
  {
    imageUrl:
      "https://media.licdn.com/dms/image/v2/D5603AQErGIZ6iL7Ojg/profile-displayphoto-shrink_400_400/profile-displayphoto-shrink_400_400/0/1702656759738?e=1747267200&v=beta&t=LMJ6zvYfldIZAxSknFLWQqCy4oZR-Xfj7ZffIZbAIeg",
    firstName: "I. Kaan",
    lastName: "Yilmaz",
    positions: ["Full-stack Developer"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/ismet-kaan-yilmaz-809175245/",
      },
      {
        name: "Github",
        url: "https://github.com/kaandesu",
      },
    ],
  },
  {
    imageUrl: "ege.png",
    firstName: "Ege",
    lastName: "Onder",
    positions: ["Full-stack Developer"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/egeonder/",
      },
      {
        name: "Github",
        url: "https://github.com/egeonder",
      },
    ],
  },
  {
    imageUrl:
      "https://media.licdn.com/dms/image/v2/D4D03AQGQNjjEdAZO9w/profile-displayphoto-shrink_800_800/profile-displayphoto-shrink_800_800/0/1681513488909?e=1747267200&v=beta&t=TxjzMyP6aQ7xZlIdgAAkK3gmqALOIYXSJ2iGLB03uoM",
    firstName: "Deran",
    lastName: "Akin",
    positions: ["Computer Engineer", "Research & Presentation"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/deran-akin/",
      },
      {
        name: "Github",
        url: "https://github.com/der4ntula",
      },
    ],
  },
  {
    imageUrl: "atabay.png",
    firstName: "Taha Atabay",
    lastName: "Cetin",
    positions: ["AI Engineer"],
    socialNetworks: [
      {
        name: "LinkedIn",
        url: "https://www.linkedin.com/in/taha-atabay-cetin/",
      },
      {
        name: "Github",
        url: "https://github.com/atabaycetin",
      },
    ],
  },
  {
    imageUrl: "elio.jpg",
    firstName: "Elio",
    lastName: "Egidio",
    positions: ["Computer Engineer", "Research & Presentation"],
    socialNetworks: [
      {
        name: "Github",
        url: "https://github.com/ElioEgidio",
      },
    ],
  },
];

const socialIcon = (socialName: string) => {
  switch (socialName) {
    case "LinkedIn":
      return LinkedInIcon;

    case "Github":
      return GithubIcon;

    case "X":
      return XIcon;
  }
};
</script>

<template>
  <section id="team" class="container lg:w-[75%] py-24 sm:py-32">
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">Team</h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">The Dream Team</h2>
    </div>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8"
    >
      <Card
        v-for="{
          imageUrl,
          firstName,
          lastName,
          positions,
          socialNetworks,
        } in teamList"
        :key="imageUrl"
        class="bg-muted/60 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg"
      >
        <CardHeader class="p-0 gap-0">
          <div class="h-full overflow-hidden">
            <img
              :src="imageUrl"
              alt=""
              class="w-full aspect-square object-cover saturate-0 transition-all duration-200 ease-linear size-full group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-[1.01]"
            />
          </div>
          <CardTitle class="py-6 pb-4 px-6"
            >{{ firstName }}
            <span class="text-primary">{{ lastName }}</span>
          </CardTitle>
        </CardHeader>

        <CardContent
          v-for="(position, index) in positions"
          :key="index"
          :class="{
            'pb-0 text-muted-foreground ': true,
            'pb-4': index === positions.length - 1,
          }"
        >
          {{ position }}<span v-if="index < positions.length - 1">,</span>
        </CardContent>

        <CardFooter class="space-x-4 mt-auto">
          <a
            v-for="{ name, url } in socialNetworks"
            key="name"
            :href="url"
            target="_blank"
            class="hover:opacity-80 transition-all"
            :aria-label="`Visit our ${name} page`"
          >
            <component :is="socialIcon(name)" />
          </a>
        </CardFooter>
      </Card>
    </div>
  </section>
</template>
