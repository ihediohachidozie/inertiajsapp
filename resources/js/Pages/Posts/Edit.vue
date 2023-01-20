<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link, useForm } from '@inertiajs/vue3';

const props = defineProps({
    post: Object,
    errors: Object,
});
/**
 * const form = useForm({
    id: props.post.id,
    title: props.post.title,
    description: props.post.description
    })

 */
const form = useForm(props.post)


</script>



<template>
    <AppLayout title="Create Posts">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Edit Posts
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">

                    <div class="block p-6 rounded-lg shadow-lg bg-white">
                        <form @submit.prevent="form.put(route('posts.update', form.id))">
                            <div class="form-group mb-6">
                                <input v-model="form.title" type="text"
                                    class="form-control block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                                    id="exampleInput7" placeholder="Title">
                                    <div v-if="errors.title" class="text-red-600">
                                        {{ errors.title }}
                                    </div>
                            </div>

                            <div class="form-group mb-6">
                                <textarea v-model="form.description"
                                    class="form-control block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none "
                                    id="exampleFormControlTextarea13" rows="3" placeholder="Description"></textarea>
                                   <div v-if="errors.description" class="text-red-600">
                                        {{ errors.description }}
                                    </div>
                            </div>
                            <button type="submit" :disabled="form.processing"
                                class="px-6 py-2.5 bg-blue-600 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out">
                                Save Post
                            </button>
                            <Link :href="route('posts.index')"
                                class="px-6 py-2.5 ml-3 bg-gray-200 text-black font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-gray-400 hover:shadow-lg focus:bg-gray-400 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-gray-400 active:shadow-lg transition duration-150 ease-in-out">
                            Cancel
                            </Link>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
