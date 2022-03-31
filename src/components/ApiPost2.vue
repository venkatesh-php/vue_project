<template>
    <div>
        <!-- <form @submit.prevent="createPost">
            <div>
                <label for="userId"> Post User Id</label>
                <input tyep="text" id="userId" v-model="formData.userId" />
            </div>
            <div>
                <label for="title"> Post Title</label>
                <input tyep="text" id="title" v-model="formData.title" />
            </div>
            <div>
                <label for="body">Body</label>
                <input tyep="text" id="body" v-model="formData.body" />
            </div>
            <button>Create Post</button>
            
        </form> -->

        <form @submit.prevent="createPost">
            <div class="form-group col-md-6">
                <label for="userId">User ID</label>
                <input type="text" class="form-control" id="userId" v-model="formData.userId" placeholder="Enter User Id" />
                
            </div>
            <div class="form-group col-md-6">
                <label for="title">Title</label>
                <input type="text" class="form-control" id="title" v-model="formData.title" placeholder="Enter Title" />
            </div>
            <div class="form-group col-md-6">
                <label for="body">Body</label>
                <textarea class="form-control" id="body" rows="3" placeholder="Enter your message here....." v-model="formData.body" />
            </div>

            <button class="btn btn-primary">Submit</button>
    </form>

        
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: "ApiPost2",
    data() {
        return {
            formData: {
                userId: '',
                title: '',
                body: '',
            },
        }
    },
    methods: {
        createPost() {
            axios
            .post('https://jsonplaceholder.typicode.com/posts', this.formData)
            .then((response) => console.log(response))
            .catch((error) => console.log(error))

        }
    }, 
}
</script>
<style>
form {
    padding-left: 200px;
}
    
</style>