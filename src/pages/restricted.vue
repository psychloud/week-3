<script setup lang="ts">
import { useAuthStore } from '@/stores/auth';
const auth = useAuthStore();
</script>

<template>
  <div v-if="auth.isLoggedIn()">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras sapien lorem, malesuada non pellentesque nec, aliquet quis augue. Proin ante tellus, ultricies quis ex et, tincidunt dignissim erat. Nullam tincidunt dui at lacus mollis, ac facilisis diam suscipit. Vestibulum imperdiet rhoncus nunc non facilisis. Ut dictum quis nulla quis vehicula. Nunc risus nibh, sagittis sed sapien a, sagittis euismod justo. Cras condimentum iaculis suscipit.</div>
  <div v-else>Anda harus login terlebih dahulu!</div>

</template>