<template>
  <center>
    <div class="container mt-3 mb-3 d-flex justify-content-center">
      <div class="card px-3 py-3 alert-primary clearfix">
        <div class="card-body">
        <h6 class="information mt-0">Fill in the form below to add a new VENDOR</h6>

            <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="text" placeholder="Vendor Name" v-model="fullName" required/>
                </div>
              </div>
            </div>

            <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="Datepicker" placeholder="XXX-XXX-XXXX" pattern="^\d{3}-\d{3}-\d{4}$" aria-describedby="phoneHelpBlock" v-model="phone" required/>
                </div>
                <span id="phoneHelpBlock" class="form-text text-danger text-muted">
                    10 digit phone number should be entered with dashes.
                </span>
              </div>
            </div> 

             <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="text" placeholder="Vendor Address" v-model="address" required/>
                </div>
              </div>
            </div>

             <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="text" placeholder="Vendor City" v-model="city" required/>
                </div>
              </div>
            </div>

             <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="text" placeholder="Vendor State" v-model="state" required/>
                </div>
              </div>
            </div>

             <div class="row  mt-3">
              <div class="col-sm-12">
                <div class="form-group">
                  <input class="form-control" type="text" placeholder="Vendor Zip" v-model="zip" required/>
                </div>
              </div>
            </div>

            <div class="control">
              <button class="btn btn-info mt-4" @click.prevent="saveVendor">SAVE</button>
            </div>   

        </div>
      </div>
    </div>
  </center>  
</template>
 
<script>
// import axios
import axios from "axios";
 
export default {
  data() {
    return {
      fullName: "",
      phone: "",
      address: "",
      city: "",
      state: "",
      zip: "",
    };
  },
  methods: {
    async saveVendor() {
      try {
        await axios.post("https://pudcapi.herokuapp.com/vendors", {
          vendor_name: this.fullName,
          vendor_phone: this.phone,
          vendor_address: this.address,
          vendor_city: this.city,
          vendor_state: this.state,
          vendor_zip: this.zip,
        });
        this.$router.push("/vendors");
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style>
    .btn {
        margin-right: 10px;
    }
</style>