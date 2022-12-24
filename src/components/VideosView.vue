<template>
    <ul>
        <ItemView v-for="video in videos" v-bind:key="video.id"
         v-bind:video="video"
         >Video</ItemView>
    </ul>
</template>
<!--props is the data from parent componenent
to child component. and emitting events is the data
from child component to parent component. 
-->
<script>
import ItemView from "./ItemView.vue";
    export default{
        name:'VideosView',
        props:["videos"],
        components:{
            ItemView,
        }
    }
</script>
<style>

</style>