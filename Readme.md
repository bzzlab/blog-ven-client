# Get started with the blog application
### Introduction
This Blog-application has been developed with the following technology-stack:
#### Backend
* Express.js (middleware, model-view-controller)
* Alasql.js (simple file-based database)
* Node.js (webbased backend infrastructure)

#### Frontend (external repo)
* Vue.js (component-based user-interfaces)
* babel (transpiler, compatibility of new ECMAScript 6 and higher to ECMAScript 5)


## Part 1: Installing the frontend
### Prerequisite
You need to install [nodejs](https://nodejs.org/en/) in order to install the required infrastructure. With the installation of nodejs the tool `npm` (Node package manager) is included.

### Remarks for MacOS-users
When using  `npm` on the command line the usage differs on Windows and MacOS based platforms.
#### Windows 
On Windows you can use the `npm ...` straight away. Example: 
```
npm install
```
#### MacOS
On MacOS - if you open the terminal as non-administrator - then use it with the `sudo`-command 
Example: 
```
sudo npm install
``` 
and then type  in the administrator password. 
In the following installation guide the `sudo`-command is omitted. But be aware of the if you're an Apple user without default administrator privileges.

### Installation guide
Step 1: Clone the code from this repo from the command-line
```
git clone https://github.com/bzzlab/blog-ven-client.git
```
Step 2: Change into the app directory
```
cd blog-ven-client
```
Step 3: Install app dependencies
```
npm install
```
Step 4: Build application
```
npm run build-client
```
Step 5: Run application
```
npm run run-client
```

## Part 2: Add some blog-posts to the server
 

## Part 3: Open client in [WebStorm](https://www.jetbrains.com/webstorm/) by Jetbrains (integrated development environment)
Task 1: Add the following code and see what happens.
        <!-- Task-1: Add code here -->
        <div>
            {{ blogs }}
        </div>
        <!-- Task-End -->

        <!-- Task-2: Add code here -->
        <div v-for="entry in blogs">
            <div class="card" style="width: 25rem;">
                <div class="card-body">
                    <h5 class="card-title">{{ entry.title }}</h5>
                    <h6 class="card-subtitle mb-2 text-muted">From {{ entry.nickname }}</h6>
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                </div>
            </div>
        <div style="margin-bottom: 1rem"></div>
        </div>
        <!-- Task-End -->

        <!-- Task-3: Add code here -->
        <h4 style="margin-top: 2rem; margin-bottom: 1rem">Post a blog</h4>
        <form @submit.prevent="addPost">
            <div class="form-group col-md-6">
                <div class="form-group">
                    <label for="nickname">Nickname</label>
                    <input v-model="blog.nickname" type="text" class="form-control" id="nickname" placeholder="Nickname">
                </div>
                <div class="form-group">
                    <label for="title">Title</label>
                    <input v-model="blog.title" type="text" class="form-control" id="title" placeholder="Title">
                </div>
                <div class="form-group">
                    <label for="content">Text</label>
                    <textarea v-model="blog.content" class="form-control" id="content" rows="3"/>
                </div>
                <div class="form-group">
                    <button type="submit" class="btn btn-primary" data-toggle="modal"
                            data-target="#confirmBlogEntry">Create</button>
                </div>
            </div>
        </form>
        <!-- Task-End -->