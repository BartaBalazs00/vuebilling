<template>
  <div id="app">
    <tablazat :rows="rows" @post-row-changed="Changed" @post-new="New" @post-row-delete="Delete"/>
    
  </div>
</template>

<script>
import Tablazat from './components/Tablazat.vue'


export default {
  name: 'App',
  components: {
    Tablazat
  },
  data() {
    return {
      rows: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  },
  methods: {
      Changed(e) {
        this.rows.map(function (row) {
          if (row.title != e.original.title || row.price != e.original.price || row.quantity != e.original.quantity) {
            return row
          }
          row.title = e.new.title,
          row.price = e.new.price,
          row.quantity = e.new.quantity
          return row
        })
      },
      New(e){
        this.rows.push(e.new)
      },
      Delete(e){
          this.rows.splice(this.rows.indexOf(e.original), 1);
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table{
  margin-left: auto;
  margin-right: auto;
}
</style>
