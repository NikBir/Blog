<template>
    <div class="container">
        <div class="div-welcome">
            <p>Welcome, {{ login }}</p>
        </div> 
        <div class="div-btn">
            <button class="btn-signout">Sign out</button>
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            login: 'Name'
        }
    }
}
</script>

<style lang="scss">
.container {
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 5px;
}
.div-welcome{
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 20px;
    height: 100%;
    p {
        margin: 0;
        font-size: 1.5rem;
    }
}
.div-btn {
    display: flex;
    margin: 0 20px;
    height: 100%;
    justify-content: center;
    align-items: center;
    .btn-signout {
        outline: none;
        display: inline-block;
        height: 100%;
        border-radius: 5px;
        border: 1px solid #444;
        background: #eee;
        padding: 0 20px;
        font-weight: 500;
        font-size: 1.1rem;
        &:hover {
            cursor: pointer;
            background: #444;
            color: #fff;
            box-shadow: 0 0 7px rgba(#444, $alpha: .5);
        }
    }
}
</style>