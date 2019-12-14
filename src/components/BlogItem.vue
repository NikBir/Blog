<template>
    <li>
        <span>
            <strong>{{ blogItem.id }}</strong>
            {{ blogItem.title }}
        </span>
        <button class="btn-remove" 
                v-on:click="$emit('remove-item', blogItem.id)"
        >&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        blogItem: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        border-radius: 5px;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        box-shadow: 0 0 10px rgba(200, 200, 200, 1);
    }

    .btn-remove {
        background: red;
        color: #fff;
        border-radius: 50%;
        font-weight: bold;
        border: 1px solid red;
    }
</style>