<template>
  <div class="container">
    <h1>Mobile</h1>
    <router-link to="/" class="btn btn-primary">Back</router-link>
    <form class="mt-2 padding" @submit="formSubmit">
      <div class="form-group w-50">
        <label for="mobile">Number</label>
        <input
          :error-messages="modelstate['PhoneNumber']"
          type="text"
          class="form-control"
          id="mobile"
          placeholder="Enter mobile number"
          v-model="phone"
        />
        <p v-if="modelstate.PhoneNumber">
          <span style="color: red">{{ modelstate.PhoneNumber[0] }}</span>
        </p>
      </div>
      <div class="form-group w-50">
        <label for="amount">Amount</label>
        <input
          type="text"
          class="form-control"
          id="amount"
          placeholder="Enter amount"
        />
        <p v-if="modelstate.Amount">
          <span style="color: red">{{ modelstate.Amount[0] }}</span>
        </p>
      </div>
      <button type="submit" class="btn btn-success mt-2">Pay</button>
    </form>
    <pre>
    {{ output }}
    </pre>
  </div>
</template>
<script>
export default {
  mounted() {
    console.log("Component mounted.");
  },
  data() {
    return {
      modelstate: {},
      phone: "",
      amount: 0,
      output: ""
    };
  },
  methods: {
    formSubmit(e) {
      e.preventDefault();
      let currentObj = this;
      this.axios
        .post("https://localhost:5001/pay/mobile", {
          phoneNumber: this.phone,
          amount: this.amount
        })
        .then(function(response) {
          currentObj.output = response.data;
        })
        .catch(function(error) {
          if (error.response.status == 400) {
            currentObj.modelstate = error.response.data.errors;
          }
          currentObj.output = error.response.data.errors;
          console.log(error.response.data);
        });
    }
  }
};
</script>
