
<template>
    <div id="app">
        <!-- Use the Navbar component -->
        <Navbar @search="search"></Navbar>

        <!-- Container for Cards -->
        <div class="container mt-4">
            <div class="row">
                <div class="col-sm-9">
                    <Inventory @newItemAdded="addCartItem" :items="items"></Inventory>
                </div>

                <!-- Cart Section -->
                <div class="col-sm-3">
                    <Cart :items="cart"></Cart>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Navbar from './components/Navbar';
    import Cart from './components/Cart';
    import Inventory from './components/Inventory';
    import data from './data';

    export default {
        name: 'App',
        components: {
            Navbar,
            Cart,
            Inventory,
        },
        data() {
            return {
                items: data, // Initialize with the full data
                cart: []
            }
        },
        methods: {
            search(keyword) {
                this.items = data.filter(item =>
                    item.title.toLowerCase().includes(keyword.toLowerCase())
                );
            },
            addCartItem(item) {
                this.cart.push(item);
            }
        }
    };
</script>

<style>
    .container {
        max-width: 1200px;
    }

    .card-body {
        text-align: center;
    }
</style>
