<template>
    <div>
        <input @input="onChange" type="text" />
    </div>
</template>
<script>
    export default{
        name:"SearchInput",
        methods:{
            onChange:function(event){
                //console.log(event.target.value);
                //every single thing the user types
                //is written in console by above line.
                //with the above line the foll line is changed
                //<input v-on:input="onChange" type="text"> in the div tag at the top.
                // or:-> <input @input="onChange" type="text">
                const term=event.target.value;
                this.$emit("newTerm",term);
            }
        }
    }
</script>
<style>

</style>