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
            <p>{{$t('description')}}</p>
          </div>
          <v-layout row wrap align-center justify-center>
            <v-flex sm2 xs3>
              <v-text-field
                v-model="countryCode"
                name="countryCode"
                :label="$t('countryCodeLabel')"
                :rules="countryCodeRules"
                :mask="'+##'"
                required
              ></v-text-field>
            </v-flex>
            <v-flex sm8>
              <v-text-field                  
                v-model="phoneNumber"
                :label="$t('phoneNumberLabel')"
                :autofocus="true"
                :rules="phoneNumberRules"
                :mask="$t('phoneMask')"
                required
              ></v-text-field>
            </v-flex>
          </v-layout>
          <v-layout row justify-center>
            <v-flex sm4 xs10>
              <v-btn color="primary" :disabled="!valid" :href="`https://api.whatsapp.com/send?phone=${countryCode}${phoneNumber}&text=${$t('message')}`" target="blank" :large="true" :block="true" :round="true">
                {{ $t('send') }}
              </v-btn>
            </v-flex>
          </v-layout>
        </v-container>
      </v-form>
    </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import { required, minLength  } from 'vuelidate/lib/validators'

  export default {
    data: () => ({
      valid: false,
      requiredMessage: '',
      countryCode: '',
      countryCodeRules: [],
      phoneNumber: '',
      phoneNumberRules: [],
    }),
    beforeMount(){
      this.countryCode = this.$i18n.t('countryCode')
      
      this.countryCodeRules = [
        (v) => required(v) || this.$i18n.t('validations.required')
      ]

      this.phoneNumberRules = [
        (v) => required(v) || this.$i18n.t('validations.required')
      ]
    }
  }
</script>