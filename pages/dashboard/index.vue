<script setup lang="ts">

</script>
<template>
    <main class="pt-24">
        <section class="container">
            <h1 class="text-2xl font-bold text-white">Dashboard</h1>
        </section>
        <section class="container mt-10">
            <div class="card">
                <form>
                    <div class="flex items-end gap-5">
                        <div class="w-5/12">
                            <label for="url" class="text-white">Long URL</label>
                            <input type="text" id="url" />
                        </div>
                        <div class="w-5/12">
                            <label for="shortKey" class="text-white">Short Key</label>
                            <input type="text" id="shortKey" />
                        </div>
                        <div class="w-2/12">
                            <button class="w-full btn-primary rounded-lg py-3">Short</button>
                        </div>
                    </div>
                </form>
            </div>
        </section>
        <section></section>
    </main>
</template>
