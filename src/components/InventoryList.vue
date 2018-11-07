<template>
    <div class="inventory-list">
        <div v-if="items.length == 0">
            <h2>Add an item to begin</h2>
        </div>
        <ul v-else class="inventory-list-ul">
            <li class="inventory-list-item" v-for="(item, index) in items" v-bind:key="index">
                <InventoryItem v-bind:description="item.description"></InventoryItem>
            </li>
        </ul>
        <div class="inventory-list-form">
            <label for="description"></label>
            <input type="text" placeholder="description" v-model="description"
                v-on:keyup.enter="addItem" />
            <button type="button" v-on:click="addItem">Add Item</button>
        </div>
    </div>
</template>
<script>
import InventoryItem from "./InventoryItem.vue";

export default {
    components: {
        InventoryItem
    },
    data() {
        return {
            items: [],
            description: "",
            id: 0
        };
    },
    methods: {
        addItem: function() {
            this.items.push({
                id: this.id,
                description: this.description
            });
            this.id++;
            this.description = "";
        },
        //removeItem: function(item) {
        //    this.items = this.items.filter(function(value, index, arr) {
        //        
        //    })
        //}
    }
}
</script>
<style>

.inventory-list {
    margin: auto;
}

.inventory-list-ul {
    border-style: solid;
    border-width: 2px;
    border-radius: 10px;
    padding: 15px;
    max-width: 80%;
    margin: auto;
}

.inventory-list-item {
    list-style-type: none;
    padding-top: 5px;
}

.inventory-list-form {
    margin-top: 10px;
}

</style>