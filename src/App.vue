<template>
  <div id="app">
    <h1>hello ~</h1>
    <input type="text" v-model="message" />
    <button @click="sendMsg">hoho</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import { Client } from '@stomp/stompjs';
import { Stomp } from '@stomp/stompjs';

export default {
  name: 'App',
  // components: {
  //   HelloWorld
  // },
  data(){
    return {
      message: ''
    }
  },
  mounted() {

    const client = Stomp.client('ws://192.168.1.118:15674/ws');
    client.activate();

    // client.subscribe(destination: string, callback: messageCallbackType, headers: StompHeaders)
  },
  methods: {
    sendMsg() {
      const req = new XMLHttpRequest()
      req.open('get', `http://192.168.1.118:3000/send/${this.message}`, true)
      req.send();
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
