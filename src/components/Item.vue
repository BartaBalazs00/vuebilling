<template>
<tr>
    <td v-if="!edit">{{post.title}}</td>
    <td v-if="!edit">{{post.price}}</td>
    <td v-if="!edit">{{post.quantity}}</td>
    <td v-if="!edit">
        <button @click="Edit">Edit</button>
        <button @click="Delete">X</button>
    </td>
    

    <td v-if="edit"><input type="text" v-model="title"></td>
    <td v-if="edit"><input type="text" v-model="price"></td>
    <td v-if="edit"><input type="text" v-model="quantity"></td>
    <td v-if="edit"><button @click="Save">Save</button></td>
</tr>
</template>

<script>
export default {
    props: ['post'],
    data() {
        return {
            title: this.post.title,
            price: this.post.price,
            quantity: this.post.quantity,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('post-row-changed', {
                original: this.post,
                new: {
                    title: this.title,
                    price: this.price,
                    quantity: this.quantity
                    },
            })
        },
        Delete() {
            
        }
    }
}
</script>

<style>
</style>