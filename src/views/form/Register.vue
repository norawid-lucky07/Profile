<template>
  <div>
    <CCard>
      <CCardHeader> <strong>Profile </strong></CCardHeader>
      <CCardBody>
        <CRow>
          <CCol sm="2">
            <div class="img-thumbnail img-circle">
              <div style="position: relative; padding: 0; cursor: pointer;">
                <img
                  class="img-circle"
                  style="width: 125px; height: 125px;"
                  src=""
                />
                <span class="img-span">Edit</span>
              </div>
            </div>
          </CCol>
          <CCol sm="4" class="name">
            <label>
              <CRow>
                <strong>Name: Norawid Nara</strong>
              </CRow>
              <CRow>
                User ID: 5931305031
              </CRow>
            </label>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="4">
            <CInput label="Name" v-model="form.name" name="form.name" />
          </CCol>
          <CCol sm="4">
            <CInput
              label="Surename"
              v-model="form.surename"
              name="form.surename"
            />
          </CCol>
          <CCol sm="2">
            <div class="form-group">
              <label class="">Gender</label>
              <select v-model="form.gender" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="gen in genders"
                  v-bind:key="gen.id"
                  v-bind:value="gen.value"
                >
                  {{ gen.text }}
                </option>
              </select>
            </div>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="4">
            <CRow sm="4">
              <CCol sm="4">
                <div class="form-group" placeholder="Select One">
                  <label class="">Day</label>
                  <select v-model="form.day" class="form-control">
                    <option disabled value="">Day</option>
                    <option
                      v-for="day in date.day"
                      v-bind:key="day.BIRTH_ID"
                      v-bind:value="day.BIRTH_DAY"
                    >
                      {{ day.BIRTH_DAY }}
                    </option>
                  </select>
                </div>
              </CCol>
              <CCol sm="4">
                <div class="form-group" placeholder="Select One">
                  <label class="">Month</label>
                  <select v-model="form.month" class="form-control">
                    <option disabled value="">Month</option>
                    <option
                      v-for="month in date.month"
                      v-bind:key="month.BIRTH_ID"
                      v-bind:value="month.BIRTH_MONTH"
                    >
                      {{ month.BIRTH_MONTH }}
                    </option>
                  </select>
                </div>
              </CCol>
              <CCol sm="4">
                <div class="form-group" placeholder="Select One">
                  <label class="">Year</label>
                  <select v-model="form.year" class="form-control">
                    <option disabled value="">Year</option>
                    <option
                      v-for="year in date.year"
                      v-bind:key="year.BIRTH_ID"
                      v-bind:value="year.BIRTH_YEAR"
                    >
                      {{ year.BIRTH_YEAR }}
                    </option>
                  </select>
                </div>
              </CCol>
            </CRow>
          </CCol>
          <CCol sm="4">
            <CInput label="Age" v-model="form.age" />
          </CCol>
          <CCol sm="4">
            <CInput label="Phone Number" v-model="form.phone">
              <template #prepend-content>+66</template>
            </CInput>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="8">
            <div class="form-group">
              <label class="">Country</label>
              <select v-model="form.country" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="coun in countries"
                  v-bind:key="coun.id"
                  v-bind:value="coun.value"
                >
                  {{ coun.text }}
                </option>
              </select>
            </div>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="4">
            <CInput label="Zipcode" v-model="form.zipCode" />
          </CCol>
          <CCol sm="4">
            <div class="form-group" placeholder="Select One">
              <label class="">Province/State</label>
              <select v-model="form.province" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="provin in provinces"
                  v-bind:key="provin.PROVINCE_ID"
                  v-bind:value="provin.PROVINCE_NAME"
                  @input="onSelect(provin.PROVINCE_ID)"
                >
                  {{ provin.PROVINCE_NAME }}
                </option>
              </select>
            </div>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="4">
            <div class="form-group">
              <label class="">District</label>
              <select v-model="form.district" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="dis in districts"
                  v-bind:key="dis.DISTRICT_ID"
                  v-bind:value="dis.DISTRICT_NAME"
                >
                  {{ dis.DISTRICT_NAME }}
                </option>
              </select>
            </div>
          </CCol>
          <CCol sm="4">
            <div class="form-group">
              <label class="">Sub-District</label>
              <select v-model="form.subDis" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="sub in subDistricts"
                  v-bind:key="sub.id"
                  v-bind:value="sub.value"
                >
                  {{ sub.text }}
                </option>
              </select>
            </div>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="8">
            <CInput label="Address" v-model="form.address" />
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="8">
            <div class="form-group">
              <label class="">Occupation</label>
              <select v-model="form.occupation" class="form-control">
                <option disabled value="">Please select one</option>
                <option
                  v-for="occ in occupations"
                  v-bind:key="occ.id"
                  v-bind:value="occ.value"
                >
                  {{ occ.text }}
                </option>
              </select>
            </div>
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="4">
            <CInput label="University" v-model="form.university" />
          </CCol>
          <CCol sm="4">
            <CInput label="Faculty/School" v-model="form.factulty" />
          </CCol>
        </CRow>
        <CRow>
          <CCol sm="8">
            <CInput label="Major" v-model="form.major" />
          </CCol>
        </CRow>
        <div>
          <p>
            <CCol sm="8" style="padding: 10px">
              <CButton color="facebook">
                <CIcon name="cib-facebook"/>
                <span>Facebook</span>
              </CButton>
            </CCol>
            <CCol sm="8">
              <CButton color="google">
                <CIcon name="cib-google" />
                <span>Google</span>
              </CButton>
            </CCol>
            <CButton class="btn btn-danger" style="float: right;">
              Cancel
            </CButton>
            <CButton
              @click="onSubmit"
              class="btn btn-success"
              style="float: right;"
            >
              Submit
            </CButton>
          </p>
        </div>
      </CCardBody>
    </CCard>
  </div>
