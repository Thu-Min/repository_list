<template>
    <div class="grid grid-cols-4 gap-4 ml-14">
        <div class="block rounded-lg shadow-lg bg-white max-w-sm text-center" v-for="(repo, index) in repoList" :key="index">
            <div class="flex flex-row justify-between items-center py-3 px-6 border-b border-gray-300">
                <h3>Repository</h3>
                <p>{{ repo.stargazers_count }} Star</p>
            </div>
            <div class="p-6 h-60">
                <h5 class="text-gray-900 text-xl font-medium mb-2">{{ repo.name }}</h5>
                <p class="text-gray-700 text-base mb-8">
                    {{ repo.html_url }}
                </p>
            </div>
            <div class="flex flex-row justify-between items-center py-3 px-6 border-t border-gray-300 text-gray-600">     
                <h1>{{ repo.pushed_at }}</h1>
                <button type="button" class="inline-block px-6 py-2.5 bg-blue-600 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out">Button</button>
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
            }
        },
        mounted () {
            axios.get("https://api.github.com/users/Thu-Min/repos?sort=updated")
                .then((response) => {
                    this.repoList = response.data;
                });
        },
    }
</script>