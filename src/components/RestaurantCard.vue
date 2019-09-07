<template>
  <div class="col-md-6 col-lg-4">
    <div class="card mb-4">
      <img
        class="card-img-top"
        :src="restaurant.image"
        alt="Card image cap"
        width="286px"
        height="180px"
      />
      <div class="card-body">
        <p class="card-text title-wrap">
          <a href="#">{{ restaurant.name }}</a>
        </p>
        <span class="badge badge-secondary">{{ restaurant.Category.name }}</span>
        <p class="card-text text-truncate">{{ restaurant.description }}</p>
      </div>
      <div class="card-footer">
        <button
          type="button"
          class="btn btn-danger btn-sm btn-border favorite mr-2 mt-1"
        >Remove from Favorite</button>
        <button
          type="button"
          class="btn btn-primary btn-sm btn-border favorite mr-2 mt-1"
        >Add to Favorite</button>
        <button type="button" class="btn btn-danger btn-sm like mr-2 mt-1">Unlike</button>
        <button type="button" class="btn btn-primary btn-sm like mr-2 mt-1">Like</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialRestaurant: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      restaurant: this.initialRestaurant
    };
  }
};
</script>