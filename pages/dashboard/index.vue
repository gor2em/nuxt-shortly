<script setup lang="ts">

definePageMeta({
    middleware: 'auth',
})

</script>

<template>
    <main class="pt-24">
        <section class="container">
            <h1 class="text-2xl font-bold text-white">Dashboard</h1>
        </section>
        <section class="container mt-10">
            <LinkForm />
        </section>
        <section class="container mt-10">
            <LinkItem v-for="i in 10" :key="i" :link="{
                shortKey: '/1qadS9',
                longUrl: 'http://google.com',
                id: '1'
            }" class="mb-5" />
        </section>
    </main>
</template>
