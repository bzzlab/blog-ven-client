<template>
    <div id="create_post">
    <h1>Create Blog</h1>
        <p>Fill out the form below to create your blog-entry.</p>
        <h4>Recent entries</h4>
        <div>
            {{ blogs }}
        </div>
        <form @submit.prevent="addPost">
            <div class="form-row">
                <div class="form-group col-md-6">
                    <label for="title">Email</label>
                    <input v-model="blog.title" type="text" class="form-control" id="title" placeholder="Title">
                </div>
                <div class="form-group col-md-6">
                    <label for="content">Your blog-entry</label>
                    <textarea v-model="blog.content" class="form-control" id="content" rows="3"/>
                </div>
            </div>
            <div class="form-group">
                <button type="submit" class="btn btn-primary" data-toggle="modal"
                        data-target="#confirmBlogEntry">Blog now</button>
            </div>
        </form>
    </div>
</template>

<script>
    import store from '../../store';
    const API_URL = store.state.apiUrl;
    export default {
        name: "BlogCreate",
        data: () => ({
            blogs: [],
            id: "blog-17",
            blog: {
                nickname: "",
                title: "",
                content: ""
            }
        }),
        mounted() {
            //later replace by fetch(this.$store.state.apiUrl);

            fetch(API_URL +'/api/blog', {
                method: 'GET', // *GET, POST, PUT, DELETE, etc.
                mode: 'cors', // no-cors, *cors, same-origin
                cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
                credentials: 'same-origin', // include, *same-origin, omit
                headers: {
                    'Content-Type': 'application/json'
                    // 'Content-Type': 'application/x-www-form-urlencoded',
                },
                redirect: 'follow', // manual, *follow, error
                referrerPolicy: 'no-referrer', // no-referrer, *client
                body: JSON.stringify(data) // body data type must match "Content-Type" header
            }).then(function (res) {
                return res.json(); // parses JSON response into native JavaScript objects
            });

            // fetch(API_URL +'/api/blog', {method: 'GET', headers: 'application/json'})
            //     //pay attention .then(res => console.log(res.json())) won't work
            //     .then(res => console.log(res));
            //     //.then(res => this.blogs = res.data.result);
        },
        methods:{
            addPost(){
                fetch(API_URL +'/api/post',
                    {
                        method: 'POST',
                        body: JSON.stringify(this.blog),
                        headers: {"content-type":"application/json"}
                    })
                    .then(res => res.json())
                    .then(res => this.id=res.id);
                this.proceed();
            },
            proceed(){
                //redirect to oder list
                this.$router.push("/blog");
            }
        }
    }
</script>
