<template>
  <div>
    <label>
      <input type="text" v-model="query">
    </label>
    <button @click="$emit('myClick', query)">send request</button>
    <br/>
    <table>
      <caption>Temperature in {{query}}</caption>
      <tr>
        <th v-for='item in this.info'>{{item.dt_txt}}</th>
      </tr>
      <tr>
        <td v-for='item in this.info'>Temp = {{item.main.temp}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      info: '',
      query: ''
    }
  },
  methods: {
  }
}
</script>

<style scoped>
  table {
    width: 1000px;
    border: 1px solid black;
    border-collapse: collapse;
  }

  tr {
    width: 100%;
  }

  th {
    border: 1px solid black;
  }

  td {
    border: 1px solid black;
  }
</style>