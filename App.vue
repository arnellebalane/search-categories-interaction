<template>
    <div id="app" class="app">
        <SearchInput />
    </div>
</template>

<script>
    import SearchInput from './components/SearchInput.vue';

    export default {
        name: 'App',

        components: {
            SearchInput
        }
    };
</script>
