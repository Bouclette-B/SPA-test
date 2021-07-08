<template>
    <section class="menu">
    <h2>Menu</h2>
    <div v-for="item in simpleMenu" :key="item.name" class="menu-item">
        <img
            class="menu-item__image"
            :src="item.image.source"
            :alt="item.image.alt"
        />
        <div>
            <h3>{{ item.name }}</h3>
            <p v-if="item.inStock">En stock</p>
            <p v-else>En rupture de stock</p>
            <div>
                <label for="add-item-quantity"
                    >Quantité : </label
                >
                <input
                    v-model.number="quantity"
                    id="add-item-quantity"
                    type="number"
                />
                <button @click="addItem()">
                    Ajouter au panier d'achat
                </button>
            </div>
        </div>
    </div>
</section>
</template>
<script>
export default {
    name: 'MenuItem',

    props: {
        simpleMenu: Array,
    },

    data() {
        return {
            quantity: 0,
        }
    },

    methods: {
        addItem(){
            this.$emit('add-item', this.quantity)
        }
    }

}
</script>