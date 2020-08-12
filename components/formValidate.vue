<template>
  <div style="width:100%;background:RGB(203,213,224);align-content:center">
    <h3 class="pt-4">Test form and validation</h3>
    <b-form
      id="app"
      class="was-validated p-4"
      style="max-width:50%;margin-left:250px"
    >
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="First Name"
        :state="stateName"
        :invalid-feedback="invalidName"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.first"
          type="text"
          required
          placeholder="Please fill first name"
        />
      </b-form-group>
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="Last Name"
        :state="stateLast"
        :invalid-feedback="invalidLast"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.last"
          type="text"
          required
          placeholder="Please fill last name"
        />
      </b-form-group>
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="Email"
        :state="stateEmail"
        :invalid-feedback="invalidEmail"
        label-for="input-3"
      >
        <b-form-input
          id="input-3"
          v-model="form.email"
          type="email"
          required
          placeholder="Please fill email"
        />
      </b-form-group>
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="Password"
        :state="statePassword"
        :invalid-feedback="invalidPassword"
        label-for="input-4"
      >
        <b-form-input
          id="input-4"
          v-model="form.password"
          type="password"
          required
          placeholder="Please fill password"
        />
      </b-form-group>
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="Verify Password"
        :state="verifyPass"
        :invalid-feedback="invalidFeedback"
        label-for="input-5"
      >
        <b-form-input
          id="input-5"
          v-model="form.verify"
          type="password"
          required
          placeholder="Please fill verify password"
        />
      </b-form-group>
      <b-form-group
        label-cols-sm="4"
        label-cols-lg="3"
        label="Gender"
        :state="stateGender"
        :invalid-feedback="invalidGender"
        label-for="input-6"
      >
        <b-form-select id="input-6" v-model="form.gender" :options="options" required></b-form-select>
      </b-form-group>
      <b-button type="button" @click="checkForm" variant="primary">Submit</b-button>
    </b-form>
    <div>
      <pre v-if="validate" style="text-align:left">
        <b>Result:</b>
        First Name: {{form.first}}
        Last Name:{{form.last}}
        Email:{{form.email}}
        Gender:{{form.gender}}
      </pre>
    </div>
  </div>
</template>

<script>
export default {
  name: "formValidate",
  props: {},
  data() {
    return {
      errors: [6],
      form: {
        first: null,
        last: null,
        email: null,
        password: null,
        verify: null,
        gender: null
      },
      options: [
        { value: "male", text: "Male" },
        { value: "female", text: "Female" }
      ],
      validate: false
    };
  },
  computed: {
    stateName() {
      return this.form.first ?  true : false;
    },
    invalidName() {
      return this.form.first ?  '' : "Please fill this field out";
    },
    stateLast() {
      return this.form.last ?  true : false;
    },
    invalidLast() {
      return this.form.last ?  '' : "Please fill this field out";
    },
    stateEmail() {
      return this.form.email ?  true : false;
    },
    invalidEmail() {
      return this.form.email ?  '' : "Please fill this field out";
    },
    statePassword() {
      return this.form.password ?  true : false;
    },
    invalidPassword() {
      return this.form.password ?  '' : "Please fill this field out";
    },
    verifyPass() {
      if (this.form.password == this.form.verify) return true;
      else return false;
    },
    invalidFeedback() {
      if (this.form.password == this.form.verify) {
        return "";
      } else {
        return "Please correct password";
      }
    },
    stateGender() {
      return this.form.gender ?  true : false;
    },
    invalidGender() {
      return this.form.gender ?  '' : "Please fill this field out";
    },
  },
  methods: {
    checkForm() {
      if (
        this.form.first &&
        this.form.last &&
        this.form.email &&
        this.form.password &&
        this.form.verify &&
        this.form.gender
      ) {
        this.validate = true;
      }

      // this.$event.preventDefault();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  size: 8px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.primary {
  color: #42b983;
}
</style>
