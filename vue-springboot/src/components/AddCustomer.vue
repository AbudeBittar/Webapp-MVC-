<template>
  <div class="submitform">
    <div v-if="!submitted">
        <div class="form-group">
          <label for="name">Name</label>
          <input type="text" class="form-control" id="name" required v-model="customer.name" name="name">
        </div>

        <div class="form-group">
          <label for="streetName">Street Name</label>
          <input type="text" class="form-control" id="streetName" required v-model="customer.streetName" name="streetName">
        </div>
        
         <div class="form-group">
          <label for="streetNumber">Street Number</label>
          <input type="number" class="form-control" id="streetNumber" required v-model="customer.streetNumber" name="streetNumber">
        </div>
    
        <div class="form-group">
          <label for="phoneNumber">Phone Number</label>
          <input type="number" class="form-control" id="phoneNumber" required v-model="customer.phoneNumber" name="phoneNumber">
        </div>

         <div class="form-group">
          <label for="email">E-Mail</label>
          <input type="text" class="form-control" id="email" required v-model="customer.email" name="email">
        </div>
    
        <button v-on:click="saveCustomer" class="btn btn-success">Submit</button>
    </div>
    
    <div v-else>
      <h4>You submitted successfully!</h4>
      <button class="btn btn-success" v-on:click="newCustomer">Add</button>
    </div>
  </div>
</template>

<script>
import http from "../http-common";

export default {
  name: "add-customer",
  data() {
    return {
      customer: {
        id: 0,
        name: ""
      },
      submitted: false
    };
  },
  methods: {
    /* eslint-disable no-console */
    saveCustomer() {
      var data = {
        name: this.customer.name,
        streetName: this.customer.streetName,
        streetNumber: this.customer.streetNumber,
        phoneNumber: this.customer.phoneNumber,
        email: this.customer.email

      };

      http
        .post("/customer", data)
        .then(response => {
          this.customer.id = response.data.id;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });

      this.submitted = true;
    },
    newCustomer() {
      this.submitted = false;
      this.customer = {};
    }
    /* eslint-enable no-console */
  }
};
</script>

<style>
.submitform {
  max-width: 300px;
  margin: auto;
}
</style>
