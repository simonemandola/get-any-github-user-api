<template>
  <section class="user">
    <div class="user__main">
      <div class="user__main-img">
        <div class="user__main-img-wrap">
          <img :src=" user.avatar_url " alt="github user image">
        </div>
      </div>
      <div class="user__main-text">
        <p class="text-s user__main-text-name">{{ user.name }}</p>
        <p class="text-s user__main-text-username">{{ user.login }}</p>
        <p class="text-s">BIO:</p>
        <p class="text-s user__main-text-bio">{{ user.bio }}</p>
      </div>
    </div>
    <div class="user__info-wrap">
      <user-form />
      <div class="user__stats">
        <div class="user__repos">
          <h4>Repos</h4>
          <p class="text-s">{{ user.public_repos }}</p>
        </div>
        <div class="user__followers">
          <h4>Followers</h4>
          <p class="text-s">{{ user.followers }}</p>
        </div>
        <div class="user__following">
          <h4>Following</h4>
          <p class="text-s">{{ user.following }}</p>
        </div>
      </div>
      <div class="user__links">
        <div class="user__links-location">
          <i class="icon__pin"></i>
          <p class="text-s">{{ user.location }}</p>
        </div>
        <div class="user__links-web">
          <i class="icon__link"></i>
          <a :href="user.blog" target="_blank" class="text-s">{{ user.blog }}</a>
        </div>
        <div class="user__links-twitter">
          <i class="icon__twitter"></i>
          <p class="text-s">{{ user.twitter_username }}</p>
        </div>
        <div class="user__links-created">
          <i class="icon__candle"></i>
          <p class="text-s">{{ user.created_at }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>

import {inject} from "vue";
import UserForm from "@/components/UserForm";

export default {
  name: "UserCard",
  components: {
    UserForm
  },

  setup() {

    let user = inject('user');

    return {
      user
    }
  }

}
</script>