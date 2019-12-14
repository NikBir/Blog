<template>
    <form v-if="showModal">
        <input type="text">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data () {
        return {
            showModal: false
        }
    },
    methods: {
        setValue: function(value) {
            this.showModal = value
        }
    },
    created: function() {
        this.$parent.$on('show', this.setValue)
    }
}
</script>

<style lang="scss">
    form {
        display: flex;
    }
</style>