<template>
  <div>
    <Screensplash />
    <h1 style="margin: 0">Get any GitHub user 😁</h1>
    <button
        type="button"><i class="icon__screensplash"
                         style="width: 6rem; height: 6rem; font-size: 6rem; color: #fff;"></i></button>
  </div>
</template>

<script>

import Screensplash from "@/components/Screensplash";

export default {
  name: "Home",

  components:{
    Screensplash
  }
}
</script>