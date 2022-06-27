<script setup>
import AppLayout from "@/Layouts/AppLayout.vue";
import { Link } from '@inertiajs/inertia-vue3';

defineProps({
    notes: Array,
});
</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notes module
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="p3-4 sm:px0">
                            <h3 class="text-lg text-gray-900">List</h3>
                            <p class="text-sm text-gray-600">
                                Select any option (see, edit, remove)
                            </p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <table>
                                <tr v-for="(note, index) in notes" :key="index">
                                    <td class="border px-4 py-2">
                                        {{ note.excerpt }}
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.show', note)">
                                            See
                                        </Link>
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.edit', note)">
                                            Edit
                                        </Link>
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.destroy', note)">
                                            Remove
                                        </Link>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
