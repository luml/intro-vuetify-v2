<template>
  <v-vontainer>
    <v-row class="mx-auto mt-5">
      <v-col>
        <h1>Sign up</h1>
        <v-form>
          <v-text-field label="Email" type="email"></v-text-field>
          <v-autocomplete label="Which browser do you use?" :items="browsers"></v-autocomplete>
          <v-file-input label="Attach profile"></v-file-input>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-text-field label="Birthday" v-model="birthday" readonly></v-text-field>
          <v-checkbox label="Agree to terms & conditions"></v-checkbox>
          <v-btn type="submit" color="primary">submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-vontainer>
</template>

<script>
export default {
  data: () => ({
    browsers: ["Chrome", "Firefox", "Safari", "Brave"],
    birthday: ""
  })
};
</script>