<template>
  <v-form v-model="valid">
    <v-container>
      <v-row class="d-flex justify-center mb-6">
        
        <v-col cols="10" md="6">
          <v-text-field 
            v-model="firstname"
            :rules="nameRules"
            :counter="20"
            label="First name"
            required
          ></v-text-field>
        </v-col>

        <v-col cols="10" md="6">
          <v-text-field
            v-model="lastname"
            :rules="nameRules"
            :counter="20"
            label="Last name"
            required
          ></v-text-field>
        </v-col>

        <v-col cols="10" md="6">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>

        <v-col cols="10" md="6">
          <v-text-field
            v-model="password"
            :counter="15"
            label="Password"
            required
            type="password"
          ></v-text-field>
        </v-col>
        
        <v-col cols="10" md="12">
          <v-btn
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="validate"
          >
             Submit
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>
<script>
  export default {
    data: () => ({
      valid: false,
      firstname: '',
      lastname: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => v.length <= 20 || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
    }),
    methods: {
      validate(){
          if(this.email == 'qwerty@gmail.com' && this.password === '1234' ){
            console.log('Correct')
          }
          else{
            alert('No valid herejkabsbjbcfksabcjBSCBik')
          }
      }
    },
  }
</script>
