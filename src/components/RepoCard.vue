<template>
    <nav id="nav" class="bg-lime-100 p-5 shadow-lg flex flex-col justify-between items-center mb-10 md:flex-row" >
        <h1 class="text-3xl ml-10">Thumin</h1>
        <a href="https://github.com/Thu-Min" target="_blank">
            <button class="bg-emerald-200 p-3 rounded-xl mr-10">
                View on Github
            </button>
        </a>
    </nav>  
    <div class="grid grid-cols-4 gap-10 ml-14">
        <div class="block rounded-lg shadow-lg bg-lime-200 max-w-sm transform transition duration-500 hover:scale-110" v-for="(repo, index) in repoList" :key="index">
            <div class="flex flex-row justify-between items-center py-3 px-6 border-b border-gray-900">
                <h3 class="text-xl font-bold">{{ repo.name }}</h3>
                <p class="py-1 px-4 bg-emerald-200 rounded-full">{{ repo.language }}</p>
            </div>
            <!-- stargazers_count -->
            <div class="p-6 h-60 text-start">
                <h5 class="text-gray-900 font-medium mb-2 ">{{ repo.description }}</h5>
                <p class="text-gray-700 text-base mb-8">
                    {{  }}
                </p>
                <h1 class="text-gray-700 text-base">{{ repo.html_url }}</h1> 
            </div>
            <div class="flex flex-row justify-between items-center py-3 px-6 border-t border-gray-900 text-gray-600">     
                <h1>{{ repo.pushed_at }}</h1>
                <button @click="copy()" class="bg-emerald-200 py-1 px-3 rounded-lg">Copy URL</button>
            </div>  
        </div>
    </div>
</template>

<script>
    import axios from "axios"
    export default {
        name: 'RepoCard',
        data() {
            return {
                repoList: [],
                // url: ''
            }
        },
        mounted () {
            axios.get("https://api.github.com/users/Thu-Min/repos")
                .then((response) => {
                    this.repoList = response.data;
                    // console.log(response.data);
                    // for(let i = 0; i < this.response.data.length; i++){
                    //     this.url = this.response.data[i].html_url;
                    // }

                    // console.log(this.url);
                });
        },
        // methods: {
        //     copy() {
        //         for(let i = 0; i < this.repoList.length; i++){
        //             this.url = this.repoList["html_url"][i];
        //         }
        //         navigator.clipboard.writeText(this.url);
        //     }
        // }
    }
</script>