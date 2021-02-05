<template>
    <p>Вы сейчас {{ status }}</p>
</template>

<script>
export default {
    props: ['iswork'],
    computed: {
        status() {
            if(!this.iswork) {
                return 'отдыхаете.'
            } else {
                return 'работаете...'
            }
           
        }
    }
}
</script>