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
        />
    
        <newItem :new="rows" @post-new="New"/>
        
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
        /*New(){
            this.$emit('post-new', e)
        }*/
    },
}
</script>