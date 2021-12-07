<template>
  <div class="user__info-wrap searchbar-mobile">
    <user-form />
  </div>
  <section class="user">
    <div class="user__main">
      <div class="user__main-img">
        <div class="user__main-img-wrap">
          <img :src=" user.avatar_url " :alt="user.name + ' github user image'">
        </div>
      </div>
      <div class="user__main-text">
        <p class="text-s user__main-text-name">{{ user.name !== null ? user.name : 'n/a' }}</p>
        <p class="text-s user__main-text-username">{{ user.login !== null ? user.login : 'n/a' }}</p>
        <p class="text-s">BIO:</p>
        <p class="text-s user__main-text-bio">{{ user.bio !== null ? user.bio : 'n/a' }}</p>
      </div>
    </div>
    <div class="user__info-wrap">
      <div class="searchbar-desktop">
        <user-form/>
      </div>
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
          <p class="text-s">{{ user.location !== null ? user.location : 'n/a' }}</p>
        </div>
        <div class="user__links-web">
          <i class="icon__link"></i>
          <a :href="user.blog !== '' ? user.blog : '#' "
             target="_blank" rel="nofollow"
             class="text-s">{{ user.blog !== '' ? user.blog : 'n/a' }}
          </a>
        </div>
        <div class="user__links-twitter">
          <i class="icon__twitter"></i>
          <p class="text-s">{{ user.twitter_username !== null ? user.twitter_username : 'n/a' }}</p>
        </div>
        <div class="user__links-view-profile">
          <a :href="user.html_url" target="_blank" class="text-s">View on GitHub</a>
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

    const user = inject('user');

    return {
      user
    }
  }

}
</script>