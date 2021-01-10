<template>
  <v-container class="pt-6">
    <v-row>
      <v-col>
        <p class="display-1 font-weight-bold mb-3">Skills List</p>
        <p class="subheading font-weight-regular">
          Here's where you can see the available skills and the hosts who are willing to teach them.
        </p>
        <v-data-table
          v-model="selectedRows"
          :headers="headers"
          :items="tableData"
          item-key="id"
          class="elevation-2 pa-1"
          :search="search"
          sort-by="Subject"
          show-select
          hide-default-footer
          disable-pagination
        >
          <template v-slot:top>
            <v-text-field
              v-model="search"
              label="Search by host, subject, or ages"
              class="mx-4"
            ></v-text-field>
          </template>
        </v-data-table>
      </v-col>
      <v-col class="mb-4">
        <p class="display-1 font-weight-bold mb-3">Session Request Form</p>
        <p class="subheading font-weight-regular">
          Fill out this form to request a session for your child.
        </p>
        <v-card class="pa-4 elevation-2">
          <v-form @submit.prevent="handleSubmit">
            <v-text-field outlined type="text" label="Parent/Guardian Name" />
            <v-text-field outlined type="email" label="Parent/Guardian Email" />
            <v-text-field outlined type="text" label="Child's Name" />
            <v-textarea outlined label="Notes" />
            <h2 class="text-h6 pb-2">Sessions Selected:</h2>
            <ol v-if="selectedRows.length" class="mb-4">
              <li v-for="item in selectedRows" :key="item.id">
                {{ item.Subject }} with {{ item.Host }}
              </li>
            </ol>
            <p v-else>
              None. Check one or more items in the skills list table to request
              a specific session.
            </p>
            <v-btn color="success" class="d-block ml-auto mr-0" type="submit">
              <span v-if="selectedRows.length < 2">Request Session</span>
              <span v-else>Request These Sessions</span>
            </v-btn>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    search: "",
    selectedRows: [],
    headers: [
      {
        text: "Subject",
        align: "start",
        value: "Subject",
      },
      {
        text: "Host",
        align: "start",
        value: "Host",
      },
      {
        text: "Ages",
        align: "start",
        value: "Ages",
      },
    ],
    tableData: [
      {
        id: 1,
        Subject: "French",
        Host: "Renee Kaplan",
        Ages: "All",
      },
      {
        id: 2,
        Subject: "Italian",
        Host: "Renee Kaplan",
        Ages: "All",
      },
      {
        id: 3,
        Subject: "History",
        Host: "Sara Germano",
        Ages: "All",
      },
      {
        id: 44,
        Subject: "Philosophy",
        Host: "Sara Germano",
        Ages: "All",
      },
      {
        id: 4,
        Subject: "Basic Spanish",
        Host: "Sara Germano",
        Ages: "All",
      },
      {
        id: 5,
        Subject: "Basic German",
        Host: "Sara Germano",
        Ages: "All",
      },
      {
        id: 6,
        Subject: "Misc",
        Host: "Brooke Masters",
        Ages: "All",
      },
      {
        id: 7,
        Subject: "English",
        Host: "Sarah Provan",
        Ages: "Teens",
      },
      {
        id: 8,
        Subject: "Literature",
        Host: "Saran Provan",
        Ages: "Teens",
      },
      {
        id: 9,
        Subject: "English literature",
        Host: "Judith Evans",
        Ages: "Teens",
      },
      {
        id: 10,
        Subject: "French",
        Host: "Adrienne Klasa",
        Ages: "All",
      },
      {
        id: 11,
        Subject: "English literature",
        Host: "Adrienne Klasa",
        Ages: "Teens",
      },
      {
        id: 12,
        Subject: "Politics",
        Host: "Adrienne Klasa",
        Ages: "Teens",
      },
      {
        id: 13,
        Subject: "Scienece",
        Host: "Adrienne Klasa",
        Ages: "Teens",
      },
      {
        id: 14,
        Subject: "Global affairs",
        Host: "Adrienne Klasa",
        Ages: "Teens",
      },
      {
        id: 15,
        Subject: "French",
        Host: "Rosalind Sykes",
        Ages: "All",
      },
      {
        id: 16,
        Subject: "Maths (SATs)",
        Host: "Joe Rennison",
        Ages: "Teens",
      },
      {
        id: 17,
        Subject: "English",
        Host: "Joe Rennison",
        Ages: "Teens",
      },
      {
        id: 18,
        Subject: "World affairs",
        Host: "Carol Major",
        Ages: "Teens",
      },
      {
        id: 19,
        Subject: "Story time",
        Host: "Iseult Fitzgerland",
        Ages: "Tots",
      },
      {
        id: 20,
        Subject: "Piano singalong",
        Host: "Claer Barrett",
        Ages: "Tots",
      },
      {
        id: 21,
        Subject: "English (TEFL)",
        Host: "John Aglionby",
        Ages: "Teens",
      },
      {
        id: 22,
        Subject: "Englsh (GCSE)",
        Host: "John Aglionby",
        Ages: "Teens",
      },
      {
        id: 23,
        Subject: "Maths (GCSE)",
        Host: "John Aglionby",
        Ages: "Teens",
      },
      {
        id: 24,
        Subject: "Misc",
        Host: "Niki Blasina",
        Ages: "All",
      },
      {
        id: 25,
        Subject: "Spanish (incl history and LatAm)",
        Host: "Peter Chapman",
        Ages: "All",
      },
      {
        id: 26,
        Subject: "German",
        Host: "Peter Chapman",
        Ages: "All",
      },
      {
        id: 27,
        Subject: "History (20th c and 10th c)",
        Host: "Peter Chapman",
        Ages: "Teens",
      },
      {
        id: 28,
        Subject: "Pensions/personal finance",
        Host: "Peter Chapman",
        Ages: "Teens",
      },
      {
        id: 29,
        Subject: "Gen homework",
        Host: "Emily Goldberg",
        Ages: "Younger",
      },
      {
        id: 30,
        Subject: "Tutoring",
        Host: "James Fontanella-Khan",
        Ages: "All",
      },
      {
        id: 31,
        Subject: "Politics (British/American)",
        Host: "Kiran Stacey",
        Ages: "All",
      },
      {
        id: 32,
        Subject: "Misc",
        Host: "Greg Meyer",
        Ages: "All",
      },
      {
        id: 33,
        Subject: "English",
        Host: "Myles McCormick",
        Ages: "All",
      },
      {
        id: 34,
        Subject: "History",
        Host: "Myles McCormick",
        Ages: "All",
      },
      {
        id: 35,
        Subject: "Economics",
        Host: "Myles McCormick",
        Ages: "All",
      },
      {
        id: 36,
        Subject: "Russian",
        Host: "Leyla Boulton",
        Ages: "All",
      },
      {
        id: 37,
        Subject: "French",
        Host: "Leyla Boulton",
        Ages: "All",
      },
      {
        id: 38,
        Subject: "Mandarin",
        Host: "Naomi Rovnik",
        Ages: "All",
      },
      {
        id: 39,
        Subject: "German",
        Host: "Guy Chazan",
        Ages: "All",
      },
      {
        id: 40,
        Subject: "Russian",
        Host: "Guy Chazan",
        Ages: "All",
      },
      {
        id: 41,
        Subject: "French",
        Host: "Jemima Kelly",
        Ages: "All",
      },
      {
        id: 42,
        Subject: "Latin",
        Host: "Josh Spero",
        Ages: "All",
      },
      {
        id: 43,
        Subject: "Greek",
        Host: "Josh Spero",
        Ages: "All",
      },
    ],
  }),
  methods: {
    handleSubmit(event) {
      console.log("handle submit", event);
    },
  },
};
</script>

<style lang="scss" scoped>
.table {
  border: 1px solid rgba(0, 0, 0, 0.2);
}
</style>
