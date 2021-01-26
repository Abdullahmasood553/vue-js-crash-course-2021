<template>
    <div class="container">
        <input type="checkbox" class="myinput" v-on:change="toggleUser">
        <p v-if="!isEditing" v-bind:class="{ 'is-status':user.status }">{{ user.name }}</p>
        <form v-else @submit.prevent="endEditing()">
            <input @blur="startEditing()" v-model="newUser" type="text" class="form-control">
        </form>
        <button @click="startEditing()" class="btn btn-primary">Edit</button>
        <button @click="$emit('on-delete')" class="btn btn-danger">Delete</button>
    </div>
</template>



<script>
export default {
    name: "User",
    props: ["user"],
    data() {
        return {
            isEditing: false,
            newUser: ''
        }
    },
    methods: {
        toggleUser() {
            this.user.status = !this.user.status;
        },
        startEditing() {
       
            if(!this.isEditing) {
                this.newUser = this.user.name;
                this.isEditing = true;
            } else {
                this.endEditing();
            }
        },

        endEditing() {
            this.isEditing = false;
            this.$emit('on-edit', this.newUser);
        }
    }
}
</script>



<style scoped>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }


    .myinput[type="checkbox"] {
        width: 16px;
        height: 15px;
        content:"";
        background: #fff;
    }


    .form-control {
        width:100%;
        padding:5px;
        margin-top:5px;
        background:#f4f4f4;
        border: 1px solid #333;
    }

        .btn.btn-primary {
        background:blue;
        color:#fff;
        padding:5px;
        margin:5px;
        border:none;
    }

.btn.btn-danger{
    background:red;
    color:#fff;
    padding:5px;
    margin:5px;
    border:none;
}

.is-status {
    text-decoration: line-through;
}
</style>