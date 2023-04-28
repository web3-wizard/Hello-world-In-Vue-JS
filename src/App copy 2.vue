<template>
  <h1>Methods in Vue JS</h1>
  <h3>{{ greeting() }}</h3>
  <h3>Calling Add(): {{ add(3, 6, 9) }}</h3>
  <hr />
  <h2>{{ name }}</h2>
  <button v-on:click="name = 'Ironman'">Change Name</button>
  <div>
    <h3>{{ count }}</h3>
    <button v-on:click="count += 1">Increment</button>
    <button v-on:click="count -= 1">Decrement</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Spiderman",
      count: 0,
    };
  },
  methods: {
    add(a, b, c) {
      return a + b + c;
    },
    greeting() {
      return "Hello Dev People!";
    },
  },
};
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

.danger {
  color: red;
  font-weight: bold;
}

.success {
  color: green;
  font-style: italic;
}
</style>
