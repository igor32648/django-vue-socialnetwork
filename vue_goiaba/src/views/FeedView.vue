<template>
    <div class="max-w-6xl mx-auto grid grid-cols-4 gap-4">
        <div class="main-center col-span-3 space-y-4">
            <div class="bg-white border border-gray-200 rounded-lg">
                <FeedForm 
                    v-bind:user="null" 
                    v-bind:posts="posts"
                />
            </div>

            <div 
                class="p-4 bg-white border border-gray-200 rounded-lg"
                v-for="post in posts"
                v-bind:key="post.id"
            >
                <FeedItem v-bind:post="post" v-on:deletePost="deletePost" />
            </div>
        </div>

        <div class="main-right col-span-1 space-y-4">
            <PeopleYouMayKnow />

            <Trends />
        </div>
    </div>
</template>

<style>
input[type="file"] {
    display: none;
}

.custom-file-upload {
    border: 1px solid #ccc;
    display: inline-block;
    padding: 6px 12px;
    cursor: pointer;
}
</style>

<script>
import axios from 'axios'
import PeopleYouMayKnow from '../components/PeopleYouMayKnow.vue'
import Trends from '../components/Trends.vue'
import FeedItem from '../components/FeedItem.vue'
import FeedForm from '../components/FeedForm.vue'

export default {
    name: 'FeedView',

    components: {
        PeopleYouMayKnow,
        Trends,
        FeedItem, 
        FeedForm
    },

    data() {
        return {
            posts: [],
            body: '',
        }
    },

    mounted() {
        this.getFeed()
    },

    methods: {
        getFeed() {
            axios
                .get('/api/posts/')
                .then(response => {
                    console.log('data', response.data)

                    this.posts = response.data
                })
                .catch(error => {
                    console.log('error', error)
                })
        },
        
        deletePost(id) {
            this.posts = this.posts.filter(post => post.id !== id)
        },


        submitForm() {
            console.log('submitForm', this.body)

            axios
                .post('/api/posts/create/', {
                    'body': this.body
                })
                .then(response => {
                    console.log('data', response.data)

                    this.posts.unshift(response.data)
                    this.body = ''
                })
                .catch(error => {
                    console.log('error', error)
                })
        }
    }
}
</script>