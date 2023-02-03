<script setup lang="ts">

const supabaseAuth = useSupabaseAuthClient();
const handleGithubLogin = () => {
    supabaseAuth.auth.signInWithOAuth({
        provider: 'github',
    });
}

const isLoggingIn = ref<boolean>(true);
const errors = ref<string>("")

const form = reactive({
    email: "",
    password: ""
});


const handleSignup = async () => {
    try {
        const { data, error } = await supabaseAuth.auth.signUp({
            email: form.email,
            password: form.password
        });

        if (error) {
            errors.value = error.message;
            return;
        }

        console.log(data)
    } catch (error) {

        errors.value = "Something went wrong."
    }
}

const handleLoginForm = async () => {
    if (!form.email || !form.password) {
        errors.value = "please fill all the fields"
        return;
    }

    if (!isLoggingIn.value) {
        return handleSignup();
    }

    try {
        const { data, error } = await supabaseAuth.auth.signInWithPassword({
            email: form.email,
            password: form.password
        });

        if (error) {
            errors.value = error.message;
            return;
        }

        console.log(data)
    } catch (error) {

        errors.value = "Something went wrong."
    }
}
</script>
<template>

    <section class="h-screen grid place-content-center">
        <div class="container">

            <!-- Card -->
            <div class="card">
                <div class="flex items-center justify-center">

                    <div class="flex justify-center items-center w-20 h-20 rounded-full border shadow-xl">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                            stroke="currentColor" class="w-8 h-8">
                            <path stroke-linecap="round" stroke-linejoin="round"
                                d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
                        </svg>

                    </div>
                </div>

                <button class="btn btn-primary w-full mt-5" @click="handleGithubLogin">
                    Continue with Github
                </button>


                <hr class="border border-white/10 my-8">

                <form @submit.prevent="handleLoginForm">
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input v-model="form.email" type="email" name="email" id="email" placeholder="john@doe.com">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input v-model="form.password" type="password" name="password" id="password"
                            placeholder="*******">
                    </div>

                    <template v-if="isLoggingIn">
                        <button type="submit" class="btn btn-primary w-full mt-5">Login</button>
                    </template>
                    <template v-else>
                        <button type="submit" class="btn btn-primary w-full mt-5">Signup</button>
                    </template>

                    <div class="text-center">
                        <button class="mt-5" @click.prevent="isLoggingIn = !isLoggingIn">
                            <template v-if="isLoggingIn">
                                Don't have an account? Signup
                            </template>
                            <template v-else>
                                Already have an account? Login
                            </template>
                        </button>
                    </div>

                    <div class="text-red-500 text-center mt-5">
                        {{ errors }}
                    </div>
                </form>

            </div>
            <!--./Card -->
        </div>
    </section>

</template>
<style scoped>

</style>