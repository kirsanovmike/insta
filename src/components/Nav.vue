<template>
  <a-layout style="height: 100%; width: 100%">
    <a-layout-header class="header">
      <container flex>
        <router-link to="/" class="mr-2">Insta</router-link>
        <a-input-search
            v-model:value="searchStr"
            class="mr-2"
            placeholder="input search text"
            enter-button
            @search="onSearch"
        />
        <template v-if="!isAuth">
          <AuthModal :is-login="false" />
          <AuthModal :is-login="true" />
        </template>
        <template v-else>
          <a-button type="primary">Profile</a-button>
          <a-button type="primary">Logout</a-button>
        </template>
      </container>
    </a-layout-header>
    <a-layout-content style="padding: 0 50px">
      <a-breadcrumb style="margin: 16px 0">
        <a-breadcrumb-item>Home</a-breadcrumb-item>
        <a-breadcrumb-item>List</a-breadcrumb-item>
        <a-breadcrumb-item>App</a-breadcrumb-item>
      </a-breadcrumb>
      <a-layout style="padding: 24px 0; background: #fff">
        <a-layout-sider width="200" style="background: #fff">
          <a-menu
              v-model:selectedKeys="selectedKeys2"
              v-model:openKeys="openKeys"
              mode="inline"
              style="height: 100%"
          >
            <a-sub-menu key="sub1">
              <template #title>
                <span>
                  <user-outlined />
                  subnav 1
                </span>
              </template>
              <a-menu-item key="1">option1</a-menu-item>
              <a-menu-item key="2">option2</a-menu-item>
              <a-menu-item key="3">option3</a-menu-item>
              <a-menu-item key="4">option4</a-menu-item>
            </a-sub-menu>
            <a-sub-menu key="sub2">
              <template #title>
                <span>
                  <laptop-outlined />
                  subnav 2
                </span>
              </template>
              <a-menu-item key="5">option5</a-menu-item>
              <a-menu-item key="6">option6</a-menu-item>
              <a-menu-item key="7">option7</a-menu-item>
              <a-menu-item key="8">option8</a-menu-item>
            </a-sub-menu>
            <a-sub-menu key="sub3">
              <template #title>
                <span>
                  <notification-outlined />
                  subnav 3
                </span>
              </template>
              <a-menu-item key="9">option9</a-menu-item>
              <a-menu-item key="10">option10</a-menu-item>
              <a-menu-item key="11">option11</a-menu-item>
              <a-menu-item key="12">option12</a-menu-item>
            </a-sub-menu>
          </a-menu>
        </a-layout-sider>
        <a-layout-content :style="{ padding: '0 24px', minHeight: '280px', maxHeight: 'calc(100% - 180px)', }">
          <router-view />
        </a-layout-content>
      </a-layout>
    </a-layout-content>
    <a-layout-footer style="text-align: center">
      Insta© App by MMK
    </a-layout-footer>
  </a-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { UserOutlined, LaptopOutlined, NotificationOutlined } from '@ant-design/icons-vue';
import Container from "@/components/common/Container.vue";
import AuthModal from "@/components/AuthModal.vue";
import {useRouter} from "vue-router";

const selectedKeys2 = ref<string[]>(['1']);
const openKeys = ref<string[]>(['sub1']);
const searchStr = ref<string>('');

const isAuth = ref<boolean>(false);

const router = useRouter()

const onSearch = (searchValue: string) => {
  console.log(searchStr.value, searchValue)
  if (searchStr.value) {
    router.push(`/profile/${searchValue}`)
  }
};
</script>

<style scoped>
#components-layout-demo-top-side .logo {
  float: left;
  width: 120px;
  height: 31px;
  margin: 16px 24px 16px 0;
  background: rgba(255, 255, 255, 0.3);
}

.ant-row-rtl #components-layout-demo-top-side .logo {
  float: right;
  margin: 16px 0 16px 24px;
}

.site-layout-background {
  background: #fff;
}
</style>