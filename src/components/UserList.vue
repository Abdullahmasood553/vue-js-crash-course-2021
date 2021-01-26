<template>
    <div>
       <div class="container">
           <div class="row">
               <h3>vue Js Crash Course</h3>
           </div>

           <div class="row">
              <AddUser @on-adduser="addUser($event)" />
           </div>

           <div class="row">
               <User v-for="(user, index) in users"
                v-bind:key="index"
                v-bind:user="user"
                @on-delete="deleteUser(user)"
                @on-edit="editUser(user, $event)"
                 />
           </div>
       </div>
    </div>
</template>



<script>

import User from './User';
import AddUser from './AddUser';
export default {
    
    name: "UserList",
    data() {
        return {
            users: [
                {
                    name: 'John',
                    status: true
                },
                {
                    name: 'Adam',
                    status: false
                },
                {
                    name: 'Harry',
                    status:true
                },
                {
                    name: 'Sara',
                    status:false
                }
            ]
        }
    }, methods: {
        addUser(newUser) {
            this.users.push({
                name: newUser,
                status: false
            })
        },
        deleteUser(deleteUser) {
            this.users = this.users.filter(user => user.name !== deleteUser.name)
        },
        editUser(user, newUser) {
            user.name = newUser;
        }
    },
    components: {
        User,
        AddUser
    }
}
</script>



<style scoped>

    * {
        margin: 0;
        padding:0;
        box-sizing: border-box;
    }   
    .container {
        width:50%;
        background:#1577b0;
        margin:10px auto;
        padding:5px;
        border:2px solid darkblue;
    }

    p {
        font-size:18px;
    }
</style>