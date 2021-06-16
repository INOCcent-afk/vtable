<template>
  <div class="shadow-2xl rounded-lg custom-maxwidth overflow-auto mx-5 z-50">
    <div class="flex flex-col custom-maxheight">
      <table class="custom-width">
        <thead class="sticky top-0 py-6 ">
          <tr class="justify-between">
            <th
              v-for="personCateg in people[0].columns"
              :key="personCateg.key"
              class="relative px-6 py-6 font-medium text-left text-xs  uppercase tracking-wider cursor-pointer bg-purple-50 text-purple-700 hover:bg-purple-100 transition-all duration-700"
            >
              <div class="flex items-center select-none">
                <p class="">
                  {{ personCateg.title }}
                </p>
                <div v-if="personCateg.sortable" @click="toggleDropdown">
                  <MenuIcon class=" w-5 h-5 ml-5" />
                  <SortingDropdown
                    @noSort="noSort(personCateg.title)"
                    @sortAscending="sortAscending(personCateg.title)"
                    @sortDescending="sortDescending(personCateg.title)"
                    v-if="sortingDropdown"
                  />
                </div>
              </div>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="person in people[0].rows"
            :key="person.id"
            class="bg-white group border-b hover:bg-gray-50"
          >
            <PersonData
              :name="person.name"
              :surname="person.surname"
              :age="person.age"
              :city="person.city"
              :address="person.address"
              :flag="person.flag"
            />
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.custom-width {
  width: 1400px;
}
.custom-maxwidth {
  max-width: 1400px;
}

.custom-maxheight {
  max-height: 600px;
}
.inActive {
  display: none;
}
.action {
  display: block !important;
}

/*
 ::-webkit-scrollbar {
  width: 5px;
  height: 5px;
  border-radius: 5px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: #333;
  border-radius: 10px;
}
::-webkit-scrollbar-corner {
  background: transparent;
}
 */
</style>

<script>
import PersonData from "../components/PersonData.vue";

import SortingDropdown from "../components/SortingDropdown.vue";
import { MenuIcon } from "@heroicons/vue/solid";
import { ref } from "@vue/reactivity";

export default {
  name: "Datatable",
  setup() {
    const sortingDropdown = ref(false);

    const toggleDropdown = () => {
      sortingDropdown.value = !sortingDropdown.value;
    };
    const noSort = () => {
      console.log(people[0].rows);
    };

    const sortAscending = (param) => {
      people[0].rows.sort((a, b) =>
        a[checkCol(param)] > b[checkCol(param)] ? 1 : -1
      );
    };

    const sortDescending = (param) => {
      people[0].rows.sort((a, b) =>
        a[checkCol(param)] < b[checkCol(param)] ? 1 : -1
      );
    };

    const checkCol = (param) => {
      if (param === "Your Name") {
        return "name";
      }
      if (param === "Your Surname") {
        return "surname";
      }
      if (param === "Your age") {
        return "age";
      }
    };
    return {
      people,
      toggleDropdown,
      sortingDropdown,
      noSort,
      sortAscending,
      sortDescending,
    };
  },
  components: {
    PersonData,
    MenuIcon,
    SortingDropdown,
  },
};

const people = [
  {
    columns: [
      {
        title: "Your Name",
        key: "name",
        sortable: true,
      },
      {
        title: "Your Surname",
        key: "surname",
        sortable: true,
      },
      {
        title: "Your age",
        key: "age",
        sortable: true,
      },
      {
        title: "Your city",
        key: "city",
        sortable: false,
      },
      {
        title: "Address",
        key: "address",
        sortable: false,
      },
    ],
    rows: [
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Colin",
        surname: "Cooper",
        age: 1,
        city: "London",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Ruben",
        surname: "Rooper",
        age: 2,
        city: "Madrid",
        flag: "🏁",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
      {
        name: "Dave",
        surname: "Iooper",
        age: 3,
        city: "Manila",
        flag: "🚩",
        address:
          "Cecilia Chapman 711-2880 Nulla St. Mankato Mississippi 96522 (257) 563-7401",
      },
    ],
  },
];
</script>
