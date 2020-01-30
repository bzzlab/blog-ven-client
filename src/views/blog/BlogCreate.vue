<template>
    <div id="create_post">
    <h1>Blog</h1>
        <p>What were experiences in your last concert? Just tell to the community.</p>
        <h4>Recent entries</h4>

        <!-- Task-1: Add code here -->
        <!-- Task-End -->

        <!-- Task-2: Add code here -->
        <!-- Task-End -->

        <!-- Task-3: Add code here -->
        <!-- Task-End -->



        <div style="margin-bottom: 5rem"> {{ message }} </div>
    </div>
</template>

<script>
    import store from '../../store';
    import http from 'axios'
    const API_URL = store.state.apiUrl;
    export default {
        name: "BlogCreate",
        data: () => ({
            message: null,
            blogs: null,
            blog: {
                nickname: "",
                title: "",
                content: ""
            }
        }),
        mounted() {
            /*  When this site is called then mounted-function will be automatically called.
                It makes a call to the server with the corresponding API
             */
            //later replace by http.get(this.$store.state.apiUrl) ...
            http.get(API_URL +'/api/blog')
                .then(response => (this.blogs = response.data));
        },
        methods:{
            //Used methods in the form
            addPost(){
                fetch(API_URL +'/api/blog',
                    {
                        method: 'POST',
                        body: JSON.stringify(this.blog),
                        headers: {"content-type":"application/json"}
                    })
                    .then(res => res.json());
                this.message = 'Your blog has been posted.';
                location.reload();
            },
            proceed(){
                //redirect to oder list
                this.$router.push("/blog");
                this.message = 'Blog posted.'
            }
        }
    }
</script>
