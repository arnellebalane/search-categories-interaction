<template>
    <div class="search-categories">
        <button></button>
        <div class="categories">
            <p>All</p>
            <p>Videos</p>
            <p>Images</p>
            <p>News</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'SearchCategories'
    };
</script>

<style scoped>
    .search-categories {
        padding: 24px;
        color: #ddd9cb;
        pointer-events: none;
    }

    button {
        width: 32px;
        height: 32px;
        border: 5px solid currentColor;
        border-radius: 50%;
        position: relative;
        color: inherit;
        cursor: pointer;
        outline: none;
        pointer-events: auto;
    }

    button::before {
        content: "";
        width: 14px;
        height: 5px;
        border-radius: 8px;
        position: absolute;
        top: calc(50% - 3px);
        left: calc(50% - 7px);
        background-color: currentColor;
        transform: translate(14px, -14px) rotate(-45deg);
        transform-origin: center center;
    }

    .categories {
        display: var(--placeholder-display, block);
    }

    .categories p {
        padding-left: 84px;
        margin: 0;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        font-size: 24px;
        line-height: 80px;
        transform-origin: 40px 40px;
    }

    .categories p:nth-child(2) {
        transform: rotate(-90deg);
    }

    .categories p:nth-child(3) {
        transform: rotate(-180deg);
    }

    .categories p:nth-child(4) {
        transform: rotate(-270deg);
    }
</style>
