<template>
<div>
    <table>
        <tr>
            <th>
                title
            </th>
            <th>
                price
            </th>
            <th>
                quantity
            </th>
        </tr>
            <item v-for="row in rows"
                v-bind:key="row.title"
                :post="row"
        />
   </table>
</div>
</template>
<script>
import Item from './Item.vue'

export default {
    props: ['rows'],
    components:{
        Item
    },
}
</script>