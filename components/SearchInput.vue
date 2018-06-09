<template>
    <div class="search-input">
        <input type="text" placeholder=" ">
        <SearchCategories />
    </div>
</template>

<script>
    import SearchCategories from './SearchCategories.vue';

    export default {
        name: 'SearchInput',

        components: {
            SearchCategories
        }
    };
</script>

<style scoped>
    .search-input {
        position: relative;
    }

    input {
        width: 90vw;
        max-width: 400px;
        padding: 0 1em;
        padding-left: 84px;
        border: none;
        border-radius: 10px;
        font-size: 28px;
        line-height: 80px;
        letter-spacing: 1px;
        outline: none;
    }

    .search-categories {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
    }

    input:not(:placeholder-shown) + .search-categories {
        --placeholder-display: none;
    }
</style>
