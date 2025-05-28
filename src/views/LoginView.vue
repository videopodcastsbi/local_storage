<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const form = reactive({
    email: '',
    password: ''
});

const login = () => {
    const users = JSON.parse(localStorage.getItem('users')) || [];
    const foundUser = users.find(user => user.email === form.email && user.password === form.password);

    if (!foundUser) {
        alert('Invalid email or password');
        return;
    } else {
        alert('Login successful!');
        localStorage.setItem('currentUser', JSON.stringify(foundUser));

        form.email = '';
        form.password = '';
        router.push('/home');
    }
}
</script>

<template>
    <div class="bg-red-400 flex">
        <div class="w-1/2 bg-white h-screen flex justify-center items-center">
            <div class="w-[70%]">
                <h1 class="text-4xl font-bold">Login Page</h1>
                <p class="text-lg text-slate-400 mt-4">Welcome Back to my website</p>
                <form @submit.prevent="login" class="mt-6 flex flex-col gap-4">
                    <div class="flex flex-col gap-3">
                        <label for="emailaa" class="text-lg">Email:</label>
                        <input type="emailaa" id="emailaa"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-red-700 transition duration-200 shadow-md"
                            placeholder="Masukkan Email Anda" v-model="form.email">
                    </div>
                    <div class="flex flex-col gap-3">
                        <label for="password" class="text-lg">Password:</label>
                        <input type="password" id="password"
                            class="border-2 p-3 rounded-md focus:outline-none focus:ring focus:ring-red-700 transition duration-200 shadow-md"
                            placeholder="Masukkan Password Anda" v-model="form.password">
                    </div>
                    <div class="flex justify-between">
                        <div class="flex items-center gap-2">
                            <input type="checkbox" id="remember" class="border-2 p-4 rounded-md">
                            <label for="remember" class="text-lg text-slate-400">Remember Me</label>
                        </div>
                        <a href="#" class="text-lg text-blue-500">Forgot Password ?</a>
                    </div>
                    <button class="w-full bg-red-600 p-4 text-xl text-white font-bold rounded-md hover:bg-red-700"
                        type="submit">Submit</button>
                    <p class="text-lg text-center">Don't have an account? <a href="/register"
                            class="text-lg text-blue-500">Register
                            Now</a></p>
                </form>
            </div>
        </div>
        <div
            class="w-1/2 bg-[url('https://storage.devopsgeming.online/file-1736386796150.JPEG')] bg-cover bg-no-repeat">
        </div>
    </div>
</template>