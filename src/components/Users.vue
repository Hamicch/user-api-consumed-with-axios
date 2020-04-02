<template>
  <div class="todos">
    <div v-for="user in users" :key="user.id">
      <NewUser v-bind:user="user" v-on:delete-user="$emit('delete-user', user.id)" />
    </div>
  </div>
</template>

<script>
import NewUser from "./NewUser";

export default {
  name: "Users",
  components: {
    NewUser
  },
  props: ["users"]
};
</script>

<style scoped>
.todos {
  margin-top: 50px;
}
</style>
