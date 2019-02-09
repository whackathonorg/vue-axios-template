<template>
  <div class="home">
    <div class="title">
      <div class="container">
      <!-- title parameter passed through the parent element -->
      <h1>{{ title }}</h1>
      <p>Press the button to request data from the yes/no API.</p>
      </div>

      <img class="wave" src="./../assets/images/wavewhite.svg">
    </div>
    
    <div class="answer">
      <div class="container">
        <!-- dynamic binding to url in data -->
        <img :src="img_url"/>

        <!-- dynamic binding to answer in data -->
        <h2>Answer: {{ answer }}</h2>
        
        <!-- onClick Eventlistener -->
        <a class="button" @click="loadData">Press me</a>
      </div>
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
    title: String
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
.title {
  background: #5865FF;
  color: #ffffff;
}
.title h1 {
  margin: 0 0 .5rem 0;
  font-size: 3.5rem;
}
.title p {
  font-size: 1.25rem;
}
.button {
  color: #ffffff;
  font-weight: 600;
  background: #5865FF;
  border-radius: .25rem;
  display: inline-block;
  padding: 1rem 2rem;
  text-decoration: none;
  box-shadow: 0 .25rem 0 rgba(0,0,0, 0.1);
  outline: none;
  border: none;
  font-size: 1rem;
  transition: all 0.2s ease;
  margin: 1rem 0 3rem 0;
  cursor: pointer;
}
.button:hover{
  transform: scale(1.1);
}
.wave {
  margin-top: 10vw;
  margin-bottom: -1rem;
  width: 100%;
}
.answer {
  text-align: center;
  background: #ffffff;
  color: #5865FF;
}
.answer img {
  max-height: 300px;
  max-width: 100%;
  margin: 1rem auto;
  border-radius: .5rem;
}
.answer h2 {
  font-size: 2.5rem;
}
</style>
