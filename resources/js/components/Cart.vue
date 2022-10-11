<template>
    <div style="text-align: center; width: 50rem;">
        <h1 class="cart">Cart</h1>
        <div>
            <table-cart :carts="carts" />
        </div>
    </div>
</template>
<script>
export default {
    props: ['carts'],
}
</script>
<style>
.cart{
    text-align: left;
    border-bottom: groove;
}
</style>