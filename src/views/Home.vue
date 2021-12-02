<template>
  <Screensplash />
  <div class="wrap">
    <header>
      <h1>Search GitHub username</h1>
    </header>
    <user-card />
  </div>
</template>

<script>

import { ref, provide } from "vue";
import Screensplash from "@/components/Screensplash.vue";
import UserCard from "@/components/UserCard.vue";

export default {
  name: "Home",

  components:{
    Screensplash,
    UserCard
  },

  setup(){

    let username = ref('');
    provide('username', username);

    let user = ref({});
    provide('user', user)

    return {
      username
    }
  }
}
</script>