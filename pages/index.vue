<template>
    <div>
        <section class="h-screen bg-none grid place-content-center">
            <div class="max-w-3xl mx-auto text-center">
                <h1 class="text-5xl font-bold heading">Make your links tiny and easy to share with tnyl</h1>
                <p class="my-10 text-lg w-10/12 md:w-2/3 mx-auto">
                    Transform your long, cumbersome URLs into short and
                    shareable links with TinyLink
                </p>
                <nuxt-link :to="{ name: 'dashboard' }" class="btn btn-primary">
                    Short Now!
                </nuxt-link>
            </div>
        </section>
    </div>
</template>

<style scoped>
.heading {
    background: linear-gradient(180deg, #fff 0%, rgba(6, 255, 89, 0) 189%);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
</style>