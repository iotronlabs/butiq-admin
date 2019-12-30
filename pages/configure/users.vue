<template>
  <v-card
    class="mx-auto mt-10"
    max-width="1000"
  >
      <v-card-title class="align justify-end ">
        <v-row>
        <v-col cols="12" md="6">
            <v-text-field
            outlined
            v-model="search"
            placeholder="Search"
            >
            </v-text-field>
        </v-col>
        <v-col cols="6" offset-md="1" md="2">
         
              <v-dialog v-model="dialog"  max-width="1000px" >
                  <template v-slot:activator="{ on }">
                    
                    <v-btn color="primary"  v-on="on"><v-icon>add</v-icon>&nbsp;&nbsp;Add New</v-btn>
                      
                  </template>
                  <UserForm />
              </v-dialog>
          
        </v-col>
        <v-col cols="6" md="2">
            <v-btn class="ml-3 error"><v-icon>delete</v-icon>&nbsp;&nbsp; Delete </v-btn>
        </v-col>
        </v-row>

 </v-card-title>
    <v-card flat class="px-6">
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