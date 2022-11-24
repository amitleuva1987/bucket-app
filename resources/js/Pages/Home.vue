<script setup>
import { Head, Link } from "@inertiajs/inertia-vue3";
</script>

<template>
    <Head title="Welcome" />
    <GuestLayout>
        <div class="container my-24 px-6 mx-auto">
            <!-- Section: Design Block -->
            <section class="mb-32 text-center text-gray-800">
                <div class="max-w-[700px] mx-auto px-3 lg:px-6">
                    <h2 class="text-3xl font-bold mb-12">
                        Welcome to Bucket App. Please
                        <Link href="/login" class="text-blue-500">Sign In</Link>
                        or
                        <Link href="/register" class="text-blue-500"
                            >Register</Link
                        >
                        to use this app
                    </h2>
                </div>
            </section>
            <!-- Section: Design Block -->
        </div>
    </GuestLayout>
</template>
