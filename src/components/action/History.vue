<template>
    <h3>История:</h3>
    <p v-for="item in historyArray"
        :key="item.date">
        <small>({{item.date}}) {{ item.name }} </small>        
    </p>   
</template>

<script>
export default {   
    props: ['historyArray'],
}
</script>

<style scoped>
 p {
     margin: 0;
 }
</style>

