<template>
  <v-stepper v-model="e1" class="ma-2">
    <v-stepper-header>
      <v-stepper-step :complete="e1 > 1" step="1">Product Details</v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step :complete="e1 > 2" step="2">Variations</v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3"> Category</v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card  class="mb-12">
             <v-form >
                <v-container fluid >
                    <v-row class="ma-4">
                        <v-col cols="12"  >
                            <v-text-field
                                v-model="name"
                                label="Name"
                                outlined
                            ></v-text-field>
                        </v-col>
                         <v-col cols="12"  >
                            <v-text-field
                                v-model="slug"
                                label="Slug"
                                outlined
                            ></v-text-field>
                        </v-col>
                        <v-col cols="12" >
                            
                                    <v-color-picker  outlined class="" hide-inputs hide-canvas></v-color-picker>
                              
                        </v-col>
                         <v-col cols="12"  >
                            <v-text-field
                                v-model="price"
                                label="price"
                                outlined
                            ></v-text-field>
                        </v-col>
                         <v-col cols="12" >
                            <v-textarea
                            v-model="description"
                            label="Description"
                            outlined
                            ></v-textarea>
                        </v-col>
                        <v-col cols="12" md="6" lg="6">
                              <v-file-input
                             
                                label="Image 1"
                                outlined
                                show-size
                                multiple
                                chips
                                prepend-icon="mdi-camera"
                            ></v-file-input>
                        </v-col>
                         <v-col cols="12" md="6" lg="6">
                              <v-file-input
                                
                                label="Image 2"
                                outlined
                                show-size
                                multiple
                                chip
                                prepend-icon="mdi-camera"
                             ></v-file-input>
                        
                        </v-col>
                        <v-col cols="12" md="6" lg="6">
                              <v-file-input
                                
                                label="Image 3"
                                outlined
                                show-size
                                multiple
                                chip
                                prepend-icon="mdi-camera"
                            ></v-file-input>
                        </v-col>
                        <v-col cols="12" md="6" lg="6">
                              <v-file-input
                                
                                label="Image 4"
                                outlined
                                show-size
                                multiple
                                chip
                                prepend-icon="mdi-camera"
                            ></v-file-input>
                        </v-col>
                    </v-row>
                </v-container>
             </v-form>
          </v-card>

        <v-btn color="primary" @click="e1 = 2">Add Variations </v-btn>
        <v-btn text>Cancel</v-btn>
      </v-stepper-content>

      <v-stepper-content step="2">
        <v-card class="mb-12 mt-2" v-for="i in n" :key="i">
            <v-form >
                <v-container  >
                    <v-row class="mx-2">
                        <v-col cols="10"   >
                            <v-text-field
                                v-model="variation_type"
                                label="Variation Type"
                               outlined
                            ></v-text-field>
                        </v-col>
                        <v-col cols="1">
                            <v-btn fab @click="n=n+1">
                               <v-icon>mdi-plus</v-icon>
                            </v-btn>

                        </v-col>

                    </v-row>
                    <v-row class="mx-2" v-for="j in m" :key="j" >
                        <v-col cols="1"></v-col>
                        <v-col cols="10" md="3" lg="3" >
                            <v-text-field
                                v-model="variation_name"
                                label="Name"
                               outlined
                            ></v-text-field>
                        </v-col>
                        <v-col cols="1" class="hidden-md-and-up"></v-col>
                        <v-col  cols="10" md="3" lg="3" >
                            <v-text-field
                                v-model="variation_price"
                                label="Price"
                                outlined
                            ></v-text-field>
                        </v-col>
                        <v-col cols="1" class="hidden-md-and-up"></v-col>
                        <v-col  cols="10" md="3" lg="3">
                            <v-text-field
                                v-model="variation_stock"
                                label="Stock"
                                outlined
                            ></v-text-field>
                        </v-col>
                        <v-col cols="5" class="hidden-md-and-up"></v-col>
                        <v-col cols="1">
                            <v-btn fab @click="m=m+1" small>
                               <v-icon>mdi-plus</v-icon>
                            </v-btn>

                        </v-col>


                    </v-row>
                </v-container>
            </v-form>
        
        </v-card>

        <v-btn color="primary" @click="e1 = 3">Add Category</v-btn>
        <v-btn text @click="e1 = 1">Back</v-btn>
      </v-stepper-content>

      <v-stepper-content step="3">
        <v-card class="mx-auto">
            <v-container>
                <v-row align="center">
                    <v-col cols="12">
                        <v-select
                            v-model="category"
                            :items="categories"
                            clearable
                            chips
                            label="Categories"
                            multiple
                        ></v-select>
                    </v-col>
                </v-row>
            </v-container>
        </v-card>

        <v-btn
          color="primary"
          @click="e1 = 1"
          class="my-10"
        >
          Save
        </v-btn>

        <v-btn text @click="e1 = 2" >Back</v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>
<script>
  export default {
    data () {
      return {
        e1: 0,
        name:'',
        slug:'',
        price:'',
        description:'',
        n:1,
        m:1,
        variation_type:'',
        variation_name:'',
        variation_price:'',
        variation_stock:'',
        category:[],
        categories: ['Men', 'Women', 'Art and Craft', 'Accessories'],
        
      }
    },
  }
</script>