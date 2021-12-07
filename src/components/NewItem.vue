<template>
<tr>
    <td><input type="text" v-model="title"></td>
    <td><input type="text" v-model="price"></td>
    <td><input type="text" v-model="quantity"></td>
    <td><button @click="Add">Add</button></td>
</tr>
</template>

<script>
export default {
    props: ['new'],
    data() {
        return {
            title: this.new.title,
            price: this.new.price,
            quantity: this.new.quantity,
        }
    },
    methods: {
        Add() {
            this.$emit('post-new', {
                original: this.new,
                new: {
                    title: this.title,
                    price: this.price,
                    quantity: this.quantity
                    },
            })
        }
    }
}
</script>

<style>
</style>