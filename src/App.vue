<template>
  <h1>Computed Properties</h1>
  <hr />

  <h3>Get Total Method : {{ getTotal() }}</h3>
  <h3>Total Computed : {{ total }}</h3>
  <hr />

  <input type="text" name="country" id="country" v-model="country" />
  <hr />
  <template v-for="item in items" :key="item.id">
    <h5 v-if="item.price > 1000">{{ item.name }} {{ item.price }}</h5>
  </template>
  <h4 v-for="item in expensiveItens" :key="item.id">
    {{ item.name }} {{ item.price }}
  </h4>
  <hr />

  <h2>{{ fullName }}, you are nice!</h2>
  <button @click="changeName">Chnage Name</button>
  <hr />

  <h1>Volume Tracker (0-20) - Watch</h1>
  <h3>Current Volume - {{ volume }}</h3>
  <button @click="volume += 2">Increase</button>
  <button @click="volume -= 2">Decrease</button>
  <hr />

  <h1>Imediate & Deep Watch</h1>
  <input type="text" name="movie" id="movie" v-model="movie" />
  <br />
  <input type="text" v-model="movieInfo.title" placeholder="movie title" />
  <input type="text" v-model="movieInfo.actor" placeholder="movie actor" />
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      items: [
        {
          id: 1,
          name: "phone",
          price: 13000,
        },
        {
          id: 2,
          name: "laptop",
          price: 35000,
        },
        {
          id: 3,
          name: "mouse",
          price: 700,
        },
      ],
      country: "",
      firstName: "Spider",
      lastName: "Man",
      volume: 0,
      movie: "ironman",
      movieInfo: {
        title: "",
        actor: "",
      },
    };
  },
  methods: {
    getTotal() {
      console.log("Get Total Method Call");
      return this.items.reduce((total, curr) => (total += curr.price), 0);
    },
    changeName() {
      this.fullName = "Iron Man";
    },
  },
  computed: {
    total() {
      console.log("Total Computed Call");
      return this.items.reduce((total, curr) => (total += curr.price), 0);
    },
    expensiveItens() {
      return this.items.filter((item) => item.price > 1000);
    },
    fullName: {
      get() {
        return `${this.firstName} ${this.lastName}`;
      },
      set(value) {
        const names = value.split(" ");
        this.firstName = names[0];
        this.lastName = names[1];
      },
    },
  },
  watch: {
    volume(newValue, oldValue) {
      if (newValue > 20) {
        alert("Max Volume!");
        this.volume = oldValue;
      }
      if (newValue < 0) {
        alert("Min Volume!");
        this.volume = oldValue;
      }
      if (newValue > oldValue && newValue === 16) {
        alert(
          "Listing to a high volume for a long time may damage your hearing!"
        );
      }
    },
    movie: {
      handler(newValue) {
        console.log(`Calling Api for movie: ${newValue}`);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log(
          `Calling Api for movie title= ${newValue.title} & actor= ${newValue.actor}`
        );
      },
      deep: true,
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
  margin-top: 6px;
}
</style>