</template>

<script>
import provinceData from "./json/provinces.json";
import districtData from "./json/districts.json";
import subDisData from "./json/subDistricts.json";
import birthDay from "./json/birthday.json";
export default {
  name: "Registers",
  data() {
    return {
      form: {
        name: "",
        surename: "",
        gender: "",
        day: "",
        month: "",
        year: "",
        age: "",
        phone: "",
        country: "",
        zipCode: "",
        province: "",
        district: "",
        subDis: "",
        address: "",
        occupation: "",
        university: "",
        factulty: "",
        major: "",
      },
      genders: [
        { id: "1", text: "Male", value: "male" },
        { id: "2", text: "Female", value: "female" },
      ],
      date: {
        day: birthDay.day,
        month: birthDay.month,
        year: birthDay.year,
      },
      countries: [{ id: "1", text: "Thailand", value: "thai" }],
      provinces: provinceData,
      districts: districtData,
      subDistricts: [
        { id: "1", text: "Option1", value: "option1" },
        { id: "2", text: "Option2", value: "option2" },
      ],
      occupations: [
        { id: "1", text: "Teacher", value: "teacher" },
        { id: "2", text: "Student", value: "student" },
      ],
    };
  },
  methods: {
    onSubmit() {
      var data = {
        name: this.form.name,
        surename: this.form.surename,
        gender: this.form.gender,
        birth: [this.form.day, this.form.month, this.form.year],
        age: this.form.age,
        phone: this.form.phone,
        country: this.form.country,
        zipCode: this.form.zipCode,
        province: this.form.province,
        district: this.form.district,
        subDis: this.form.subDis,
        address: this.form.address,
        occupation: this.form.occupation,
        university: this.form.university,
        factulty: this.form.factulty,
        major: this.form.major,
      };
      console.log(data);
    },
    onChange(event) {
      console.log(event.target.value);
      console.log("its change!");
    },
  },
  created() {
    console.log("created");
  },
  mounted() {
    console.log("mounted to HTML");
  },
  beforeDestroy() {
    console.log("beforeDestroy");
  },
};
</script>

<style>
.img-circle {
  border-radius: 50%;
}
img.img-circle {
  background: #fff;
}

.img-span {
  left: 0;
  text-align: center;
  width: 100%;
  background: rgb(185, 183, 183);
  bottom: 0;
  padding: 20px 0;
  opacity: 70%;
  position: absolute;
  color: black;
}
.img-thumbnail {
  border-radius: 50%;
  display: inline-block;
  overflow: hidden;
  background: #333;
}
.img-thumbnail > div {
  display: inline-block;
  overflow: hidden;
  height: 125px;
  border: 3px solid #fff;
  -webkit-box-shadow: 0 1px 0 1px #333;
  box-shadow: 0 1px 0 1px #333;
  border-radius: 50%;
}
</style>
