<template>
  <tr>
    <td class="n">
       {{indexData + 1}}
    </td>
    <td class="name">
      <input v-model="nameData" placeholder="Наименование" @change="renewRowData">
    </td>
    <td class="price">
      <input v-model="amountData" placeholder="Количество" @change="renewRowData">      
    </td>
    <td class="amount">
      <input v-model="priceData" placeholder="Цена" @change="renewRowData">
    </td>
    <td class="button">
      <button v-on:click="deleteItem">Удалить</button>
    </td>    
  </tr>
</template>
<!-- _________________________________________________________________________________________ -->
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
<!-- _________________________________________________________________________________________ -->
<style>
tr {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #000;
  font-weight: bold;
}

.name input {
  width: 230px;
}

.price input,
.amount input {
  text-align: center;
  font-weight: bold;
  width: 130px;
}

button {
  background-color: #f88;
}
</style>
