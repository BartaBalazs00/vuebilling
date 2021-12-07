<template>
<div>
    <table>
        <tr>
            <th>
                Title
            </th>
            <th>
                Price
            </th>
            <th>
                Quantity
            </th>
            <th>
                Összérték
            </th>
            <th>
                Operations
            </th>
        </tr>
            <item v-for="row in rows"
                v-bind:key="row.title"
                :post="row"
                @post-row-changed="Changed"
                @post-row-delete="Delete"
        />
        <tr>
            <td></td>
            <td></td>
            <td></td>
            <td>{{rows.price*rows.quantity}}</td>
        </tr>
    
        <newItem :new="row" @post-new="New"/>
        
   </table>
</div>
</template>
<script>
import Item from './Item.vue'
import NewItem from './NewItem.vue'

export default {
    props: ['rows'],
    components:{
        Item,
        NewItem
    },
    methods: {
        Changed(e) {
            this.$emit('post-row-changed', e)
        },
        New(e){
            this.$emit('post-new',e)
        },
        Delete(e){
            this.$emit('post-row-delete', e)
        }
    },
}
</script>