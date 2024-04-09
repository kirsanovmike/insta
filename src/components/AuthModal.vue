<template>
  <div>
    <a-button type="primary" @click="showModal">{{ isLogin ? "Login" : "Signup" }}</a-button>
    <a-modal v-model:open="open" :title="isLogin ? 'Login' : 'Signup'" @ok="handleOk">
    <a-input v-if="!isLogin" v-model:value="value" placeholder="Username" />
    <a-input v-model:value="value" placeholder="Email" />
    <a-input v-model:value="value" placeholder="Password" />
    </a-modal>
  </div>
</template>
<script lang="ts" setup>
import { ref } from 'vue';

defineProps<{isLogin: boolean}>()

const open = ref<boolean>(false);
const value = ref<string>("")

const showModal = () => {
  open.value = true;
};

const handleOk = () => {
  open.value = false;
};
</script>