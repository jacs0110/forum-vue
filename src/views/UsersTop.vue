<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">Top Users</h1>
    <hr />
    <div class="row text-center">
      <UserCard v-for="user in users" :key="user.id" :user="user" />
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import UserCard from "./../components/UserCard";

const dummyData = {
  users: [
    {
      id: 23,
      name: "root-test",
      email: "root@example.com",
      password: "$2a$10$P2kn1Pnu2TIEtniHEK.vr.J1.oxzADZ8koKTgrODqK8Cy2v0l.om6",
      isAdmin: true,
      image: "https://i.imgur.com/wuBpQcD.jpg",
      createdAt: "2019-08-30T10:04:58.000Z",
      updatedAt: "2019-09-03T15:47:54.000Z",
      Followers: [
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
          Followership: {
            followerId: 24,
            followingId: 23,
            createdAt: "2019-08-31T00:55:56.000Z",
            updatedAt: "2019-08-31T00:55:56.000Z"
          }
        },
        {
          id: 23,
          name: "root-test",
          email: "root@example.com",
          password:
            "$2a$10$P2kn1Pnu2TIEtniHEK.vr.J1.oxzADZ8koKTgrODqK8Cy2v0l.om6",
          isAdmin: true,
          image: "https://i.imgur.com/wuBpQcD.jpg",
          createdAt: "2019-08-30T10:04:58.000Z",
          updatedAt: "2019-09-03T15:47:54.000Z",
          Followership: {
            followerId: 23,
            followingId: 23,
            createdAt: "2019-09-03T15:54:52.000Z",
            updatedAt: "2019-09-03T15:54:52.000Z"
          }
        }
      ],
      FollowerCount: 2,
      isFollowed: true
    },
    {
      id: 24,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$Y3ACAUofMHsf1S.R.qUYM.7nrm9Pt4Y/o.TuryJ4pJL4O6cdHL3yC",
      isAdmin: false,
      image: null,
      createdAt: "2019-08-30T10:04:58.000Z",
      updatedAt: "2019-09-03T15:49:08.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 25,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$1pWkFo.EWbKX00gHF6qnNuGxCG4QfMYUrNRFCkjlBqcWFTxdP.jk6",
      isAdmin: false,
      image: null,
      createdAt: "2019-08-30T10:04:58.000Z",
      updatedAt: "2019-08-30T10:04:58.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    }
  ]
};

export default {
  components: {
    NavTabs,
    UserCard
  },
  data() {
    return {
      users: []
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users;
    }
  }
};
</script>