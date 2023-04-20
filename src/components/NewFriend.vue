<template>
<form @submit.prevent="submitNewFriend" ref="friendForm">
    <label>Name</label>
    <input type="text" placeholder="Name..." v-model="friendName"/>
    <label>Phone</label>
    <input type="tel" placeholder="Phone..." v-model="friendPhone"/>
    <label>Email</label>
    <input type="email" placeholder="Email..." v-model="friendEmail"/>
    <button type="submit">Add New Friend</button>
</form>
</template>

<script>
export default {
    props: {

    },
    emits: {
        'add-friend': function(friendObj){
            if(friendObj) {
                return true;
            } else {
                console.log('friend object is missing')
                return false;
            }
        }
    },
    data() {
        return {
            friendName: '',
            friendPhone: '',
            friendEmail: '',
        }
    },
    methods: {
        submitNewFriend(){
            let newFriendObj = {
                name: this.friendName,
                phone: this.friendPhone,
                email: this.friendEmail,
            }
            this.$emit('add-friend', newFriendObj)
            this.$refs.friendForm.reset()
        }
    }
}
</script>

