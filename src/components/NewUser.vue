<template>
  <div class="new-user" >
    <!-- <input type="checkbox" v-on:change="checkComplete" class="checker" />
    <span>{{ todo.title }}</span>
    <button class="del" @click="$emit('del-todo', todo.id)">X</button> -->
    <p>
      {{ user.name }}
     <span>
       <svg @click="$emit('del-todo', todo.id)" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="trash" class="svg-inline--fa fa-trash fa-w-14" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path fill="currentColor" d="M432 32H312l-9.4-18.7A24 24 0 0 0 281.1 0H166.8a23.72 23.72 0 0 0-21.4 13.3L136 32H16A16 16 0 0 0 0 48v32a16 16 0 0 0 16 16h416a16 16 0 0 0 16-16V48a16 16 0 0 0-16-16zM53.2 467a48 48 0 0 0 47.9 45h245.8a48 48 0 0 0 47.9-45L416 128H32z"></path></svg>
     </span>
    </p>
  </div>
</template>

<script>
export default {
  name: "NewUser",
  props: ["user"],
};
</script>

<style scoped>
.new-user {
  text-align: left;
  margin: 7px;
  padding: 15px;
  color: crimson;
  font-size: 14px;
  font-weight: 500;
  background: rgb(248, 245, 246);
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.5sec ease-in-out;
}

.new-user:hover {
  background: rgb(247, 239, 240);
}

.is-complete {
  text-decoration: line-through;
  color: rgb(221, 135, 152);
}

span {
  margin: 0px 20px;
}

span svg {
  float: right;
  width: 18px;
  height: 18px;
}
</style>
