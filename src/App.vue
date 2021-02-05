<template>
  <div id="app">
    <div v-for="person in persons" :key="person.id">
      <Person :firstName="person.name"></Person>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Person from './components/Person.vue';
import axios from "axios";

// PersonInterface heisst PersonInterface, 
// da es das Objekt Person schon gibt und IPerson mag ESLint nicht.
interface PersonInterface {
  id: number;
  imageUrl: string;
  firstName: string;
  lastName: string;
  email: string;
  contactNumber: string;
  age: number;
  dob: string;
  salary: number;
  address: string;
}

async function getPersons<P>(uri: string): Promise<P> {
  return await axios.get(uri);
}

@Component({
  components: {
    Person,
  },
})
export default class App extends Vue {
  persons = getPersons<PersonInterface[]>("https://hub.dummyapis.com/employee?noofRecords=10&idStarts=1001");

}
</script>