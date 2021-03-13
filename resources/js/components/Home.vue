<template>
    <div style="text-align: center; padding: 40px">
        <h1>{{ welcome }}</h1>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Soluta unde tempora consequatur vel, ut quaerat natus eaque voluptates, eligendi necessitatibus sint. Nulla possimus est suscipit magnam doloribus quaerat sapiente corporis.</p>
    </div>
</template>

<script>
    export default {
        name: 'home',
        computed: {
            welcome() {
                return this.$store.getters.welcome
            }
        }
    }
</script>