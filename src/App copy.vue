<template>
  <div>Hello {{ name }}</div>
  <div v-text="language"></div>
  <p>Hello {{ name }}, How r you doing? <span v-text="language"></span></p>
  <h1 v-html="msg" v-bind:id="headingId"></h1>
  <Button v-bind:disabled="isDisabled" onclick="alert('Here i am')"
    >Click Me</Button
  >
  <h2 class="underline">Underline Text</h2>
  <h2 v-bind:class="status">Status for compilation</h2>
  <h2 v-bind:class="isError ? ['danger', 'underline'] : 'success'">
    Error in Code
  </h2>
  <h1 v-bind:class="{ danger: isError, success: !isError, underline: isError }">
    Object Conditional Rendering
  </h1>

  <h3
    v-bind:style="{
      color: highlightColor,
      fontSize: headerSize + 'px',
      padding: '10px',
    }"
  >
    Inline Style Binding
  </h3>

  <h3 v-bind:style="headerStyleObject">Style Object Binding</h3>

  <div class="container">
    <h2 v-if="num === 0">The Num is Zero.</h2>
    <h2 v-else-if="num < 0" class="danger">The Num is Negetive!</h2>
    <h2 v-else-if="num > 0" class="success">The Num is Positive.</h2>
    <h2 v-else>Not a Number!</h2>

    <template v-if="display">
      <h3>Rahul</h3>
      <h3>Web3 Wizard</h3>
      <h3>Vue Js</h3>
    </template>

    <h2 v-show="showElement">Using V-show</h2>
  </div>

  <h2 v-for="(name, index) in names" :key="name">{{ index }} -> {{ name }}</h2>
  <h2 v-for="name in fullnames" :key="name.first">
    {{ name.first }} {{ name.last }}
  </h2>

  <h3 v-for="(value, key) in myinfo" :key="value">{{ key }} : {{ value }}</h3>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Spiderman",
      language: "VueJs",
      msg: "<u>Welcome to my blog!</u>",
      headingId: "heading",
      isDisabled: true,
      status: "success",
      isError: true,
      highlightColor: "orange",
      headerSize: 32,
      headerStyleObject: {
        color: "orange",
        fontSize: "32px",
        padding: "10px",
      },
      num: 7,
      display: true,
      showElement: false,
      names: ["Ladakh", "Manali", "Darjeeling"],
      fullnames: [
        { first: "Captain", last: "America" },
        { first: "Iron", last: "Man" },
        { first: "Dr", last: "Strange" },
      ],
      myinfo: {
        name: "Rahul Dey",
        github: "web3-wizard",
        language: "Vue 3",
      },
    };
  },
};
</script>

<style>
.container {
  border: 2px solid orchid;
  padding: 10px;
  margin: 10px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
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
