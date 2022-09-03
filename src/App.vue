<script>
import contactData from "./contacts.json";
export default {
  name: "App",
  components: {},
  data() {
    const myArray = contactData; //todos los datos
    const contacts = contactData.slice(0, 5); // 5primeros datos
    const myArrayToShow = [];
    let contactId = 0;

    return {
      myArray: myArray,
      contacts: contacts,
      myArrayToShow: myArrayToShow,
      contactId: contactId++,
    };
  },
  computed: {
   
  },
  methods: {
    getRandomInt() {
      return Math.floor(Math.random() * 100) + 5;
    },

    addRandomElem() {
      let randomcontact = this.contacts.splice(5, this.myArray.length - 1);git add .
      this.contacts.unshift(randomcontact[0]);
    },

    created() {
      // const firstFivemyArray = [];
      // for (i = 0; i < 5; i++) {
      //   myArrayToShow.push(myArray.unshift());
      // }
    },
  },
};
</script>

<template>
  <h1>IronContacts</h1>
  <p>{{}}</p>
  <div>
    <table style="width: 100%">
      <thead>
        <tr>
          <th>Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won Oscar</th>
          <th>Won Emmy</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in contacts" :key="item.contactId">
          <td>
            <img :src="item.pictureUrl" alt="contact Image" />
          </td>
          <td>{{ item.name }}</td>
          <td>{{ item.popularity.toFixed(2) }}</td>
          <td>
            <img
              v-if="item.wonOscar"
              src="./assets/trophy.png"
              id="trophy"
              alt=""
            />
          </td>

          <td>
            <img
              v-if="item.wonEmmy"
              src="./assets/trophy.png"
              id="trophy"
              alt=""
            />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <button @click="addRandomElem">Add Random Contact</button>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  width: 100px;
  height: 120px;
}
#trophy {
  width: 80px;
  height: 80px;
}
</style>
