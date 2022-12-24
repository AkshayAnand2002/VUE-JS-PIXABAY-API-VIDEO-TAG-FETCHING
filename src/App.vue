<template>
  <div>
    <SearchInput @newTerm="handleNewTerm"></SearchInput>
    <!--
      in place of above we can write identical statement :-
      <SearchInput v-on:newTerm="handleNewTerm"></SearchInput>
    -->
    <!-- <VideosView :videos="videos" ></VideosView> -->
    <!--below is the another way to write v-bind staatement.-->
    <VideosView v-bind:videos="videos" ></VideosView>
    <!--videos="videos"
    LHS is the property that exists in the child component
    i.e. VideosView and the RHS is property of parent component
    i.e. App.
    V-bind is used as any time videos component is updated in
    parent it should automatically be rendered to child.
    -->
    <!-- {{ videos.valueOf() }} -->
  </div>
</template>

<script>
import SearchInput from "./components/SearchInput.vue";
const API_KEY="32323331-b91de8c8eefa153fcaf5dc505";
import VideosView from "./components/VideosView.vue";
export default {
  name: 'App',
  components:{
    SearchInput,
    VideosView,
  },
  data(){
    return {
      videos:[],
    };
  },
  methods:{
    handleNewTerm: async function(searchInput){
      // console.log(searchInput);
      const response = await fetch('https://pixabay.com/api/videos/?' + 
       new URLSearchParams({
          key:API_KEY,
          q:searchInput
       }))
       const data = await response.json();
      //  console.log(response);
      this.videos= data.hits;
    },
  },
};
</script>

<style>
</style>
