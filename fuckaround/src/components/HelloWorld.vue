<template>
  <div class="hello">
    <h1>{{msg}}</h1>
    <p>{{date}}</p>
    <p>{{time}}</p>
    <p>The temperature is: {{temperature}} degrees celcuis</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      msg: 'Welcome to you death',
      date: 'date',
      time: 'time',
      temperature: 'laoding...'
    }
  }, 
  beforeMount() {
    setInterval(this.updateDate, 1000);
    this.getWeatherData();

  },
  onload() {
    this.getWeatherData();
  },
  methods: {
    updateDate() {
      now=new Date();
      this.time=mytime();
      this.date = date;
    },
    getWeatherData() {
      axios.get('http://api.weatherunlocked.com/api/current/au.4169?app_id=f9036d25&app_key=209242d2e09f96ce4db61ae73e5e2ad7').then(response => {
        console.log(response);
        this.temperature = response.data.temp_c;});
      }

  }
}
function mytime(){
  var now = new Date();
  var time = now.getHours()+":" + now.getMinutes()+":"+ now.getSeconds();
  return time;
}
var now = new Date();
var date = [now.getDate(), now.getMonth(), now.getFullYear()];

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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