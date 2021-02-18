<template>
  <v-row justify="center">
    <v-dialog
      v-model= "dialog_1"
      persistent
      max-width= "330px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color= "primary"
          dark
          v-bind= "attrs"
          v-on= "on"
        ><v-icon>mdi-menu-down</v-icon>
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class= "headline">Sign Up</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "firstname"
                  :rules= "[rules.required, rules.counter]"
                  :counter= longitud
                  label="First name*"
                  hint="example: Angeles"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "firstname"
                  :rules= "[rules.required, rules.counter]"
                  :counter= longitud
                  label="First name*"
                  hint="example: Angeles"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "lastName1"
                  :rules= "[rules.required, rules.counter]"
                  :counter="20"
                  label="Last name*"
                  hint="example: Sanchez"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "email"
                  :rules= "[rules.required, rules.email]"
                  label="Email*"
                  hint='email@email.com'
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "password_1"
                  :append-icon= "show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules= "[rules.required, rules.min]"
                  :type= "show1 ? 'text' : 'password'"
                  :counter= longitud
                  label= "Password*"
                  hint= "At least 8 characters"
                  @click:append= "show1 = !show1"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  v-model= "password_2"
                  :append-icon= "show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules= "[rules.required, rules.min, rules.comparatePass]"
                  :type= "show1 ? 'text' : 'password'"
                  :counter= longitud
                  label="Password Confirm*"
                  hint= "At least 8 characters"
                  @click:append= "show1 = !show1"
                  
                >
                </v-text-field>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color= "blue darken-1"
            text
            @click= "dialog_1 = false"
          >Close</v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click= "dialog_1 = false"
          >Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
<script>
  export default {
    data: () => ({
      dialog_1:false,
      longitud:20,
      firstname: '',
      lastName1: '',
      email:'',
      password_1: '',
      password_2:'',
      show1: false,
      rules: {
          required: value => !!value || 'Required.',
          counter: value => value.length <= 20 || 'Max '+20+ ' characters',
          email: value => {
            const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
            return pattern.test(value) || 'Invalid e-mail.'
          },
          min: v => v.length >= 8 || 'Min 8 characters',
          comparatePass: value => {
            // https://stackoverflow.com/questions/56642635/how-to-add-password-matching-validation-in-vuetify/56642723
            // if ( v.password_1 === v.password_2){
            //   return 'passwords match'
            // }else{
            //   return 'passwords not match'
            // }


          }
      },
    }),
  }
</script>