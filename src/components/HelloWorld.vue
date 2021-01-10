<template>
  <v-container class="pt-6">
    <v-row>
      <v-col>
        <p class="display-1 font-weight-bold mb-3">Skills List</p>
        <p class="subheading font-weight-regular">
          Here's where you can see the available skills and the hosts who are
          willing to teach them.
        </p>
        <v-data-table
          v-model="selectedRows"
          :headers="headers"
          :items="filteredTableData"
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
          <v-form netlify @submit.prevent="handleSubmit" name="session-request">
            <input type="hidden" name="form-name" value="session-request" />
            <v-text-field
              v-model="formFields.parentName"
              outlined
              type="text"
              label="Parent/Guardian Name"
            />
            <v-text-field
              v-model="formFields.parentEmail"
              outlined
              type="email"
              label="Parent/Guardian Email"
            />
            <v-text-field
              v-model="formFields.childName"
              outlined
              type="text"
              label="Child's Name"
            />
            <v-textarea v-model="formFields.notes" outlined label="Notes" />
            <h2 class="text-h6 pb-2">Sessions Selected:</h2>
            <ol v-if="selectedRows.length" class="mb-4">
              <li v-for="item in selectedRows" :key="item.id">
                {{ item.Subject }}
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
function encode(data) {
  return Object.keys(data)
    .map((key) => encodeURIComponent(key) + "=" + encodeURIComponent(data[key]))
    .join("&");
}

export default {
  name: "HelloWorld",
  data: () => ({
    search: "",
    formFields: {
      parentName: "",
      parentEmail: "",
      childName: "",
      notes: "",
    },
    selectedRows: [],
    headers: [
      {
        text: "Subject",
        align: "start",
        value: "Subject",
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
        Ages: "All",
      },
      {
        id: 2,
        Subject: "Italian",
        Ages: "All",
      },
      {
        id: 3,
        Subject: "History",
        Ages: "All",
      },
      {
        id: 44,
        Subject: "Philosophy",
        Ages: "All",
      },
      {
        id: 4,
        Subject: "Basic Spanish",
        Ages: "All",
      },
      {
        id: 5,
        Subject: "Basic German",
        Ages: "All",
      },
      {
        id: 6,
        Subject: "Misc",
        Ages: "All",
      },
      {
        id: 7,
        Subject: "English",
        Ages: "Teens",
      },
      {
        id: 8,
        Subject: "Literature",
        Ages: "Teens",
      },
      {
        id: 9,
        Subject: "English literature",
        Ages: "Teens",
      },
      {
        id: 10,
        Subject: "French",
        Ages: "All",
      },
      {
        id: 11,
        Subject: "English literature",
        Ages: "Teens",
      },
      {
        id: 12,
        Subject: "Politics",
        Ages: "Teens",
      },
      {
        id: 13,
        Subject: "Scienece",
        Ages: "Teens",
      },
      {
        id: 14,
        Subject: "Global affairs",
        Ages: "Teens",
      },
      {
        id: 15,
        Subject: "French",
        Ages: "All",
      },
      {
        id: 16,
        Subject: "Maths (SATs)",
        Ages: "Teens",
      },
      {
        id: 17,
        Subject: "English",
        Ages: "Teens",
      },
      {
        id: 18,
        Subject: "World affairs",
        Ages: "Teens",
      },
      {
        id: 19,
        Subject: "Story time",
        Ages: "Tots",
      },
      {
        id: 20,
        Subject: "Piano singalong",
        Ages: "Tots",
      },
      {
        id: 21,
        Subject: "English (TEFL)",
        Ages: "Teens",
      },
      {
        id: 22,
        Subject: "Englsh (GCSE)",
        Ages: "Teens",
      },
      {
        id: 23,
        Subject: "Maths (GCSE)",
        Ages: "Teens",
      },
      {
        id: 24,
        Subject: "Misc",
        Ages: "All",
      },
      {
        id: 25,
        Subject: "Spanish (incl history and LatAm)",
        Ages: "All",
      },
      {
        id: 26,
        Subject: "German",
        Ages: "All",
      },
      {
        id: 27,
        Subject: "History (20th c and 10th c)",
        Ages: "Teens",
      },
      {
        id: 28,
        Subject: "Pensions/personal finance",
        Ages: "Teens",
      },
      {
        id: 29,
        Subject: "Gen homework",
        Ages: "Younger",
      },
      {
        id: 30,
        Subject: "Tutoring",
        Ages: "All",
      },
      {
        id: 31,
        Subject: "Politics (British/American)",
        Ages: "All",
      },
      {
        id: 32,
        Subject: "Misc",
        Ages: "All",
      },
      {
        id: 33,
        Subject: "English",
        Ages: "All",
      },
      {
        id: 34,
        Subject: "History",
        Ages: "All",
      },
      {
        id: 35,
        Subject: "Economics",
        Ages: "All",
      },
      {
        id: 36,
        Subject: "Russian",
        Ages: "All",
      },
      {
        id: 37,
        Subject: "French",
        Ages: "All",
      },
      {
        id: 38,
        Subject: "Mandarin",
        Ages: "All",
      },
      {
        id: 39,
        Subject: "German",
        Ages: "All",
      },
      {
        id: 40,
        Subject: "Russian",
        Ages: "All",
      },
      {
        id: 41,
        Subject: "French",
        Ages: "All",
      },
      {
        id: 42,
        Subject: "Latin",
        Ages: "All",
      },
      {
        id: 43,
        Subject: "Greek",
        Ages: "All",
      },
    ],
  }),
  computed: {
    filteredTableData() {
      const finalData = [];
      this.tableData.forEach((item) => {
        if (
          !finalData.find((subject) => {
            return (
              subject.Subject === item.Subject && subject.Ages === item.Ages
            );
          })
        ) {
          finalData.push(item);
        }
      });
      return finalData;
    },
  },
  methods: {
    handleSubmit(event) {
      fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: encode({
          "form-name": event.target.getAttribute("name"),
          ...this.formFields,
          subjects: this.selectedRows
            .map((item) => `${item.Subject} (${item.Ages})`)
            .join(", ") || 'None chosen',
        }),
      })
        .then(() => console.log("thank you"))
        .catch((error) => console.log(error));
    },
  },
};
</script>

<style lang="scss" scoped>
.table {
  border: 1px solid rgba(0, 0, 0, 0.2);
}
</style>
