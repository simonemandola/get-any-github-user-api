<template>
  <div>
    <div class="layer">
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
      <div class="layer__col" :class="{'hide-screensplash' : showTransClass}"></div>
    </div>
    <div class="screensplash" v-if="hideScreenSP">
      <button type="button" title="Click to start" @click.prevent="startFinder">
        <i class="icon__screensplash"></i>
        <i class="icon__screensplash icon-shadow"></i>
        <span class="dev-by">dev. by @simonemandola</span>
      </button>
    </div>
  </div>
</template>

<script>

import {ref, computed} from "vue";

export default {

  name: "Screensplash",

  setup() {

    let showTransition = ref(false);

    let hideScreenSP = ref(true);

    const startFinder = ()=>{
      showTransition.value = true;
      setTimeout(()=>{
        hideScreenSP.value = false
        showTransition.value = false;
      }, 800)
    }

    const showTransClass = computed(()=>{
      return showTransition.value;
    })

    return {
      showTransClass,
      hideScreenSP,
      startFinder
    }

  },
}
</script>