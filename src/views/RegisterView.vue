<script setup>
import { reactive } from 'vue';
import { useRouter } from 'vue-router'

const router = useRouter()
const form = reactive({
    name: '',
    email: '',
    password: '',
    confirmPassword: ''
});

const register = () => {
    const users = JSON.parse(localStorage.getItem('users')) || [];
    users.push({
        name: form.name,
        email: form.email,
        password: form.password
    });

    localStorage.setItem('users', JSON.stringify(users));

    alert('Registration successful!');

    form.name = '';
    form.email = '';
    form.password = '';
    form.confirmPassword = '';
    router.push('/');
};
</script>

<template>
    <div class="bg-blue-400 flex">
        <div class="w-1/2 bg-white h-screen flex justify-center items-center">
            <div class="w-[70%]">
                <h1 class="text-4xl font-bold">Register Page</h1>
                <p class="text-lg text-slate-400 mt-4">Create your account</p>
                <form @submit.prevent="register" class="mt-6 flex flex-col gap-4">
                    <div class="flex flex-col gap-3">
                        <label for="name" class="text-lg">Name:</label>
                        <input type="text" id="name"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-blue-700 transition duration-200 shadow-md"
                            placeholder="Masukkan Nama Anda" v-model="form.name">
                    </div>
                    <div class="flex flex-col gap-3">
                        <label for="email" class="text-lg">Email:</label>
                        <input type="email" id="email"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-blue-700 transition duration-200 shadow-md"
                            placeholder="Masukkan Email Anda" v-model="form.email">
                    </div>
                    <div class="flex flex-col gap-3">
                        <label for="password" class="text-lg">Password:</label>
                        <input type="password" id="password"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-blue-700 transition duration-200 shadow-md"
                            placeholder="Masukkan Password Anda" v-model="form.password">
                    </div>
                    <div class="flex flex-col gap-3">
                        <label for="confirm-password" class="text-lg">Confirm Password:</label>
                        <input type="password" id="confirm-password"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-blue-700 transition duration-200 shadow-md"
                            placeholder="Konfirmasi Password Anda" v-model="form.confirmPassword">
                    </div>
                    <button class="w-full bg-red-600 p-4 text-xl text-white font-bold rounded-md hover:bg-red-700"
                        type="submit">Submit</button>
                    <p class="text-lg text-center">Already have an account? <a href="/"
                            class="text-lg text-blue-500">Login
                            Here</a></p>
                </form>
            </div>
        </div>
        <div
            class="w-1/2 bg-[url('https://storage.devopsgeming.online/file-1736386796150.JPEG')] bg-cover bg-no-repeat">
        </div>
    </div>
</template>