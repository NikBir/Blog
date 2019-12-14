<template>
    <div class="div-container-list">
        <ul>
            <BlogItem
                v-for="blogItem of blogs"
                v-bind:blogItem="blogItem"
                v-on:remove-item="removeItem"
                :key='blogItem.blogs'
            />
        </ul>
    </div>
</template>

<script>
import BlogItem from '@/components/BlogItem'
export default {
    props: ['blogs'],
    components: {
        BlogItem
    },
    methods: {
        removeItem(id) {
            this.$emit('remove-item', id)
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
    .div-container-list {
        width: 50%;
        margin: 0 auto;
    }
</style>