<template>
    <div class="">
      <h1>This is an blog view</h1>
      <div class="mt-3 max-w-2x1 mx-auto text-xl text-gray-500 sm:mt-4">
          <div class="mt-12 max-w-lg mx-auto grid gap-5 lg:grid-cols-3 lg:max-w-none">
              <div v-for="posts in APIData" :key="posts.id">
                <router-link :to="{name:'BlogPost', params: {id: posts.id, title:posts.title, thumbnail: posts.thumbnail, slug: posts.slug, excerpt: posts.excerpt, content: posts.content }}">
                  <p>
                    {{ posts.slug }}
                  </p>
                </router-link>
                
              </div>
            </div>
          </div>
      </div>
  </template>
 
  
  
<script>
import { getAPI } from "../axios-api";

export default{
  name: 'Blog',
  data(){
    return{
      APIData: []
    }
  },

  created(){
    getAPI.get('/blog/posts/',)

    .then(response =>{
      console.log('Post API has received data')
      this.APIData = response.data
    })
    .catch(err =>{
      console.log(err)
    })
  }
}
</script>