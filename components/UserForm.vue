<template>
    <v-layout wrap class=" align-center justify-center">
    <v-flex xs12 sm12 md9 lg9>
      <v-card class="mx-auto pa-10" light max-width="800">

         <v-card-title class="align-center justify-center display-1 mb-2">User Form</v-card-title>
         <v-form
            ref="form"
            v-model="active"
        >
        <!-- name -->
           <v-text-field
            v-model="name"
            :rules="nameRules"
            label="Name"
            required
            outlined
            ></v-text-field>
         <!-- email -->
            <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
            outlined
            ></v-text-field>
        <!-- gender -->
        <span > Gender </span>
         <v-radio-group v-model="radioGroup" outlined>
            <v-radio
             label="Male"
             ></v-radio>
              <v-radio
             label="Female"
             ></v-radio>
              <v-radio
             label="Others"
             ></v-radio>
        </v-radio-group>


        <!-- contact number -->
            <v-text-field
            v-model="contact"
            label="Contact Number"
            required
            outlined
            ></v-text-field>

        <!-- address -->
             <v-text-field
            v-model="address"
            label="Address"
            outlined
            ></v-text-field>

        <!-- city -->
            <v-text-field
            v-model="city"
            label="City"
            outlined
            ></v-text-field>
        
        <!-- pin -->
            <v-text-field
            v-model="pin"
            label="PIN"
            outlined
            ></v-text-field>

         <!--submit  -->
            <div class="text-center">
            <v-btn rounded  large class="primary mr-3"> Submit </v-btn>
            <v-btn color="error" @click="reset" large rounded>  Clear  </v-btn>
            </div>
           
        </v-form>
      

      </v-card>
      </v-flex>
    </v-layout>   
</template>

<script>
  export default {
    data: () => ({
      active: true,
      name: '',
       nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 30) || 'Name must be less than 30 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      radioGroup:'',
      contact:'',
      address:'',
      city:'',
      pin:'',
      
    }),

    methods: {
      reset () {
        this.$refs.form.reset()
      },
  },
}
</script>