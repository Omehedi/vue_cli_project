<template>
    <div class="row row-cols-1 row-cols-md-3 g-4">
        <div v-for="(item, index) in items" :key="index" class="col">
            <div class="card shadow-sm h-100">
                <img :src="item.photo" class="card-img-top" alt="Item Image">
                <div class="card-body">
                    <h5 class="card-title">{{ item.title }}</h5>
                    <p class="card-text text-muted">{{ item.price }}</p>
                    <a @click="addToCart(item)" class="btn btn-primary w-100">+ Add</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Inventory',
        props: ['items'],
        methods : {
            addToCart(item){
                this.$emit('newItemAdded',item)
            }
        }
    }
</script>

<style>
    .card {
        border-radius: 12px;
    }

    .card-img-top {
        border-top-left-radius: 12px;
        border-top-right-radius: 12px;
        object-fit: cover;
        height: 200px;
    }

    .card-body {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .card-title {
        font-weight: 600;
        color: #333;
    }

    .btn-primary {
        background-color: #007bff;
        border-color: #007bff;
        transition: background-color 0.3s ease;
    }

    .btn-primary:hover {
        background-color: #0056b3;
        border-color: #0056b3;
    }
</style>
