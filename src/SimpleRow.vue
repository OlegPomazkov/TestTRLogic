<template>
  <div id="row">
    <span>
      <input v-bind:value="msg" v-on:input="updateValue($event.target.value)">
    </span>
<!--    <p>{{ msg }}</p> -->
  </div>
</template>

<script>
export default {
  props: {
    rowData: Object
  },
  name: 'row',
  data () {
    return {
      msg: this.rowData.a  
    }
  },
  methods:{
    updateValue: function(value) {
      this.$emit('valueChanged', {newValue: value})
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
