<template>
    <div class="max-w-7xl mx-auto grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
        <div class="main-left sm:col-span-1 md:col-span-1">
            <div class="p-4 bg-white border border-gray-200 text-center rounded-lg">
                <img :src="user.get_avatar" class="mb-6 rounded-full w-full h-full object-cover">
                
                <p><strong>{{ user.name }}</strong></p>

                <div class="mt-6 flex space-x-8 justify-around" v-if="user.id">
                    <RouterLink :to="{name: 'friends', params: {id: user.id}}" class="text-xs text-gray-500">{{ user.friends_count }} friends</RouterLink>
                    <p class="text-xs text-gray-500">{{ user.posts_count }} posts</p>
                </div>
                <div class="mt-6">
                    <button 
                        class="inline-block py-4 px-3 mr-2 bg-pink-600 text-xs text-white" 
                        @click="sendFriendshipRequest"
                        v-if="userStore.user.id !== user.id && can_send_friendship_request"
                    >
                        Add friend
                    </button>

                    <button 
                        class="inline-block mt-4 py-4 px-3 bg-pink-500 text-xs text-white" 
                        @click="sendDirectMessage"
                        v-if="userStore.user.id !== user.id"
                    >
                        Message
                    </button>

                    <RouterLink 
                        class="inline-block mr-2 py-4 px-3 bg-pink-500 text-xs text-white" 
                        to="/profile/edit"
                        v-if="userStore.user.id === user.id"
                    >
                        Edit profile
                    </RouterLink>

                    <button 
                        class="inline-block py-4 px-3 bg-red-600 text-xs text-white" 
                        @click="logout"
                        v-if="userStore.user.id === user.id"
                    >
                        Log out
                    </button>
                </div>
            </div>
        </div>
        <div class="main-center sm:col-span-2 md:col-span-2 space-y-4">
            <div 
                class="bg-white border border-gray-200 rounded-lg"
                v-if="userStore.user.id === user.id"
            >
                <FeedForm 
                    v-bind:user="user"
                    v-bind:posts="posts"
                />
            </div>

            <div 
                class="p-4 bg-white border border-gray-200 rounded-lg"
                v-for="post in posts"
                v-bind:key="post.id"
            >
                <FeedItem v-bind:post="post"  v-on:deletePost="deletePost"/>
            </div>
        </div>

        <div class="main-right sm:col-span-1 md:col-span-1 space-y-4">
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
import { useUserStore } from '@/stores/user'
import { useToastStore } from '@/stores/toast'

export default {
    name: 'ProfileView',

    setup() {
        const userStore = useUserStore()
        const toastStore = useToastStore()

        return {
            userStore,
            toastStore
        }
    },

    components: {
        PeopleYouMayKnow,
        Trends,
        FeedItem,
        FeedForm
    },

    data() {
        return {
            posts: [],
            user: {
                id: ''
            },
            can_send_friendship_request: null,
            body: '',
            url: null,
        }
    },

    mounted() {
        this.getFeed()
    },

    watch: { 
        '$route.params.id': {
            handler: function() {
                this.getFeed()
            },
            deep: true,
            immediate: true
        }
    },

    methods: {
        deletePost(id) {
            this.posts = this.posts.filter(post => post.id !== id)
        },
        
        sendDirectMessage() {
            console.log('sendDirectMessage')

            axios
                .get(`/api/chat/${this.$route.params.id}/get-or-create/`)
                .then(response => {
                    console.log(response.data)

                    this.$router.push('/chat')
                })
                .catch(error => {
                    console.log('error', error)
                })
        },

        sendFriendshipRequest() {
            axios
                .post(`/api/friends/${this.$route.params.id}/request/`)
                .then(response => {
                    console.log('data', response.data)
                    this.can_send_friendship_request = false
                    if (response.data.message == 'request already sent') {
                        this.toastStore.showToast(5000, 'The request has already been sent!', 'bg-red-300')
                    } else {
                        this.toastStore.showToast(5000, 'The request was sent!', 'bg-emerald-300')
                    }
                })
                .catch(error => {
                    console.log('error', error)
                })
        },
        
        getFeed() {
            axios
                .get(`/api/posts/profile/${this.$route.params.id}/`)
                .then(response => {
                    console.log('data', response.data)

                    this.posts = response.data.posts
                    this.user = response.data.user
                    this.can_send_friendship_request = response.data.can_send_friendship_request
                })
                .catch(error => {
                    console.log('error', error)
                })
        },

        submitForm() {
            console.log('submitForm', this.body)

            let formData = new FormData()
            formData.append('image', this.$refs.file.files[0])
            formData.append('body', this.body)

            axios
                .post('/api/posts/create/', formData, {
                    headers: {
                        "Content-Type": "multipart/form-data",
                    }
                })
                .then(response => {
                    console.log('data', response.data)

                    this.posts.unshift(response.data)
                    this.body = ''
                    this.$refs.file.value = null
                    this.url = null
                    this.user.posts_count += 1
                })
                .catch(error => {
                    console.log('error', error)
                })
        },

        logout() {
            console.log('Log out')

            this.userStore.removeToken()

            this.$router.push('/login')
        }
    }
}
</script>