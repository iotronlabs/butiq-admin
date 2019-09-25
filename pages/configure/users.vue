<template>
  <v-card
    class="mx-auto mt-10"
    max-width="1000"
  >
      <v-card-title class="align justify-end ">
        <v-flex xs12 sm12 md8 lg8>
            <v-text-field
             v-model="search"
            placeholder="Search"
            >
             </v-text-field>
       </v-flex>
        <v-flex xs6 sm6 md2 lg2>
            <v-btn class="ml-3 error"> Delete </v-btn>
        </v-flex>
        <!-- <v-flex xs6 sm6 md2 lg2>
            <v-btn class="primary" >  Add New </v-btn>
        </v-flex> -->

        <template>
            <v-dialog v-model="dialog"  max-width="1000px" >
                <template v-slot:activator="{ on }">
                    <v-flex xs6 sm6 md2 lg2>  
                     <v-btn color="primary"  v-on="on">Add New</v-btn>
                    </v-flex>
                </template>
                <UserForm />
            </v-dialog>
        </template>

 </v-card-title>
    <v-card>
     <v-data-table
      :headers="headers"
      :items="users"
      :search="search"
     >
     </v-data-table>
  </v-card>

   
  </v-card>
</template>
<script>
import UserForm from "~/components/UserForm"
  export default {
    components:{
        UserForm
    },
    data () {
      return {
        search: '',
        headers: [
          {
            text: 'ID',
            align: 'left',
            sortable: false,
            value: 'id',
          },
          { text: 'Name', value: 'name' },
          { text: 'Email', value: 'email' },
          { text: 'Contact', value: 'contact' },
          
        ],
        users: [
          {
            id:1,
            name:'abc',
            email:'abc',
            contact:234,
          },
          {
            id:2,
            name:'abc',
            email:'bcd',
            contact:234,
          },
          {
            id:3,
            name:'abs',
            email:'cvfg',
            contact:234,
          },
          {
            id:4,
            name:'dfg',
            email:'dfg',
            contact:234,
          },
          {
            id:5,
            name:'xys',
            email:'xys',
            contact:234,
          },
          {
            id:6,
            name:'hjj',
            email:'hjk',
            contact:234,
          },
          
        ],
      }
    },
  }
</script>