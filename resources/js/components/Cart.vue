<!--<template>-->
<!--    <ul class="list-group shadow-sm p-3 mb-5 bg-white rounded">-->
<!--        &lt;!&ndash; List header with bold text and a different background &ndash;&gt;-->
<!--        <li class="list-group-item d-flex justify-content-between align-items-center bg-primary text-white font-weight-bold">-->
<!--            <span class="item-name">Name</span>-->
<!--            <span class="item-price">Price</span>-->
<!--        </li>-->
<!--        &lt;!&ndash; Dynamic list items with a subtle hover effect &ndash;&gt;-->
<!--        <li v-for="(item, index) in items" :key="index" class="list-group-item d-flex justify-content-between align-items-center list-group-item-action">-->
<!--            <span class="item-name">{{ item.title }}</span>-->
<!--            <span class="item-price text-success font-weight-bold">${{ item.price }}</span>-->
<!--        </li>-->
<!--        &lt;!&ndash; Divider with a subtle color &ndash;&gt;-->
<!--        <li class="list-group-item border-0">-->
<!--            <hr class="my-1">-->
<!--        </li>-->
<!--        &lt;!&ndash; Example item for total &ndash;&gt;-->
<!--        <li class="list-group-item d-flex justify-content-between align-items-center list-group-item-action">-->
<!--            <span class="item-name">Total</span>-->
<!--            <span class="item-price text-danger font-weight-bold">${{totalPrice}}</span>-->
<!--        </li>-->
<!--    </ul>-->
<!--</template>-->

<!--<script>-->
<!--    export default {-->
<!--        props: ['items'],-->
<!--        computed : {-->
<!--            totalPrice () {-->
<!--                var total = 0-->
<!--                this.items.forEach(item=>{-->
<!--                    total += parseFloat(item.price)-->
<!--                })-->
<!--                return total-->
<!--            }-->
<!--        }-->
<!--    }-->
<!--</script>-->

<!--<style>-->
<!--    .list-group-item {-->
<!--        transition: background-color 0.2s ease;-->
<!--    }-->

<!--    .list-group-item:hover {-->
<!--        background-color: #f1f1f1;-->
<!--    }-->

<!--    .item-name {-->
<!--        font-size: 1.1rem;-->
<!--    }-->

<!--    .item-price {-->
<!--        font-size: 1.1rem;-->
<!--    }-->
<!--</style>-->



<template>
    <ul class="list-group shadow-sm p-3 mb-5 bg-white rounded">
        <!-- List header with bold text and a different background -->
        <li class="list-group-item d-flex justify-content-between align-items-center bg-primary text-white font-weight-bold">
            <span class="item-name">Name</span>
            <span class="item-price">Price</span>
            <span class="item-action">Action</span>
        </li>

        <!-- Dynamic list items with a subtle hover effect -->
        <li v-for="(item, index) in items" :key="index" class="list-group-item d-flex justify-content-between align-items-center list-group-item-action">
            <span class="item-name">{{ item.title }}</span>
            <span class="item-price text-success font-weight-bold">${{ item.price }}</span>
            <button @click="removeItem(index)" class="btn btn-outline-danger btn-sm">Remove</button>
        </li>

        <!-- Divider with a subtle color -->
        <li class="list-group-item border-0">
            <hr class="my-1">
        </li>

        <!-- Example item for total -->
        <li class="list-group-item d-flex justify-content-between align-items-center list-group-item-action">
            <span class="item-name">Total</span>
            <span class="item-price text-danger font-weight-bold">${{ totalPrice }}</span>
        </li>
    </ul>
</template>

<script>
    export default {
        props: ['items'],
        methods: {
            removeItem(index) {
                this.items.splice(index, 1);
            }
        },
        computed: {
            totalPrice() {
                let total = 0;
                this.items.forEach(item => {
                    const price = typeof item.price === 'number' ? item.price : parseFloat(item.price.replace(/[^0-9.]/g, ''));
                    total += price;
                });
                return total.toFixed(2);
            }
        }
    }
</script>

<style>
    .list-group-item {
        transition: background-color 0.2s ease;
        padding: 10px 20px; /* Adds padding for better spacing */
    }

    .list-group-item:hover {
        background-color: #f1f1f1;
    }

    .item-name {
        font-size: 1.1rem;
        flex: 2; /* Makes the name column larger */
        margin-right: 10px; /* Adds space between columns */
    }

    .item-price {
        font-size: 1.1rem;
        flex: 1; /* Sets the price column size */
        margin-right: 10px; /* Adds space between columns */
    }

    .item-action {
        font-size: 1rem;
        flex: 1; /* Sets the action column size */
        text-align: center; /* Centers the button */
    }

    .btn-outline-danger {
        padding: 4px 8px; /* Makes button size more balanced */
        font-size: 0.9rem; /* Sets font size for a professional look */
    }
</style>
