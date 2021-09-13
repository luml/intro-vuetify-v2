<template>
  <v-vontainer>
    <v-row class="mx-auto mt-5">
      <v-col>
        <h1>Sign up</h1>
        <v-form ref="signUpFrom" v-model="formValidity">
          <v-text-field v-model="email" :rules="emailRules" label="Email" type="email" required></v-text-field>
          <v-autocomplete label="Which browser do you use?" :items="browsers"></v-autocomplete>
          <v-file-input label="Attach profile"></v-file-input>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-text-field label="Birthday" v-model="birthday" readonly></v-text-field>
          <v-checkbox v-model="agreeToTerms" :rules="agreeToTermsRules" label="Agree to terms & conditions"></v-checkbox>
          <v-btn type="submit" color="primary" class="mr-4" :disabled="!formValidity">submit</v-btn>
          <v-btn @click="validateForm" class="mr-4" color="warning">Validate Form</v-btn>
          <v-btn color="warning" @click="resetValidation" class="mr-4">Reset Validation</v-btn>
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-vontainer>
</template>

<script>
export default {
  data: () => ({
    email: '',
    emailRules: [
      value => !!value || 'Email is required',
      value => value.indexOf('@') !== 0 || 'Email should have a username',
      value => value.includes('@') || 'Email should include @ symbol',
      value => value.indexOf('.') - value.indexOf('@') > 1 || 'Email should have a valid domain.',
      value => value.indexOf('.') <= value.length - 3 || 'Email should have a valid domain extension'
    ],
    agreeToTermsRules: [
      value => !!value || 'You must agree to all terms to continue to sign up an account!'
    ],
    agreeToTerms: false,
    browsers: ["Chrome", "Firefox", "Safari", "Brave"], 
    birthday: "",
    formValidity: false
  }),
  methods: {
    resetValidation() {
      this.$refs.signUpFrom.resetValidation()
    },
    resetForm() {
      this.$refs.signUpFrom.reset()
    },
    validateForm() {
      this.$refs.signUpFrom.validate()
    }
  }
};
</script>