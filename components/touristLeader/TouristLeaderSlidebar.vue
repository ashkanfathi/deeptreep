<template>
  <div class="shadow h-100">
    <ul
      class="d-flex flex-column vh-100 p-0 w-100"
      style="position: sticky; top: 0px"
    >
      <li class="text-center py-3 border-bottom bgmain text-light">
        <h3 class="h6">
          <nuxt-link to="/" class="text-white">DEEP TREEP</nuxt-link>
        </h3>
      </li>
      <nuxt-link
        to="/panel/touristLeader/profile"
        class="py-2 px-4 w-100 right-to-left-animation border-bottom"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-solid fa-user"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block">profile</span>
      </nuxt-link>
      <nuxt-link
        to="/panel/touristLeader/users"
        class="py-2 px-4 w-100 right-to-left-animation border-bottom"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-solid fa-users"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block">users</span>
      </nuxt-link>
      <nuxt-link
        to="/panel/touristLeader/tours"
        class="py-2 px-4 w-100 right-to-left-animation border-bottom"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-solid fa-plane"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block">tours</span>
      </nuxt-link>
      <nuxt-link
        to="/panel/touristLeader/tiket"
        class="py-2 px-4 w-100 right-to-left-animation border-bottom"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-regular fa-ticket"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block"
          >request travel itinerary</span
        >
      </nuxt-link>
      <nuxt-link
        to="/panel/touristLeader/education"
        class="py-2 px-4 w-100 right-to-left-animation border-bottom"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-regular fa-film"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block">education</span>
      </nuxt-link>
      <button
        class="py-2 px-4 w-100 right-to-left-animation border-0 border-bottom text-left bg-transparent"
        @click="onSignOut"
      >
        <span class="d-block d-sm-inline-block text-center">
          <i class="fa-solid fa-sign-out"></i>
        </span>
        <span class="ms-1 d-none d-sm-inline-block">sign out</span>
      </button>
    </ul>
  </div>
</template>

<script>
export default {
  name: "touristSidebarSection",

  data() {
    return {};
  },

  methods: {
    async onSignOut() {
      await this.$auth.logout();
    },
  },
};
</script>

<style scoped>
span {
  color: black !important;
}
</style>
