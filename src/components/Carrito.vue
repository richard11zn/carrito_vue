<template>
    <div class="my-5">
        <h4>Carrito de compras</h4>

        <table class="table">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Item</th>
                    <th scope="col">Cantidad</th>
                    <th scope="col">Acción</th>
                    <th scope="col">Total</th>
                </tr>
            </thead>
            <tbody id="items">
                <Item
                    v-for="item in items" :key="item.id"
                    :item="item"
                 />
            </tbody>
            <tfoot>
                <tr id="footer-carrito">
                    <th scope="row" colspan="5" v-if="Object.keys(items).length === 0">Carrito vacío - Comience a comprar!</th>

                    <FooterCarrito />
                </tr>
            </tfoot>
        </table>
    </div>
</template>

<script>
import { computed } from 'vue'
import { useStore } from 'vuex'

import Item from './Item.vue'
import FooterCarrito from './FooterCarrito.vue'

export default {
    components : {
        Item, 
        FooterCarrito
    }, 

    setup() {
        const store = useStore()

        const items = computed(() => store.state.carrito)

        return {items}
    }
}
</script>
