<template>
    <div>
        <div class="card border-0 rounded shadow">
            <div class="card-body">
                <h4>Edit Post</h4>
                <hr />
                <form @submit.prevent="updatePost">
                    <div class="mb-3">
                        <label class="form-label">Judul Post</label>
                        <input
                            type="text"
                            class="form-control"
                            v-model="post.title"
                            placeholder="Masukkan Judul Post"
                        />
                        <div
                            v-if="errors.title"
                            class="mt-2 alert alert-danger"
                        >
                            {{ errors.title }}
                        </div>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Konten</label>
                        <textarea
                            class="form-control"
                            rows="5"
                            v-model="post.content"
                            placeholder="Masukkan Content Post"
                        ></textarea>
                        <div
                            v-if="errors.content"
                            class="mt-2 alert alert-danger"
                        >
                            {{ errors.content }}
                        </div>
                    </div>
                    <div class="mb-3">
                        <button
                            type="submit"
                            class="btn btn-primary btn-md shadow-sm me-2"
                        >
                            Update
                        </button>
                        <button
                            type="reset"
                            class="btn btn-warning btn-md shadow-sm"
                        >
                            Reset
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
//import layout
import LayoutApp from "../../Layouts/App.vue";

import { reactive } from "vue";
import { Inertia } from "@inertiajs/inertia";

export default {
    //layout
    layout: LayoutApp,

    //props
    props: {
        post: Object,
        errors: Object,
    },

    //define Composition Api
    setup(props) {
        //state posts
        const post = reactive({
            title: props.post.title,
            content: props.post.content,
        });

        //function updatePost
        function updatePost() {
            //define variable
            let title = post.title;
            let content = post.content;

            //send data
            Inertia.put(`/posts/${props.post.id}`, {
                title: title,
                content: content,
            });
        }

        return {
            post,
            updatePost,
        };
    },
};
</script>
