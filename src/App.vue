<template>
  <div id="app">
    @{{ user.username }} - {{ fullName }}
    <div><strong>Followers:</strong> {{ followers }}</div>
    <button @click="followUser">
      Follow
    </button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'jackwkinsey',
        firstName: 'Jack',
        lastName: 'Kinsey',
        email: 'jack.w.kinsey@gmail.com',
        isAdmin: true,
      },
    };
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (newFollowerCount > oldFollowerCount) {
        console.log(`${this.user.username} has gained a new follower!`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
  },
  mounted() {
    this.followUser();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
