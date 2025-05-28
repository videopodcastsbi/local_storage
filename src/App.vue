<script setup>
import { RouterView } from 'vue-router'
import { useRouter } from 'vue-router'
import { onMounted } from 'vue'

const router = useRouter()
onMounted(() => {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (currentUser) {
    router.push('/home');
  }
});
</script>

<template>
  <RouterView />
</template>

<style scoped>
* {
  font-family: 'Poppins', 'sans-serif';
}
</style>
