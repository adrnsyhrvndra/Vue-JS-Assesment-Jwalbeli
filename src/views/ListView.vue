<template>

    <div>

        <NavbarView />

        <div class="container-fluid">

            <div class="row">

                <div class="col-lg-12">

                    <div class="jumbotron bg-white">

                    <div class="container text-center">

                    <h1 class="display-4">Comment List Page</h1>

                    <p class="lead">This is a comment list page for showing al data from resource.</p>

                    </div>

                </div>

                </div>

            </div>

        </div>

        <div class="container">

            <div class="row justify-content-md-center text-center">

                <div class="col-lg-10">

                    <h1>Comment List From Resource</h1>

                </div>
                
            </div>

            <div class="row mt-1">

                <div class="col-lg-3 mt-4" v-for="post in posts" v-bind:key="post.id">

                    <CardPost :post="post"/>

                </div>

            </div>

        </div>

        <div class="container">

        <footer class="d-flex flex-wrap justify-content-between align-items-center py-3 my-4 border-top">

            <div class="col-md-4 d-flex align-items-center">

            <a href="/" class="mb-3 me-2 mb-md-0 text-muted text-decoration-none lh-1">

                <b-icon icon="shop-window" class="rounded bg-warning p-1" variant="dark"></b-icon>

            </a>

            <span class="text-muted ml-1"> &copy; 2022 Jwalbeli Company</span>

            </div>

        </footer>
        
        </div>

    </div>

</template>

<script>
// @ is an alias to /src
import NavbarView from '@/components/NavbarView.vue'
import CardPost from '@/components/CardPost.vue'
import axios from 'axios'

export default {

    name: 'ListView',
    components: {
        NavbarView,
        CardPost
    },

    data(){

        return{

            posts: []

        }

    },

    methods: {

        setPosts(data){

            this.posts = data
            
        }

    },

    mounted(){

        axios.get('https://jsonplaceholder.typicode.com/posts')
        .then((response) => this.setPosts(response.data))
        .catch((error) => console.log("Gagal : ",error));

    }

    };
</script>

<style>

</style>