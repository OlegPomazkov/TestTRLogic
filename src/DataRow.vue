<template>
  <tr>
    <td>
       {{indexData + 1}}
    </td>
    <td>
      <input v-model="nameData" placeholder="Введите наименование" @change="renewRowData">
    </td>
    <td>
      <input v-model="amountData" placeholder="Введите количество" @change="renewRowData">      
    </td>
    <td>
      <input v-model="priceData" placeholder="Введите цену" @change="renewRowData">
    </td>
    <td>
      <button v-on:click="deleteItem">Удалить</button>
    </td>    
  </tr>
</template>

<script>
export default {
  name: 'dataRow',
  props: {
    rowData: Object
  },

  data () {

    return {
      indexData: +this.rowData.index,
      nameData: this.rowData.name,
      amountData: +this.rowData.amount,
      priceData: +this.rowData.price
    }
  },  

  methods:{
    deleteItem: function() {
      this.$emit('deleteItem', +this.indexData)
    },
    renewRowData: function(e) {
      console.log('Data changed to ----> ', e.target.value, this.priceData)
      var newDataObj = {
        index: this.indexData,
        name:this.nameData,
        amount: this.amountData,
        price: this.priceData
      } 
      this.$emit('rowDataChanged', newDataObj)
    }
  }  
}
</script>

<style>
#row {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
