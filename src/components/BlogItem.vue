<template>
    <li>
        <div class="div-item">
            <div class="div-text-title">
                <span>
                    {{ blogItem.title }}
                </span>
            </div>
            <hr v-if="!checkLogin">
            <div class="div-btn"
                v-if="!checkLogin"
            >
                <button class="btn-edit"
                        @click="show"
                >Edit</button>
                <button class="btn-remove" 
                        v-on:click="$emit('remove-item', blogItem.id)"
                >Delete</button>
            </div>
        </div>
        <ModalCheageBlog
            v-if="showEdit"
            @closeEdit="closeEdit"
            @edit-blog="editBlog"
        />
    </li>
</template>

<script>
import ModalCheageBlog from '@/components/ModalCheageBlog'
export default {
    props: {
        checkLogin: Boolean,
        blogItem: {
            type: Object,
            required: true
        },
        index: Number
    },
    data() {
        return {
            showEdit: false
        }
    },
    methods: {
        show() {
            this.showEdit = true
            this.$emit('text', this.blogItem.title)
        },
        closeEdit() {
            this.showEdit = false
        },
        editBlog(value) {
            this.showEdit = false
            this.blogItem.title = value.title
        }
    },
    components: {
        ModalCheageBlog
    }
}
</script>

<style scoped lang="scss">
    li {
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        box-shadow: 0 0 10px rgba(200, 200, 200, 1);
    }
    .div-item {
        span {
            display: block;
        }
        hr {
            margin: 5px;
        }
    }
    .div-text-title {
        display: flex;
        padding: 20px 0;
        text-align: start;
    }
    .div-btn {
        margin: 0;
        display: flex;
        justify-content: flex-end
    }
    .btn-edit {
        background: #ddd;
        border-radius: 5px;
        font-weight: bold;
        font-size: 1.05rem;
        padding: 5px 10px;
        border: none;
        margin-right: 6px;
        box-shadow: 0 0 0 1px rgba(68, 68, 68, 0.5) inset;
        &:hover {
            background: #444;
            color: #fff;
            box-shadow: 0 0 5px rgba(68, 68, 68, .5);
            cursor: pointer;
        }
    }
    .btn-remove {
        background: rgb(250, 25, 25);
        color: #fff;
        border-radius: 5px;
        font-weight: bold;
        font-size: 1.05rem;
        border: none;
        padding: 5px 10px;
        margin-left: 6px;
        &:hover {
            background: #fff;
            color: rgb(250, 25, 25);
            box-shadow: 0 0 0 1px rgb(250, 25, 25) inset, 0 0 5px rgba(250, 25, 25, .5);
            cursor: pointer;
        }
    }
</style>