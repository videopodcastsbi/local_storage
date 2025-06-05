<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()
const logout = () => {
  localStorage.removeItem('loggedInUser')
  router.push('/')
}
</script>

<template>
  <div class="font-bold flex flex-col items-center justify-center h-screen">
    <h1>Halaman Home</h1>
    <button @click="logout"
      class="w-[100px] bg-red-600 p-4 text-xl text-white font-bold rounded-md hover:bg-red-700">Logout</button>
  </div>
</template>

