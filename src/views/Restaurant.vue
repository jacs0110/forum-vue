<template>
  <div class="container py-5">
    <h1>Restaurant</h1>
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :key="restaurant.id" :initial-restaurant="restaurant" />
    <hr />
    <!-- 餐廳評論 RestaurantComments -->
    <!-- 新增評論 CreateComment -->
  </div>
</template>

<script>
import RestaurantDetail from "./../components/RestaurantDetail";

const dummyData = {
  restaurant: {
    id: 104,
    name: "Micah Lubowitz",
    tel: "593.321.5257",
    address: "698 Mathias Tunnel",
    opening_hours: "08:00",
    description: "Est quasi quae at quo.",
    image: "http://lorempixel.com/640/480/food",
    viewCount: 8,
    createdAt: "2019-08-30T10:04:58.000Z",
    updatedAt: "2019-09-03T16:44:05.000Z",
    CategoryId: 7,
    Category: {
      id: 7,
      name: "複合式料理",
      createdAt: "2019-08-30T10:04:58.000Z",
      updatedAt: "2019-08-30T10:04:58.000Z"
    },
    Comments: [],
    LikedUsers: [
      {
        id: 24,
        name: "user1",
        email: "user1@example.com",
        password:
          "$2a$10$Y3ACAUofMHsf1S.R.qUYM.7nrm9Pt4Y/o.TuryJ4pJL4O6cdHL3yC",
        isAdmin: false,
        image: null,
        createdAt: "2019-08-30T10:04:58.000Z",
        updatedAt: "2019-09-03T15:49:08.000Z",
        Like: {
          UserId: 24,
          RestaurantId: 104,
          createdAt: "2019-09-02T18:51:26.000Z",
          updatedAt: "2019-09-02T18:51:26.000Z"
        }
      }
    ]
  },
  isLiked: false
};
export default {
  components: {
    RestaurantDetail
  },
  data() {
    return {
      restaurant: {
        id: -1,
        name: "",
        categoryName: "",
        image: "",
        openingHours: "",
        tel: "",
        address: "",
        description: "",
        // isFavorited: false,
        isLiked: false
      },
      restaurantComments: []
    };
  },
  created() {
    const { id: restaurantId } = this.$route.params;
    this.fetchRestaurant(restaurantId);
  },
  methods: {
    fetchRestaurant(restaurantId) {
      // eslint-disable-next-line
      console.log("fetchRestaurant id: ", restaurantId);

      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        image: dummyData.restaurant.image,
        openingHours: dummyData.restaurant.opening_hours,
        tel: dummyData.restaurant.tel,
        address: dummyData.restaurant.address,
        description: dummyData.restaurant.description,
        // isFavorited: dummyData.isFavorited,
        isLiked: dummyData.isLiked
      };
      this.restaurantComments = dummyData.restaurant.Comments;
    }
  }
};
</script>