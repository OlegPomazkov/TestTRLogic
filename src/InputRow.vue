<template>
  <tr id="inputRow">
    <td class="not-used n"></td>
    <td class="name">
      <input v-model="name" placeholder="Наименование">
    </td>
    <td class="amount">
      <input v-model="amount" placeholder="Количество">      
    </td>
    <td class="price">
      <input v-model="price" placeholder="Цена">
    </td>
    <td class="button">
      <button v-on:click="addNewItem">Добавить</button>
    </td>    
  </tr>
</template>
<!-- _________________________________________________________________________________________ -->
<script>
export default {
  name: 'inputRow',

  data () {
    return {
      name: '',
      amount: '',
      price:''  
    }
  },

  methods:{
    addNewItem: function() {
      this.$emit('newItemAdded', {
        name: this.name, 
        amount: this.amount,
        price: this.price
      })
      this.name = '';
      this.amount = '';
      this.price = '';      
    }
  }  
}
</script>
<!-- _________________________________________________________________________________________ -->
<style>
tr {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  margin-top: 60px;
}

.name input {
  width: 230px;
}

.price input,
.amount input {
  text-align: center;
  font-weight: normal;
  width: 130px;
}

tfoot button {
  background-color: #8f8;
}
</style>
