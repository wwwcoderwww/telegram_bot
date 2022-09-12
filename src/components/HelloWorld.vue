<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      {{JSON.stringify(tg.initData)}}
      {{JSON.stringify(tg.initDataUnsafe)}}
    </p>
    <ul>
      <li v-for="(chat, key) in chats" :key="key">{{chat}}</li>
    </ul>
    <p class="wrap-chat">
      <textarea name="chat" v-model="text"></textarea>
      <button @click="addChat">Add message</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      chats: [],
      text: '',
      tg: {}
    }
  },
  methods: {
    addChat() {
      this.chats.push(this.text)
      this.text = ''
    }
  },
  mounted() {
    // props are exposed on `this`
    // let ss = "dsa";
    this.tg = window.Telegram.WebApp;
    console.log(this.tg)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
button {
  margin-left: 16px;
  height: 58px;
  padding: 17px;
}
.wrap-chat {
  display: flex;
  justify-content: center;
}
ul {
  display: flex;
  justify-content: center;
  flex-direction: column;
}
</style>
