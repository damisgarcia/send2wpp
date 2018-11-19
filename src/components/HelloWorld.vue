<template>
  <v-container fill-height>
    <v-layout
      text-xs-center
      fill-height
      justify-center
      wrap
    >      
    <v-flex mb-12>
      <v-form v-model="valid">
        <v-container grid-list-lg>
          <div class="mt-5 mb-4">
            <div class="display-3">Send2WPP</div>
            <p>A maneira mais fácil de conversar no whatsapp sem adicionar contato</p>
          </div>
          <v-layout row wrap justify-center>
            <v-flex xs2>
              <v-text-field
                v-model="countryCode"
                name=""
                label="Country Code"
                :rules="countryCodeRules"
                required
              ></v-text-field>
            </v-flex>
            <v-flex xs8>
              <v-text-field                  
                v-model="phoneNumber"
                label="Phone Number"
                :rules="phoneNumberRules"
                required
              ></v-text-field>
            </v-flex>
          </v-layout>
          <v-layout row justify-center>
            <v-flex xs3>
              <v-btn color="primary" :disabled="!valid" :href="`https://api.whatsapp.com/send?phone=${countryCode}${phoneNumber}&text=Olá`" target="blank" :large="true" :block="true" :round="true">Enviar</v-btn>
            </v-flex>
          </v-layout>
        </v-container>
      </v-form>
    </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      valid: false,
      countryCode: '',
      countryCodeRules: [
        v => !!v || 'Country Code is required'
      ],
      phoneNumber: '',
      phoneNumberRules: [
        v => !!v || 'Phone Number is required'
      ]
    })
  }
</script>

<style>

</style>
