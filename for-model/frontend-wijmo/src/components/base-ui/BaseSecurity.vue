<template>
    <div></div>
</template>

<script>

export default {
    name: 'BaseSecurity',
    methods: {
        getUserRole(){
            if(this.$OAuth){
                return this.$OAuth.tokenParsed.realm_access.roles.join(",")
            }else{
                return ''
            }
        },
        hasRole(roleName){
            if(!this.$OAuth){
                return true
            }
            return this.getUserRole().includes(roleName);
        },
        getUserName(){
            if(this.$OAuth){
                return this.$OAuth.idTokenParsed.preferred_username
            }else{
                return 'Guest'
            }
        },
    },
};
</script>
