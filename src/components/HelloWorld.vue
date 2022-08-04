<template>
  <v-card>
    <v-card-title>
      Nutrition
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="members"
      :search="search"
    >
    <template v-slot:[`item.activity`]="{ item }">
      <v-chip class="mx-1" v-for="act in item.activity" :key="act" color="gray"
      >
        {{ act }}
      </v-chip>
    </template>
    <template v-slot:[`item.actions`]="{ item }">
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
    </template>
    <template v-slot:no-data>
      <v-btn
        color="primary"
        @click="initialize"
      >
        Reset
      </v-btn>
    </template>
    </v-data-table>
  </v-card>
</template>
<script>
export default {
  data() {
    return {
      search: '',
      headers: [
        {
          text: 'Member Name',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Age', value: 'age' },
        { text: 'Rating', value: 'rating' },
        { text: 'Activities ( last 3 )', value: 'activity' },
        { text: 'Actions', value: 'actions', sortable: false }
      ],
      members:[]
    }
  },

    created () {
      this.initialize()
    },
  methods:{
    initialize(){
      this.members = [
        {
          name: 'john',
          age: 25,
          rating: 3,
          activity: ['cycling','yoga','cardio']
        },
        {
          name: 'brendon',
          age: 23,
          rating: 1,
          activity: ['cycling','swimming','cardio'],
        },
        {
          name: 'axel',
          age: 20,
          rating: 5,
          activity: ['soccer','judo','cardio'],
        },
      ]
    },
    deleteItem(item){
      console.log("delete item function called");
      this.editedIndex = this.members.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialogDelete = true
    }
  }
}
</script>
