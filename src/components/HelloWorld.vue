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
    <template v-slot:activity="{ item }">
      <v-chip color="green"
      >
        {{ item.activity }}
      </v-chip>
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
      ],
      members: [
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
      ],
    }
  },
}
</script>
