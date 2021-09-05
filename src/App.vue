<template>
  <article :class="[(this.gender === 'female' ? 'b--pink' : 'b--blue'),'mw5', 'center', 'bg-white', 'br3', 'pa3', 'pa4-ns', 'mv3', 'ba', 'bw2']">
    <div class="tc">
      <img :src="photo" :class="[(this.gender === 'female' ? 'b--pink' : 'b--blue'),'br-100', 'h4', 'w4', 'dib', 'ba', 'bw2', 'pa2']" title="Random User">
      <h1 class="f3 mb2">{{username}}</h1>
      <div :class="[(this.gender === 'female' ? 'b--pink' : 'b--blue'), 'ba', 'b--dashed', 'br-pill', 'bw1']"></div>
      <br>
      <h2 class="f6 fw2 gray mt0">{{phone}}</h2>
      <h2 class="f6 fw2 gray mt0 flex-wrap">{{email}}</h2>
    </div>
  </article>
  <button @click="onGenerate" class="f6 grow no-underline br-pill ph3 pv2 mb2 di bg-white w-25">Generate</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      username: 'Cat',
      phone: 1234567890,
      email: 'lovelycat@gmail.com',
      photo: 'http://tachyons.io/img/avatar_1.jpg',
      gender: 'female'
    }
  },
  methods: {
    async onGenerate(){
      // fetch('https://randomuser.me/api/')
      //   .then(response => response.json())
      //   .then(
      //     (data) => {
      //       this.username = data.results[0].name.first + data.results[0].name.last;
      //       this.phone = data.results[0].phone;
      //       this.email = data.results[0].email;
      //       this.photo = data.results[0].picture.medium;
      //       this.gender = data.results[0].gender;
      //     }
      //   )
      const response = await fetch('https://randomuser.me/api/')
      const { results } = await response.json();
      this.username = results[0].name.first + results[0].name.last;
      this.phone = results[0].phone;
      this.email = results[0].email;
      this.photo = results[0].picture.medium;
      this.gender = results[0].gender;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
