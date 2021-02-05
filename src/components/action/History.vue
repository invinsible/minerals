<template>
    <h3>История:</h3>
    <p v-for="item in historyIn"
        :key="item.date">
        <small>({{item.date}}) {{ item.name }} </small>        
    </p>   
</template>

<script>
export default {
    created() {
        this.getHistory();
    },

    updated() {
        this.getHistory();
    },
    props: ['weblink'],

    data() {
        return {
            historyIn: []
        }
        
    },
    
    methods: {
        getHistory() {
            fetch(this.weblink).then((response) => {
                if (response.ok) {
                    return response.json()
                }
            }).then((data) => {
                this.historyIn = data ;
            })
        }
    }
}
</script>

<style scoped>
 p {
     margin: 0;
 }
</style>

