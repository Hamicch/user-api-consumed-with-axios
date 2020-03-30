<template>
    <div>
        <form @submit="addUser">
            <input type="text" name="name" placeholder="Add User..." class="txtbox" v-model="name" />
            <input type="submit" value="Add" class="btn" />
        </form>
    </div>
</template>

<script>

export default {
    name: "Adduser",
    data() {
        return {
            name: ""
        };
    },

    methods: {
        addUser(e) {
            e.preventDefault();
            const newUser = {
                name: this.name
            };
            // Sending emits   signal to parent
            this.$emit("add-user", newUser);

            this.name = " ";
        }
    }
};
</script>

<style scoped>
form {
    text-align: center;
}

.txtbox {
    border: none;
    width: 200px;
    height: 30px;
    border-radius: 4px;
    background-color: rgb(248, 245, 246);
    padding: 4px 20px;
}

.btn {
    margin: 10px;
    border: none;
    width: 70px;
    height: 37px;
    border-radius: 4px;
    color: #fff;
    background-color: crimson;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
}

::placeholder {
    color: rgb(219, 146, 160);
}

.btn:hover {
    background-color: rgb(220, 20, 60, 0.8);
}

input[type="submit"] {
    margin: 10px;
}
</style>
