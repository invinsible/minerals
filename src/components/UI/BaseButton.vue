<template>
    <button :type="type" @click="someAction">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: ['type'],

    methods: {
        someAction() {
            this.$emit('some-action');
        }
    }
}
</script>