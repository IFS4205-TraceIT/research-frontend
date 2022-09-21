<script setup lang="ts">
const { useApi } = useAuth();
const { data: records, refresh } = await useApi("/api/researchs");
records.value = [
  {
    dob: "2021-01-01",
    gender: "M",
    postal_code: "asdasd",
    list_of_vaccines: "asdasd",
    last_close_contact: "asdasd",
    last_infected_date: "asdsada",
    total_infection: "asdasdasdsa",
    total_close_contact_as_infected: "asdasdasda",
    total_close_contact_with_infected: "12j013j2h1h912",
  },
];
</script>
<template>
  <div class="container flex w-full mx-auto my-4">
    <div class="overflow-x-auto w-full relative shadow-md sm:rounded-lg">
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <caption
          class="p-5 text-lg font-semibold text-left text-gray-900 bg-white dark:text-white dark:bg-gray-800"
        >
          Researcher DB
          <div class="py-4">
            <div class="relative mt-1">
              <div
                class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none"
              >
                <svg
                  class="w-5 h-5 text-gray-500 dark:text-gray-400"
                  aria-hidden="true"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    fill-rule="evenodd"
                    d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                    clip-rule="evenodd"
                  ></path>
                </svg>
              </div>
              <input
                id="table-search"
                type="input"
                class="block p-2 pl-10 w-80 text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                placeholder="Search for items"
              />
            </div>
          </div>
        </caption>
        <thead
          class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400"
        >
          <tr>
            <th scope="col" class="py-3 px-6">Date of Birth</th>
            <th scope="col" class="py-3 px-6">Gender</th>
            <th scope="col" class="py-3 px-6">Postal Code</th>
            <th scope="col" class="py-3 px-6">List of vaccines</th>
            <th scope="col" class="py-3 px-6">Latest close contact</th>
            <th scope="col" class="py-3 px-6">Latest infected date</th>
            <th scope="col" class="py-3 px-6">Total infection</th>
            <th scope="col" class="py-3 px-6">
              Total close contact as infected
            </th>
            <th scope="col" class="py-3 px-6">
              Total close contact with infected
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(record, index) in records"
            class="bg-white border-b dark:bg-gray-800 dark:border-gray-700"
          >
            <td class="py-4 px-6">{{ record.dob }}</td>
            <td class="py-4 px-6">{{ record.gender }}</td>
            <td class="py-4 px-6">{{ record.postal_code }}</td>
            <td class="py-4 px-6">{{ record.list_of_vaccines }}</td>
            <td class="py-4 px-6">{{ record.last_close_contact }}</td>
            <td class="py-4 px-6">{{ record.last_infected_date }}</td>
            <td class="py-4 px-6">{{ record.total_infection }}</td>
            <td class="py-4 px-6">
              {{ record.total_close_contact_as_infected }}
            </td>
            <td class="py-4 px-6">
              {{ record.total_close_contact_with_infected }}
            </td>
          </tr>
        </tbody>
      </table>
      <div
        v-if="records && (records as Array<any>).length === 0"
        class="text-center p-4 dark:bg-gray-800"
      >
        No records found
      </div>
    </div>
  </div>
</template>
