<template>
  <section class="container">
    <user-data :first-name='firstName' :last-name='lastName'></user-data>
    <h2>{{ userName }}</h2>
    <button @click='setAge'>Change Age</button>
    <div>
      <input type='text' placeholder='First Name' v-model='firstName'>
      <input type='text' placeholder='Last Name' v-model='lastNameInput'>
      <button @click='setLastName'> Set Last Name</button>
    </div>
  </section>
</template>

<script>
import { ref, computed, watch, provide } from 'vue';
import UserData from '@/components/UserData.vue';

export default {
  components:{
    UserData
  },
  setup(){
    // const uName = ref('Samantha');
    const firstName = ref('')
    const lastName = ref('')
    const lastNameInput = ref(null)
    const uAge = ref(19);
    // const user = ref({
    //   name: 'Samantha',
    //   age: 19
    // })

    // const isLoading = computed(() => {
    //   return productsLoading.value || servicesLoading.value || mapLoading.value
    // })

    provide('userAge', uAge)

    const uName = computed(() => {
      return firstName.value + ' ' + lastName.value;
    })

    watch([uAge, uName], function (newValues, oldValues){
      console.log ('Old age: ' + oldValues[0])
      console.log('New age: ' + newValues[0])
      console.log('New name: ' + newValues[1])
      console.log('Old name: ' + oldValues[1])
    } );

    const setNewAge = () => {
      uAge.value = 44
    }

    const setLastName = () => {
      lastName.value = lastNameInput.value.value
    }

    // const spocitejCenu = (vstupniCena) => {
    //   const cenaProduktu = 1000 + vstupniCena
    //
    //   return cenaProduktu
    // }

    // onMounted(() => {
    //   const vyslednaCena = spocitejCenu(3000)
    //   console.log(vyslednaCena)
    // })


    // const setFirstName = (event) => {
    //   firstName.value = event.target.value;
    // }
    //
    //
    // const setLastName = (event) => {
    //   lastName.value = event.target.value;
    // }


    return {
      userName: uName,
      age: uAge,
      setAge: setNewAge,
      // setFirstName,
      // setLastName,
      firstName,
      lastNameInput,
      setLastName
    };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },


};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>