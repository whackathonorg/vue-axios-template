<template>
  <div>
    <!-- msg Parameter passed through the parent element -->
    <h1>{{ msg }}</h1>
    <p>Press the button to request data from the yes/no API.</p>
    <!-- dynamic binding to url in data -->
    <img :src="img_url"/>
    <div>
      <!-- dynamic binding to answer in data -->
      <h2>Answer: {{ answer }}</h2>
      <!-- onClick Eventlistener -->
      <a class="button" @click="loadData">PRESS ME!</a>
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Start',
  // "state" of the component, for proper state management for multiple components
  // have a look at vuex
  data () {
    return {
      answer: '',
      img_url: '',
      api_url: 'https://yesno.wtf/api/'
    }
  },
  // Declaration of parameters passed through the parent element
  props: {
    msg: String
  },
  // methods that can be called
  methods: {
    /**
    * Calls the yes/no API with axios and saves that into the data.
    */
    loadData: function() {
      axios.get(this.api_url) // returns a promise
        .then(response => {
          // axios returns a response object, which contains the requested data
          // can be accessed via response.data
          this.answer = response.data.answer
          this.img_url = response.data.image
        }).catch(err => {
          alert('Error while trying to call the api: ' + err)
        })
    }
  },
  // vue-hook that gets called once the component is mounted
  mounted() {
    this.loadData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.button {
  font-weight: 900;
  color: #000;
  border: 2px solid #000;
  border-radius: 0 !important;
  padding: .5rem 3rem;
  height: auto !important;
  font-size: 1.25rem;
  transition: all .2s ease;
  font-size: 12px;
  font-weight: 600;
  line-height: 38px;
  cursor: pointer;
}

.button:hover{
  background-color: white;
}

img {
  height: 300px;
}

</style>
