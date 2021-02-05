<template>
    <h3>История:</h3>
    <p v-for="item in history"
        :key="item.id">
        <small>{{item.date.getHours()}}:{{item.date.getMinutes()}}:{{item.date.getSeconds()}} {{ item.name }} </small>        
    </p>   
</template>

<script>
export default {
    props: ['history'],

   
}
</script>

<style scoped>
 p {
     margin: 0;
 }
</style>