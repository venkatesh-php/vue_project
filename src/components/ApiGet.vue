<template>
    <div>
        <!-- <button @click="getPosts">Load Posts</button> -->
        <h3 v-if="errorMsg">{{ errorMsg }}</h3>
         <table class="table">
            <thead>
                <tr>
                    <th scope="col">SNO</th>
                    <th scope="col">Title</th>
                    <th scope="col">Content</th>
                    <th scope="col">View</th>
                    <th scope="col">Edit</th>
                    <th scope="col">Delete</th>
                </tr>
            </thead>
            <tbody v-for="post in posts" :key="post.id">
                <tr>
                    <td>{{ post.id }}</td>
                    <td>{{ post.title }}</td>
                    <td>{{ post.body }}</td>
                    <td><button @click="view">View</button></td>
                    <td><button @click="edit">Edit</button></td>
                    <td><button @click="deleteProduct(post.id)">Delete</button></td>
                </tr>
            </tbody>
        </table>


        <!-- <div v-for="post in posts" :key="post.id">
            <h3>{{ post.id }}.{{ post.title }}</h3>
            <p>{{ post.body }}</p>
            <hr />
        </div> -->
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'ApiGet',
    created () {
        this.getPosts()
    },
    data() {
        return  {
            posts: [],
            errorMsg: '',
        }
    },
    methods: {
        getPosts(){
            axios
            .get('https://jsonplaceholder.typicode.com/posts')
            .then((response) => {
                console.log(response.data)
                this.posts = response.data
            })
            .catch((error) => {
                //console.log(error)
                this.errorMsg = 'We got error while retrieving data'
            })
        },
        async deleteProduct(productId) {
            console.log(productId)
             await axios
            .delete('https://jsonplaceholder.typicode.com/posts/${productId}')
            .then((response) => {
                console.log(response)
            })
            .catch((error) => {
                //console.log(error)
                this.errorMsg = 'product not deleted'
            })

        },
    },
}
</script>
<style>
    
</style>