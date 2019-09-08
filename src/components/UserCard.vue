<template>
  <div class="col-4">
    <a href="#">
      <img :src="user.image" width="140px" height="140px" />
    </a>
    <h2>{{user.name}}</h2>
    <span class="badge badge-secondary">Followers：{{user.FollowerCount}}</span>
    <p class="mt-3">
      <button
        v-if="user.isFollowed"
        type="button"
        class="btn btn-sm btn-danger mr-2"
        @click.stop.prevent="unfollow"
      >Unfollow</button>
      <button
        v-else
        type="button"
        class="btn btn-sm btn-primary mr-2"
        @click.stop.prevent="follow"
      >Follow</button>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line
    user: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      // eslint-disable-next-line
      user: this.user
    };
  },
  methods: {
    follow() {
      this.user = {
        ...this.user,
        isFollowed: true
      };
    },
    unfollow() {
      this.user = {
        ...this.user,
        isFollowed: false
      };
    }
  }
};
</script>