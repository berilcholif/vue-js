<template>
    <div>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet">
        <div class="row">
            <div class="col-md-8" style="display:grid; grid-template-columns:max-content; margin:auto">
                <div>
                    <div v-for="(item) in allProduct" :key="item.id" class="card product-item" style="display: flex;  width: 18rem; float: left;">
                        <div class="card-body">
                            <h4 class="card-title">{{ item.name }}</h4>
                            <div class="row">
                                <div class="col-md-6">Stock {{ item.qty }}</div>
                                <div class="col-md-6 text-right">Rp. {{ item.price }}</div>
                            </div>
                            <p v-if="item.qty > 0" class="text-right mt-2">
                                <button style="border-radius:20px;" @click="addToCart(item.id)">Add</button>
                            </p>
                            <p v-else>
                                <button style="background: #ccc; width">Stock Kosong</button>
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['allProduct'],
    methods: {
        addToCart(id) {
            this.$emit("emitAddToCart", id);
        },
    }
}
</script>