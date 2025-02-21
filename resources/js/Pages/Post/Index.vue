<template>
    <div class="mt-5">
        <!-- flash message -->
        <div
            v-if="$page.props.flash.message"
            class="alert alert-success"
            role="alert"
        >
            {{ $page.props.flash.message }}
        </div>
        <!-- flash message -->
        <div class="mb-3">
            <inertia-link href="/posts/create" class="btn btn-md btn-primary"
                >Tambah</inertia-link
            >
        </div>
        <div class="card border-0 rounded shadow-sm">
            <div class="card-body">
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">Judul</th>
                            <th scope="col">Konten</th>
                            <th scope="col">Aksi</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="post in posts" :key="post.id">
                            <td>{{ post.title }}</td>
                            <td>{{ post.content }}</td>
                            <td class="text-center">
                                <inertia-link
                                    :href="`/posts/${post.id}/edit`"
                                    class="btn btn-sm btn-primary me-2"
                                    >Edit</inertia-link
                                >
                                <button
                                    @click.prevent="deletePost(`${post.id}`)"
                                    class="btn btn-sm btn-danger"
                                >
                                    Hapus
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
//import layout
import LayoutApp from "../../Layouts/App.vue";

//import Link dari inertia
import { Link } from "@inertiajs/inertia-vue3";

import { Inertia } from "@inertiajs/inertia";

export default {
    //layout
    layout: LayoutApp,

    //register Link di component
    components: {
        "inertia-link": Link,
    },

    //props
    props: {
        posts: Array, // <- nama props yang dibuat di controller saat parsing data
    },

    //define Composition Api
    setup() {
        //method deletePost
        function deletePost(id) {
            Inertia.delete(`/posts/${id}`);
        }

        return {
            deletePost,
        };
    },
};
</script>

<style></style>
