<template>
    <p>{{ lootText }}</p>
</template>

<script>
export default {
    props: ['loot'],

    computed: {
        lootText() {
            if(this.loot) {
                return 'Поздравляем, вы нашли ' + this.loot.name;
            } else {
                return 'Ничего не найдено'
            }
        }
    }
}
</script>