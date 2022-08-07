<template>
    <header>
        <h2>{{ title }}</h2>
        <AppButton @toggle-add-list="$emit('toggle-add-list')" text='+ LIST ITEM' color='steelblue' />
    </header>
</template>

<script>
    import AppButton from './AppButton.vue'

    export default {
        name: 'AppHeader',

        props: {
            title: String,
        },

        components: {
            AppButton,
        }
    }
</script>

<style scoped>
    header {
        color: white;
        background-color: lightblue;
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
    h2 {
        padding-left: 100px;
    }
</style>