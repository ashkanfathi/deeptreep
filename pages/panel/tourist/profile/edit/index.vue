<template>
  <div>
    <ValidationObserver ref="form" v-slot="{ handleSubmit }">
      <form action="#" @submit.prevent="handleSubmit(edit)">
        <div class="row">
          <div class="col-6">
            <ValidationProvider v-slot="{ errors }" vid="role" rules="required">
              <label for="" class="col-12 mt-2">first name:</label>
              <input type="text" class="col-12" v-model="user.first_name" />
              <span class="text-xs text-danger col-12 p-0">{{
                errors[0]
              }}</span>
            </ValidationProvider>
          </div>
          <div class="col-6">
            <ValidationProvider v-slot="{ errors }" vid="role" rules="required">
              <label for="" class="col-12 mt-2">last name:</label>
              <input type="text" class="col-12" v-model="user.last_name" />
              <span class="text-xs text-danger col-12 p-0">{{
                errors[0]
              }}</span>
            </ValidationProvider>
          </div>
        </div>

        <ValidationProvider v-slot="{ errors }" vid="role" rules="required">
          <label for="" class="col-12 mt-2">gender:</label>
          <select class="col-12" style="height: 38px" v-model="user.gender">
            <option value="male">male</option>
            <option value="female">female</option>
          </select>
          <span class="text-xs text-danger col-12 p-0">{{ errors[0] }}</span>
        </ValidationProvider>
        <ValidationProvider v-slot="{ errors }" vid="role" rules="required">
          <label for="" class="col-12 mt-2">address:</label>
          <textarea
            type="text"
            class="col-12"
            rows="5"
            v-model="user.address"
          />
          <span class="text-xs text-danger col-12 p-0">{{ errors[0] }}</span>
        </ValidationProvider>
        <button class="btn btn-warning mt-3">Done</button>
      </form>
    </ValidationObserver>
  </div>
</template>

<script>
export default {
  name: "profile",
  layout: "tourist",

  async asyncData({ $axios }) {
    const user = await $axios.get("api/usersmodel/user-info/");
    return {
      user: user.data.results[0],
    };
  },

  methods: {
    async edit() {
      try {
        const bodyFormData = new FormData();
        bodyFormData.append("first_name", this.user.first_name);
        bodyFormData.append("last_name", this.user.last_name);
        bodyFormData.append("gender", this.user.gender || "");
        bodyFormData.append("address", this.user.address);
        const res = await this.$axios.put(
          "api/usersmodel/user-update/",
          bodyFormData
        );
        this.$router.push("/panel/tourist/profile");
        console.log(res);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style></style>
