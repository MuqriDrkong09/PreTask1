<template>
  <form class="2xl:w-full max-h-lg m-8" @submit.prevent="false">
    <fieldset>
      <h2 class="text-3xl text-left font-bold">Search Invoice</h2><br>

      <div>
        <Radio v-model="enquiry" label="General Enquiry" type="radio" />

        <div>
          <Radio v-model="match" label="Exact Match" type="radio" />
          <!-- <div class="input-errors" v-for="(error, index) of v$.form.match.$errors" :key="index">
            <div class="error-msg text-left text-sm text-red-500">This field is required.</div>
          </div> -->
        </div>
      </div>
      <br>

      <div class="flex-wrap -mx-3 mb-6 grid grid-cols-1 md:grid-cols-3">

        <div class="mb-6 md:mb-8">
          <BaseInput v-model="v$.form.inv_number.$model" label="Invoice Number" type="text" />
          <div class="input-errors" v-for="(error, index) of v$.form.inv_number.$errors" :key="index">
            <div class="error-msg text-left text-sm text-red-500 px-3">This field is required.</div>
          </div>
        </div>

        <div class="flex flex-row mb-6 md:mb-8">
          <div class="w-1/2">
            <BaseInput1 v-model="v$.form.inv_date.$model" label="Invoice Date" type="date" />
            <div class="input-errors" v-for="(error, index) of v$.form.inv_date.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">Please select the exact date.</div>
            </div>
          </div>

          <div class="w-1/2">
            <BaseInput2 v-model="v$.form.inv_type.$model" label="Invoice type" type="select" />
            <div class="input-errors" v-for="(error, index) of v$.form.inv_type.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">This field need to be selected.</div>
            </div>
          </div>
        </div>

        <div class="w-1/2 mb-6 md:mb-8">
          <div>
            <BaseInput v-model="v$.form.bank_ref_number.$model" label="Bank Reference Number" type="text" />
            <div class="input-errors" v-for="(error, index) of v$.form.bank_ref_number.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">This field is required.</div>
            </div>
          </div>
        </div>

        <div class="flex flex-row mb-6 md:mb-8">
          <div class="w-1/2">
            <BaseInput v-model="v$.form.inv_amount.$model" label="Invoice Amount" type="text" />
            <div class="input-errors" v-for="(error, index) of v$.form.inv_amount.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">This field is required.</div>
            </div>
          </div>

          <div class="w-1/2">
            <BaseInput1 v-model="v$.form.inv_record_date.$model" label="Invoice Record Date" type="date" />
            <div class="input-errors" v-for="(error, index) of v$.form.inv_record_date.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">Please select the exact date.</div>
            </div>
          </div>
        </div>

        <div class="mb-6 md:mb-8">
          <div>
            <BaseInput v-model="v$.form.brn.$model" label="BRN" type="text" />
            <div class="input-errors" v-for="(error, index) of v$.form.brn.$errors" :key="index">
              <div class="error-msg text-left text-sm text-red-500 px-3">This field is required.</div>
            </div>
          </div>
        </div>

        <div>
          <button class="bg-blue-700 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg m-4 w-44 h-12"
            @click="reset">
            Reset
          </button>
          <button class="bg-blue-700 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg m-4 w-44 h-12"
            @click="submit">
            Search
          </button>
        </div>

      </div><br><br>

    </fieldset>
  </form>
</template>
  
<script>
import BaseInput from './ReuseComponents/BaseInput.vue';
import BaseInput1 from './ReuseComponents/BaseInput1.vue';
import BaseInput2 from './ReuseComponents/BaseInput2.vue';
import Radio from './ReuseComponents/Radio.vue';

import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'

export default {
  setup() {
    return { v$: useVuelidate() }
  },

  data() {
    return {
      form: {
        // enquiry: "",
        // match: "",
        inv_number: "",
        inv_date: "",
        inv_type: "",
        bank_ref_number: "",
        inv_amount: "",
        inv_record_date: "",
        brn: ""
      },
    };
  },
  components: { BaseInput, BaseInput1, BaseInput2, Radio },

  validations() {
    return {
      form: {
        // enquiry: {
        //   required
        // },
        // match: {
        //   required
        // },
        inv_number: {
          required
        },
        inv_date: {
          required
        },
        inv_type: {
          required
        },
        bank_ref_number: {
          required
        },
        inv_amount: {
          required
        },
        inv_record_date: {
          required
        },
        brn: {
          required
        }
      },
    }
  },
  methods: {
    submit() {
      //console.log("Success")
      //const result = this.v$.$validate()
      this.v$.$validate()
      //const error = this.v$.$error
      if (this.v$.$error) {
        alert("Form failed validation")
      } else {
        alert("Form successfully submitted.")
        this.form = null
      }
    },
    reset() {
      this.form = null
    }
  }
}
</script>
  