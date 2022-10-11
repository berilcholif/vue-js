
    <template>
        <div class="container">
            <all-product :allProduct="allProduct" @emitAddToCart="addToCart" />
            <cart :carts="carts" />
        </div>
    </template>
        
    <script>
    export default {
        data() {
            return {
                allProduct: [
                    {
                        id: 1,
                        name: "Indomie Goreng Kuah",
                        qty: 20,
                        carts_qty: 0,
                        price: 3500,
                        carts_price: 0,
                    },
                    {
                        id: 2,
                        name: "Indomie Goreng Kuah",
                        qty: 10,
                        carts_qty: 0,
                        price: 3500,
                        carts_price: 0,
                    },
                    {
                        id: 3,
                        name: "Indomie Goreng Sedap",
                        qty: 20,
                        carts_qty: 0,
                        price: 3500,
                        carts_price: 0,
                    }
                ],
                carts: []
            }
        },
        methods: {
            addToCart(id) {
                let produk = this.allProduct.find((item) => item.id == id);
                let cart = this.carts.find((item) => item.idProduk == id);
                let idProduk = produk.id;
                let name = produk.name;
                let price = produk.price;
                if (!cart) {
                    let cartTotal = {
                        idProduk: idProduk,
                        name: name,
                        price: price,
                        qty: 1,
                        subTotal: price,
                    };
                    this.carts.push(cartTotal);
                    console.log(cartTotal.imgUrl)
                } else {
                    cart.qty++;
                    cart.subTotal = cart.qty * cart.price;
                }
            },
        }
    }
    </script>
    <style>
        button {
            background: yellowgreen;
            border: none;
            border-radius: 100%;
            cursor: pointer;
            height: 2rem;
            width: 100%;
        }
    .container {
    margin: 0 auto;
    width: 100%;
    margin-top: 10vh;
    display: grid;
    gap: 11rem;
  }
        </style>