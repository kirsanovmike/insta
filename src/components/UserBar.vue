<template>
<div>
  <h1>
    {{userName}}
  </h1>
  <ul>
    <li>
      Posts: {{userInfo.postsCount}}
    </li>
    <li>
      Followers: {{userInfo.followers}}
    </li>
    <li>
      Followings: {{userInfo.followings}}
    </li>
  </ul>
  <h1>
    Image gallery
  </h1>
  <image-gallery :posts="posts" />
</div>
</template>

<script setup lang="ts">
import ImageGallery from "@/components/ImageGallery.vue";

interface UserInfo {
  postsCount: number,
  followers: number,
  followings: number,
}

interface Image {
  id: number,
  image?: string
}

interface Props {
  userName: string,
  userInfo: UserInfo,
  posts?: Image[]
}

withDefaults(defineProps<Props>(), {
  userName: "UserName",
  posts: () => [],
  userInfo: () => ({
    postsCount: 0,
    followers: 0,
    followings: 0,
  }),
})
</script>
