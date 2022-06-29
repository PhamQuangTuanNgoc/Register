<template>
  <div id="app">
    <section class=" gradient-custom">
      <div class="container py-5 h-100">
        <div class="row justify-content-center align-items-center h-100">
          <div class="col-12 col-lg-9 col-xl-7">
            <div class="card shadow-2-strong card-registration" style="border-radius: 15px;">
              <div class="card-body p-4 p-md-5">
                <h3 class="mb-4 pb-2 pb-md-0 mb-md-5">Register</h3>
                <form>

                  <div class="row">
                    <div class="col-md-6 mb-4">

                      <div class="form-outline">
                        <input v-model="firstName" type="text" id="firstName" class="form-control form-control-lg"/>
                        <label class="form-label" for="firstName">UserName</label>
                      </div>

                    </div>
                    <div class="col-md-6 mb-4">

                      <div class="form-outline">
                        <input v-model="password" type="password" id="lastName" class="form-control form-control-lg"/>
                        <label class="form-label" for="lastName">Password</label>
                      </div>

                    </div>
                  </div>

                  <div class="row">
                    <div class="form-outline datepicker w-100">
                      <label class="form-label">Birthday:</label>
                      <select v-on:click="getDay" v-model="getDaySelected" style="padding: 4px" class="form-select"
                              aria-label="Default select example">
                        <option selected>Ngày sinh</option>
                        <option v-for="item2 in day" v-bind:value="item2">{{ item2 }}</option>
                      </select>
                      <select v-on:click="getMonth" v-model="dayByMonth" style="padding: 4px" class="form-select"
                              aria-label="Default select example">
                        <option selected>Tháng sinh</option>
                        <option v-for="(item1) in month" v-bind:index="item1" v-bind:value="item1">{{ item1 }}</option>
                      </select>
                      <select v-on:click="getYear" v-model="getYearSelected" style="padding: 4px" class="form-select"
                              aria-label="Default select example">
                        <option selected>Năm sinh</option>
                        <option v-for="item in year" v-bind:value="item">{{ item }}</option>
                      </select>
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-md-6 mb-4">

                      <h6 class="mb-2 pb-1">Gender: </h6>

                      <div class="form-check form-check-inline">
                        <input v-model="gender" class="form-check-input" type="radio" name="inlineRadioOptions"
                               id="femaleGender"
                               value="nữ" checked/>
                        <label class="form-check-label" for="femaleGender">Female</label>
                      </div>

                      <div class="form-check form-check-inline">
                        <input v-model="gender" class="form-check-input" type="radio" name="inlineRadioOptions"
                               id="maleGender"
                               value="nam"/>
                        <label class="form-check-label" for="maleGender">Male</label>
                      </div>

                      <div class="form-check form-check-inline">
                        <input v-model="gender" class="form-check-input" type="radio" name="inlineRadioOptions"
                               id="otherGender"
                               value="lgbt"/>
                        <label class="form-check-label" for="otherGender">Other</label>
                      </div>

                    </div>
                  </div>
                  <div class="row">
                    <div class="col-md-6 mb-4 pb-2">

                      <div class="form-outline">
                        <input v-model="email" type="email" id="emailAddress" class="form-control form-control-lg"/>
                        <label class="form-label" for="emailAddress">Email</label>
                      </div>

                    </div>
                    <div class="row">
                      <div class="col-md-6 mb-4 pb-2">

                        <div class="form-outline">
                          <input v-on:change="onImageChange" type="file" id="image" class="" value="image"/>
                          <label class="form-label" for="image">Image</label>
                        </div>

                      </div>
                    </div>
                    <div class="col-md-6 mb-4 pb-2">

                      <div class="form-outline">
                        <textarea v-model="note" type="tel" id="phoneNumber" class="form-control form-control-lg"/>
                        <label class="form-label" for="phoneNumber">Note</label>
                      </div>

                    </div>
                  </div>
                  <input type="checkbox" id="PHP" value="PHP" v-model="language">
                  <label for="PHP">PHP</label>
                  <br>
                  <input type="checkbox" id="VUE" value="VUE" v-model="language">
                  <label for="VUE">VUE</label>
                  <br>
                  <input type="checkbox" id="JS" value="JS" v-model="language">
                  <label for="JS">Vue</label>
                  <div class="mt-4 pt-2">
                    <input v-on:click.prevent="printMessage" class="btn btn-primary btn-lg" type="submit"
                           value="Submit"/>
                  </div>

                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      firstName: '',
      password: '',
      email: '',
      gender: '',
      note: '',
      language: [],
      image: [],
      year: [],
      month: [],
      day: [],
      dayByMonth: '',
      getYearSelected: '',
      getDaySelected: ''
    }
  },
  methods: {
    printMessage() {
      let {firstName, password, email, gender, note, language, image} = this;
      console.log(firstName);
      console.log(password);
      console.log(email);
      console.log(gender);
      console.log(note);
      console.log(language);
      console.log(image);
      console.log(this.getDaySelected + '-' + this.dayByMonth + '-' + this.getYearSelected);
    },
    onImageChange(e) {
      let files = e.target.files;
      if (!files.length)
        return;
      this.image = e.target.files[0].name;
    },
    getYear() {
      var result = [];
      for (var from = +1930, to = +2022; from <= to; from++)
        result.push(from);

      this.year = result;
    },
    getMonth() {
      var startDate = "1",
        endDate = "12";

      var result = [];
      for (var from = +startDate, to = +endDate; from <= to; from++)
        result.push(from);

      this.month = result;
    },

    getDay() {
      if (this.dayByMonth == 1) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 2) {
        var result = [];
        for (var from = +1, to = +28; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 2 && this.getYearSelected % 400 == 0) {
        var result = [];
        for (var from = +1, to = +29; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 2 && this.getYearSelected % 4 == 0 && this.getYearSelected % 100 != 0) {
        var result = [];
        for (var from = +1, to = +29; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 3) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 4) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 5) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 6) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 7) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 8) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
      if (this.dayByMonth == 9) {
        var result = [];
        for (var from = +1, to = +31; from <= to; from++)
          result.push(from);
        this.day = result;
      }
    }
  }
}
</script>

<style>
.gradient-custom {
  /* fallback for old browsers */
  background: #f093fb;

  /* Chrome 10-25, Safari 5.1-6 */
  background: -webkit-linear-gradient(to bottom right, rgba(240, 147, 251, 1), rgba(245, 87, 108, 1));

  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  background: linear-gradient(to bottom right, rgba(240, 147, 251, 1), rgba(245, 87, 108, 1))
}

.card-registration .select-input.form-control[readonly]:not([disabled]) {
  font-size: 1rem;
  line-height: 2.15;
  padding-left: .75em;
  padding-right: .75em;
}

.card-registration .select-arrow {
  top: 13px;
}
</style>
