<template>
  <form id="data-form" v-on:submit.prevent="submit">
    <div class="row">
      <div class="col-12 form-group">
        <label class="col-form-label col-form-label-lg"
          >Nama Lengkap <span class="text-danger">*</span></label
        >
        <input
          type="text"
          v-model.trim="$v.namalengkap.$model"
          :class="{ 'is-invalid': validationStatus($v.namalengkap) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.namalengkap.required" class="invalid-feedback">
          Nama Lengkap Harus di Isi.
        </div>
      </div>
      <div class="col-12 form-group">
        <label class="col-form-label col-form-label-lg"
          >Alamat <span class="text-danger">*</span></label
        >
        <input
          type="text"
          v-model.trim="$v.alamat.$model"
          :class="{ 'is-invalid': validationStatus($v.alamat) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.alamat.required" class="invalid-feedback">
          Alamat Harus di Isi.
        </div>
      </div>
      <div class="col-12 form-group">
        <label class="col-form-label col-form-label-lg"
          >Nomor Telepon <span class="text-danger">*</span></label
        >
        <input
          type="tel"
          v-model.trim="$v.nomortelepon.$model"
          :class="{ 'is-invalid': validationStatus($v.nomortelepon) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.nomortelepon.required" class="invalid-feedback">
          Nomor Telepon Harus di Isi.
        </div>
        <div v-if="!$v.nomortelepon.minLength" class="invalid-feedback">
          Nomor Telepon Kurang dari 10 Angka.
        </div>
        <div v-if="!$v.nomortelepon.maxLength" class="invalid-feedback">
          Nomor Telepon Lebih dari 15 Angka.
        </div>
      </div>
      <div class="col-12 form-group">
        <label class="col-form-label col-form-label-lg"
          >Email <span class="text-danger">*</span></label
        >
        <input
          type="email"
          v-model.trim="$v.email.$model"
          :class="{ 'is-invalid': validationStatus($v.email) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.email.required" class="invalid-feedback">
          Email Lengkap Harus di Isi.
        </div>
        <div v-if="!$v.email.email" class="invalid-feedback">
          Email Tidak Valid.
        </div>
      </div>
      <div class="col-12 form-group text-center">
        <button class="btn btn-submit btn-lg col-4">Submit</button>
      </div>
    </div>
  </form>
</template>

<script>
import {
  required,
  email,
  minLength,
  maxLength,
} from "vuelidate/lib/validators";

export default {
  name: "AturToko",
  data: function () {
    return {
      namalengkap: "",
      alamat: "",
      nomortelepon: "",
      email: "",
    };
  },
  validations: {
    namalengkap: { required },
    alamat: { required },
    nomortelepon: {
      required,
      minLength: minLength(10),
      maxLength: maxLength(15),
    },
    email: { required, email },
  },

  methods: {
    validationStatus: function (validation) {
      return typeof validation != "undefined" ? validation.$error : false;
    },

    submit: function () {
      this.$v.$touch();
      if (this.$v.$pending || this.$v.$error) return;

      alert("Data Submit");
    },
  },
};
</script>

<style>
.btn-submit {
  background: #53b985;
  color: white;
  margin: 15px;
  font-weight: bold;
}
</style>