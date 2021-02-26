<template>
    <p v-if="tired < 39">Вы сейчас {{ status }}</p>
    <p v-else>Вам требуется отдохнуть</p>
    <small>Усталость: {{ tired }}</small>
    <div class="tire-wrapper">        
        <p class="tire" :style="{width: tired + '%'}"></p>
    </div>        
</template>


<script>
export default {
    props: ['iswork', 'tired'],

    computed: {
        status() {
            if(!this.iswork) {
                return 'отдыхаете.'
            } else {
                return 'работаете...'
            }           
        },       
    }
}
</script>


<style scoped>
    .tire-wrapper {
        width: 390px;
        border: 1px solid rgb(134, 35, 35);
    }
    .tire {
        margin: 0;
        height: 10px;   
        background-color: brown;
        color: #fff;
        transition: width 0.3s ease-out;
    }
</style>

