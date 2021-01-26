<template>
    <form @submit.prevent="addUser()">
        <input v-model="newUser"  type="text" placeholder="Enter User">
    </form>
</template>



<script>
export default {
    name: "AddUser",
    data() {
        return {
            newUser: ''
        }
    },
    methods: {
        addUser() {
            if(this.newUser.length > 1) {
                this.$emit('on-adduser', this.newUser);
            }
            this.newUser = "";
        }
    }
}
</script>


<style scoped>

</style>