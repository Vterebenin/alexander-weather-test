<template>
  <div>
    <my-input @myClick="onClick($event)"></my-input>
    <my-chart></my-chart>
  </div>
</template>

<script>
import MyInput from './components/Input'
import MyChart from './components/Chart'
import axios from 'axios'

export default {
  components: {
    MyInput,
    MyChart
  },
  methods: {
    onClick (query) {
      axios
        .get(`https://cors-anywhere.herokuapp.com/api.openweathermap.org/data/2.5/forecast?q=${query}&appid=ad628c3ff34d34a2909a06ce888926bd`)
        .then((response) => {
          this.info = response.data.list
          console.log(this.info)
          let massWeather = []
          let massTemp = []

          for (const key in this.info) {
            massWeather.push(this.info[key].dt_txt)
            massTemp.push(this.info[key].main.temp)
          }
          this.renderChart(massWeather, massTemp)
        })
    }
  }
}
</script>>