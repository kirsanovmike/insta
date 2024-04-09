<template>
  <container>
    <user-bar :user-info="userInfo" :user-name="userName" :posts="posts" />
  </container>
</template>

<script setup lang="ts">
import Card from "@/components/Card.vue";
import Container from "@/components/common/Container.vue";
import UserBar from "@/components/UserBar.vue";

interface UserInfo {
  postsCount: number,
  followers: number,
  followings: number,
}

const userInfo: UserInfo = {
  followers: 555,
  followings: 345,
  postsCount: 123
}

interface Image {
  id: number,
  image?: string
}

const userName: string = "Mike Kirsanov";

const posts: Image[] = [
  {
    id: 1,
    image: "https://cdn.pixabay.com/photo/2024/03/13/19/06/ai-generated-8631634_1280.jpg",
  },
  {
    id: 2,
    image: "https://cdn.pixabay.com/photo/2024/03/13/19/06/ai-generated-8631634_1280.jpg",
  },
  {
    id: 3,
    image: "https://cdn.pixabay.com/photo/2024/03/13/19/06/ai-generated-8631634_1280.jpg",
  },
];
</script>
