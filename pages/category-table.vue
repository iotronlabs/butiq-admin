<template>
<v-container fluid>
    <v-row>
        <v-col cols = 12 xs = "12" sm = "12" md = "12" lg = "12">
            <v-data-table
            :headers="headers"
            :items="categories"
            sort-by="id"
            class="elevation-1"
            >
                <template v-slot:top>
                    <v-toolbar flat >
                        <v-text-field
                        v-model="search"
                        label="Search"
                        single-line
                        hide-details
                        ></v-text-field>
                    
                        <v-spacer></v-spacer>
                        <v-dialog v-model="dialog" max-width="500px">
                            <template v-slot:activator="{ on }">
                                <v-btn color="primary" dark class="mb-2" v-on="on"><v-icon>add</v-icon>&nbsp;Add Category</v-btn>
                            </template>
                            <v-card>
                                <v-card-title>
                                    <span class="headline">{{ formTitle }}</span>
                                </v-card-title>
                
                                <v-card-text>
                                    <v-container>
                                        <v-row>
                                            <v-col cols="12" sm="6" md="6">
                                            <v-text-field v-model="editedItem.name" label="Name"></v-text-field>
                                            </v-col>
                                            <v-col cols="12" sm="6" md="6">
                                            <v-text-field v-model="editedItem.slug" label="Slug"></v-text-field>
                                            </v-col>
                                            <v-col cols="12" sm="12" md="12">
                                            <v-select
                                            :items="items"
                                            label="Select Parent"
                                            outlined
                                            ></v-select>
                                            </v-col>
                                            
                                        </v-row>
                                    </v-container>
                                </v-card-text>
                
                                <v-card-actions>
                                    <v-spacer></v-spacer>
                                    <v-btn color="blue darken-1" text @click="close">Cancel</v-btn>
                                    <v-btn color="blue darken-1" text @click="save">Save</v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                    </v-toolbar>
                </template>
                <template v-slot:item.action="{ item }">
                    <v-icon
                    small
                    class="mr-2"
                    @click="editItem(item)"
                    >
                    edit
                    </v-icon>
                    <v-icon
                    small
                    @click="deleteItem(item)"
                    >
                    delete
                    </v-icon>
                </template>
                <template v-slot:no-data>
                    <v-btn color="primary" @click="initialize"><v-icon>mdi-backup-restore</v-icon>&nbsp;&nbsp; Reset</v-btn>
                </template>
             </v-data-table>
        </v-col>
    </v-row>
</v-container>
    
</template>

<script>
export default {
    data(){
        return{

            dialog: false,
            search: '',
            items: ['a','b','c','d'],
    headers: [
      {
        text: 'ID',
        align: 'left',
        sortable: false,
        value: 'id',
      },
      { text: 'Name', value: 'name' },
      { text: 'Slug', value: 'slug' },
      { text: 'Parent ID', value: 'pid' },
      { text: 'Actions', value: 'action', sortable: false },
    ],
    categories: [],
    editedIndex: -1,
    editedItem: {
      id: '',
      name: 0,
      slug: 0,
      pid: 0,
      
    },
    defaultItem: {
       id: '',
      name: 0,
      slug: 0,
      pid: 0,
      
    },
        computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Item' : 'Edit Item'
    },
  },

  watch: {
    dialog (val) {
      val || this.close()
    },
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.categories = [
        {
          id : '1',
          name :'a',
          slug :'a',
          pid :'1a',
        },
        {
         id : '2',
          name :'b',
          slug :'b',
          pid :'2a',
        },
        {
         id : '3',
          name :'c',
          slug :'c',
          pid :'3a',
        },
        {
          id : '4',
          name :'d',
          slug :'d',
          pid :'4a',
        },
        
      ]
    },

    editItem (item) {
      this.editedIndex = this.categories.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      const index = this.categories.indexOf(item)
      confirm('Are you sure you want to delete this item?') && this.categories.splice(index, 1)
    },

    close () {
      this.dialog = false
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      }, 300)
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.categories[this.editedIndex], this.editedItem)
      } else {
        this.categories.push(this.editedItem)
      }
      this.close()
    },
  },
        }
        
    }

}
</script>

<style>

</style>
