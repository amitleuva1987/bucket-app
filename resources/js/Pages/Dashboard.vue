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
                <div
                    class="grid grid-cols-3 overflow-hidden shadow-sm sm:rounded-lg space-x-5"
                >
                    <div>
                        <h2 class="text-lg mb-2">Fruits</h2>
                        <draggable
                            class="list-group"
                            v-model="list1"
                            group="fruits"
                            itemKey="name"
                        >
                            <template #item="{ element }">
                                <div
                                    class="list-group-item bg-white p-2 border-b-2 cursor-move"
                                    :class="
                                        element.type == 'vegetable'
                                            ? 'bg-red-500 text-white'
                                            : ''
                                    "
                                >
                                    {{ element.name }}
                                    <span v-if="element.type == 'vegetable'">
                                        --> Placed in wrong bucket</span
                                    >
                                </div>
                            </template>
                        </draggable>
                    </div>
                    <div>
                        <h2 class="text-lg mb-2">Vegetables</h2>
                        <draggable
                            class="list-group"
                            :list="list2"
                            group="fruits"
                            itemKey="name"
                        >
                            <template #item="{ element }">
                                <div
                                    class="list-group-item bg-white p-2 border-b-2 cursor-move"
                                    :class="
                                        element.type == 'fruit'
                                            ? 'bg-red-500 text-white'
                                            : ''
                                    "
                                >
                                    {{ element.name }}
                                    <span v-if="element.type == 'fruit'">
                                        --> Placed in wrong bucket</span
                                    >
                                </div>
                            </template>
                        </draggable>
                    </div>
                    <div>
                        <h2 class="text-lg mb-2">Fruits & Vegetables</h2>
                        <draggable
                            class="list-group"
                            :list="list3"
                            group="fruits"
                            itemKey="name"
                        >
                            <template #item="{ element }">
                                <div
                                    class="list-group-item bg-white p-2 border-b-2 cursor-move"
                                >
                                    {{ element.name }}
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
            list1: [
                { name: "Apple", type: "fruit" },
                { name: "Pinaple", type: "fruit" },
                { name: "Orange", type: "fruit" },
                { name: "Kiwi", type: "fruit" },
                { name: "Mango", type: "fruit" },
            ],
            list2: [
                { name: "Spinach", type: "vegetable" },
                { name: "Okra", type: "vegetable" },
                { name: "Potato", type: "vegetable" },
            ],
            list3: [
                { name: "Banana", type: "fruit" },
                { name: "Cauliflower", type: "vegetable" },
                { name: "Grapes", type: "fruit" },
                { name: "Garlic", type: "vegetable" },
                { name: "Brocolli", type: "vegetable" },
                { name: "Tomato", type: "vegetable" },
            ],
        };
    },
};
</script>
