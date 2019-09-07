<template>
  <div class="card">
    <div class="card-header">New comments</div>
    <div class="card-body">
      <div v-for="comment in comments" :key="comment.id">
        <h4>
          <a href="#">{{ comment.User.name }}</a>
        </h4>
        <p>{{ comment.text }}</p>
        {{ comment.createdAt | fromNow }}
        <hr />
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  filters: {
    fromNow(datetime) {
      if (!datetime) {
        return "-";
      }
      return moment(datetime).fromNow();
    }
  },
  props: {
    comments: {
      type: Array,
      required: true
    }
  }
};
</script>