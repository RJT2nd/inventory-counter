<template>
    <div class="inventory-item">
        <div class="inventory-item-description">
            {{ item.description }}
        </div>
        <div class="inventory-item-form">
            <div class="decrement" v-on:click="decrement">-</div>
            <input type="text" v-model="item.quantity" />
            <div class="increment" v-on:click="increment">+</div>
        </div>
    </div>
</template>

<script>

export default {
    data() {
        return {
            item: {
                description: this.description,
                quantity: 0
            }
        };
    },
    props: {
        description: String
    },
    methods: {
        decrement: function() {
            this.item.quantity--;
        },
        increment: function() {
            this.item.quantity++;
        }
    }
}

</script>
<style>

.inventory-item-description {
    display: inline-block;
    width: 10em;
}

.inventory-item-form {
    display: inline-block;
}

.decrement {
    display: inline-block;
    padding: 10px 30px;
    background-color: #F75270;
    margin: 0px 10px;
    border-radius: 5px;
    user-select: none;
}

.increment {
    display: inline-block;
    padding: 10px 30px;
    background-color: #4EFC6E;
    margin: 0px 10px;
    border-radius: 5px;
    user-select: none;
}


</style>