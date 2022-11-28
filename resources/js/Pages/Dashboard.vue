<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head } from "@inertiajs/inertia-vue3";
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <p class="text-center text-red-600">{{ error }}</p>
                <div
                    class="grid grid-cols-3 overflow-hidden shadow-sm sm:rounded-lg space-x-5"
                >
                    <div v-for="bucket in data" :key="bucket.bucket">
                        <h2 class="text-lg mb-2">{{ bucket.bucket }}</h2>
                        <draggable
                            :class="bucket.bucket"
                            :list="bucket.values"
                            group="fruits"
                            itemKey="name"
                            :move="checkElement"
                        >
                            <template #item="{ element }">
                                <div
                                    class="list-group-item bg-white p-2 border-b-2 cursor-move"
                                    :class="
                                        element.type == 'vegetable' &&
                                        bucket.bucket == 'fruit'
                                            ? 'bg-red-500 text-white'
                                            : ''
                                    "
                                >
                                    {{ element.name }}
                                    <span
                                        v-if="
                                            element.type == 'vegetable' &&
                                            bucket.bucket == 'fruit'
                                        "
                                    >
                                        Placed in wrong bucket</span
                                    >
                                </div>
                            </template>
                        </draggable>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script>
import draggable from "vuedraggable";
export default {
    components: {
        draggable,
    },
    data() {
        return {
            error: "",
            data: [
                {
                    bucket: "fruit",
                    values: [
                        {
                            id: 1,
                            name: "Apple",
                            type: "fruit",
                            bucket: "fruit",
                        },
                        {
                            id: 2,
                            name: "Pinaple",
                            type: "fruit",
                            bucket: "fruit",
                        },
                        {
                            id: 3,
                            name: "Orange",
                            type: "fruit",
                            bucket: "fruit",
                        },
                        { id: 4, name: "Kiwi", type: "fruit", bucket: "fruit" },
                        {
                            id: 5,
                            name: "Mango",
                            type: "fruit",
                            bucket: "fruit",
                        },
                    ],
                },
                {
                    bucket: "vegetable",
                    values: [
                        {
                            id: 6,
                            name: "Spinach",
                            type: "vegetable",
                            bucket: "vegetable",
                        },
                        {
                            id: 7,
                            name: "Okra",
                            type: "vegetable",
                            bucket: "vegetable",
                        },
                        {
                            id: 8,
                            name: "Potato",
                            type: "vegetable",
                            bucket: "vegetable",
                        },
                    ],
                },
                {
                    bucket: "common",
                    values: [
                        { name: "Banana", type: "fruit" },
                        { name: "Cauliflower", type: "vegetable" },
                        { name: "Grapes", type: "fruit" },
                        { name: "Garlic", type: "vegetable" },
                        { name: "Brocolli", type: "vegetable" },
                        { name: "Tomato", type: "vegetable" },
                    ],
                },
            ],
        };
    },
    methods: {
        checkElement: function (evt) {
            if (
                evt.to.classList.contains("vegetable") == true &&
                evt.draggedContext.element.type == "fruit"
            ) {
                this.error = "You choose wrong bucket";
                setTimeout(() => (this.error = ""), 3000);
                return false;
            }

            if (
                evt.to.classList.contains("fruit-group") == true &&
                evt.draggedContext.element.type == "vegetable"
            ) {
                this.error = "You choose wrong bucket";
                setTimeout(() => (this.error = ""), 3000);
                return false;
            }

            return true;
            // console.log(evt.moved.element);
        },
        checkNewElement: function (item) {
            // console.log(item);
        },
    },
};
</script>
