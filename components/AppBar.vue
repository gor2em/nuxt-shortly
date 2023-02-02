<script setup lang="ts">

const navLinks = ref<{
    to: string,
    label: string,
}[]>([
    {
        to: '/',
        label: 'Home'
    },
    {
        to: '/about',
        label: 'About'
    },
    {
        to: '/contact',
        label: 'Contact'
    }
])

</script>

<template>
    <div class="fixed top-0 left-0 right-0 border-b border-white/20 bg-blur">
        <nav class="container py-4 flex justify-between">
            <nuxt-link :to="{ name: 'index' }" class="text-2xl font-bold text-white">
                shortly
            </nuxt-link>
            <ul class="flex items-center space-x-4">
                <li v-for="link in navLinks" :key="link.to">
                    <nuxt-link :to="link.to">
                        {{ link.label }}
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link :to="{ name: 'auth' }" class="btn btn-primary">Sign In</nuxt-link>
                </li>
            </ul>
        </nav>
    </div>
</template>
<style scoped>

</style>