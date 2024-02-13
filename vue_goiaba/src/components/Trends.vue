<template>
    <div class="p-4 bg-white border border-gray-200 rounded-lg">
            <h3 class="mb-6 text-xl">Trends</h3>
    
            <div class="space-y-4">
                <div 
                class="flex items-center justify-between sm:flex-col md:flex-row"
                v-for="trend in trends"
                v-bind:key="trend.id"
                >  
                    <p class="text-xs flex space-x-2 mb-2">
                        <strong>#{{ trend.hashtag }}</strong><br>
                        <span class="text-gray-500">{{ trend.occurences }} posts</span>
                    </p>
                    <RouterLink :to="{name: 'trendview', params: {id: trend.hashtag}}" class="py-2 px-3 bg-pink-600 text-white text-xs">Explore</RouterLink>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'trends',

    data() {
        return {
            trends: []
        }
    },

    mounted() {
        this.getTrends()
    },

    methods: {
        getTrends() {
            axios
                .get('/api/posts/trends/')
                .then(response => {
                    console.log(response.data)

                    this.trends = response.data
                })
                .catch(error => {
                    console.log('Error: ', error)
                })
        }
    }
}
</script>