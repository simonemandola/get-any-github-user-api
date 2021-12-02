<template>
  <form @submit.prevent="findUser">
    <label>
      <input type="text"
             v-model.trim="usernameInput"
             placeholder="Search GitHub username..."
             required
             :class="{ 'error' : notFound }"
      >
    </label>
    <button type="submit">Search</button>
  </form>
</template>

<script>

import { ref, inject } from "vue";

export default {
  name: "UserForm",

 setup() {

    const API = 'https://api.github.com/users/';
    let usernameInput = ref('');
    let username = inject('username');
    let user = inject('user');
    let notFound = ref(false);

    const getUser = async (url)=>{
      await fetch(url)
          .then(res => res.json())
          .then(res => {
            notFound = false;
            user.value = res;
          })
          .catch(error => {
            console.log("Not Found!");
            notFound.value = true;
            console.log(error);
          });
    }

    const findUser = ()=> {

      if (usernameInput.value === "") {
        alert("Please insert GitHub username. 😉");
        return usernameInput.value;
      } else {

        if(usernameInput.value.includes(' ')) usernameInput.value = usernameInput.value.replace(/ /g, "");

        let url = API + usernameInput.value;

        getUser(url)

        usernameInput.value = '';
      }
    }

    return {
      username,
      findUser,
      usernameInput,
      notFound
    }
  }
}
</script>