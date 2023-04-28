<template>
  <h2>Job Application</h2>
  <div>
    <form @submit.prevent="submitForm">
      <div>
        <label for="name">Name</label>
        <input
          type="text"
          name="name"
          id="name"
          v-model.trim="formValues.name"
        />
      </div>

      <div>
        <label for="age">Age : </label>
        <input
          type="number"
          name="age"
          id="age"
          v-model.number="formValues.age"
          @keyup.enter="checkAge"
        />
      </div>

      <div>
        <label for="profile">Profile Summery</label>
        <textarea
          name="profile"
          id="profile"
          v-model.trim.lazy="formValues.profileSummery"
        />
      </div>

      <div>
        <label for="country">Country</label>
        <select name="country" id="country" v-model="formValues.country">
          <option value="" selected>Select an option</option>
          <option value="india">India</option>
          <option value="uk">UK</option>
          <option value="usa">USA</option>
        </select>
      </div>

      <div>
        <label for="jobLocation">Job Location</label>
        <select
          name="jobLocation"
          multiple
          id="jobLocation"
          v-model="formValues.jobLocation"
        >
          <option value="india">India</option>
          <option value="uk">UK</option>
          <option value="usa">USA</option>
        </select>
      </div>

      <div>
        <input
          type="checkbox"
          name="remoteWork"
          id="remoteWork"
          v-model="formValues.remoteWork"
        />
        <label for="remotework">Open to remote work?</label>
      </div>

      <div>
        <label>Skill Set : </label>
        <input
          type="checkbox"
          value="html"
          id="html"
          v-model="formValues.skillSets"
        />
        <label for="html">HTML</label>
        <input
          type="checkbox"
          value="css"
          id="css"
          v-model="formValues.skillSets"
        />
        <label for="css">CSS</label>
        <input
          type="checkbox"
          value="javascript"
          id="javascript"
          v-model="formValues.skillSets"
        />
        <label for="javascript">Javascript</label>
      </div>

      <div>
        <label>Year Of Exprience : </label>
        <input
          type="radio"
          value="0-2"
          id="0-2"
          v-model="formValues.yearOfExprience"
        />
        <label for="0-2">0-2</label>
        <input
          type="radio"
          value="3-5"
          id="3-5"
          v-model="formValues.yearOfExprience"
        />
        <label for="3-5">3-5</label>
        <input
          type="radio"
          value="6-10"
          id="6-10"
          v-model="formValues.yearOfExprience"
        />
        <label for="6-10">6-10</label>
        <input
          type="radio"
          value="10+"
          id="10+"
          v-model="formValues.yearOfExprience"
        />
        <label for="10+">10+</label>
      </div>

      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>

  <div>
    <pre>{{ JSON.stringify(formValues, null, 2) }}</pre>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      formValues: {
        name: "",
        age: null,
        profileSummery: "",
        country: "",
        jobLocation: [],
        remoteWork: false,
        skillSets: [],
        yearOfExprience: "",
      },
    };
  },
  methods: {
    submitForm() {
      console.log(this.formValues);
    },
    checkAge() {
      if (this.formValues.age < 18) {
        alert("You are not eligible!");
      }
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
