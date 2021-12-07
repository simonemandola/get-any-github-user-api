<template>
  <form @submit.prevent="findUser">
    <label>
      <input type="text"
             v-model.trim="usernameInput"
             :placeholder="!isMobile ? 'Insert GitHub username...' : 'Username...' "
             required
             :class="{ 'error' : notFound }"
      >
    </label>
    <button type="submit" v-if="!isMobile">Search</button>
    <button type="submit" v-if="isMobile"><i class="icon__search"></i></button>
  </form>
</template>

<script>

import {ref, inject, computed} from "vue";

export default {

  name: "UserForm",

 setup() {

    const API = 'https://api.github.com/users/';
    let url = API;
    let usernameInput = ref('');
    let username = inject('username');
    let user = inject('user');
    const DEFAULT_USER = 'octocat';
    let notFound = ref(false);
    const BREAK_POINT = 600;
    let isMobile = false;

    (window.innerWidth <= BREAK_POINT) ? isMobile = true : isMobile = false;

   const getUser = async () =>{

     try {

       const resUser = await fetch(url);

       if(resUser.status === 404) {
         throw new Error("GitHub user not found!")
       } else {
         user.value = await resUser.json();
         notFound.value = false;
         console.log(user.value);
       }

     } catch (error) {
       console.error(error.message);
       notFound.value = true;
     }
   }

    const findUser = async ()=> {

      if (usernameInput.value === "") {
        alert("Please insert GitHub username. 😉");
        return usernameInput.value;
      } else {

        if(usernameInput.value.includes(' ')) usernameInput.value = usernameInput.value.replace(/ /g, "");

        url = API + usernameInput.value;

        await getUser();

        usernameInput.value = '';
      }
    }

    computed(()=>{
      return notFound;
   })

    window.addEventListener('load', ()=>{
      url = API + DEFAULT_USER;
      getUser();
    })

    return {
      username,
      findUser,
      usernameInput,
      notFound,
      isMobile
    }
  }
}
</script>