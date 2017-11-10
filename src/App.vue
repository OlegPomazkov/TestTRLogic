<template>
  <div id="app">
    <h5> Накладная </h5>

    <table>
    	<thead>
    		<tr>
    			<th>№</th>
    			<th>Наименование</th>
    			<th>Количество</th>
    			<th>Цена</th>
    		</tr>
    	</thead>
    	<input-row v-on:newItemAdded="addNewItem"></input-row>
        <tfoot>
        	<tr>
    			<td colspan="3">ИТОГО</td>
    			<td>111</td>
    		</tr>
        </tfoot>
    </table>

  </div>
</template>

<script>
import row from './SimpleRow.vue'
import inputRow from './InputRow.vue'
import dataRow from './DataRow.vue'

export default {	
  components: {
    'my-row': row,
    'data-row': dataRow,
    'input-row': inputRow
  }, 
  name: 'app',
  data () {
    return {
      rowsData: []
    }
  },

  methods: {
    addNewItem: function (obj) {
      obj.index = this.rowsData.lendth	
      this.rowsData.push(obj)
      console.log(this.rowsData)
    }
  }
}
</script>

<style>
#app {
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
