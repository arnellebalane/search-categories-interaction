<template>
    <div class="search-categories">
        <button ref="button" @click="rotate"></button>
        <div ref="ripple" class="ripple"></div>

        <div class="overflow">
            <div ref="categories" class="categories">
                <p ref="all">All</p>
                <p ref="videos">Videos</p>
                <p ref="images">Images</p>
                <p ref="news">News</p>
            </div>
        </div>
    </div>
</template>

<script>
    import anime from 'animejs';

    export default {
        name: 'SearchCategories',

        data() {
            return {
                rotation: 0
            };
        },

        methods: {
            rotate() {
                this.rotation += 90;

                anime({
                    targets: [this.$refs.button, this.$refs.categories],
                    rotate: this.rotation,
                    easing: 'easeInOutBack',
                    duration: 700,
                    delay: 50
                });

                var current, next;

                if (this.rotation % 360 === 0) {
                    current = this.$refs.news;
                    next = this.$refs.all;
                } else if (this.rotation % 360 === 90) {
                    current = this.$refs.all;
                    next = this.$refs.videos;
                } else if (this.rotation % 360 === 180) {
                    current = this.$refs.videos;
                    next = this.$refs.images;
                } else if (this.rotation % 360 === 270) {
                    current = this.$refs.images;
                    next = this.$refs.news;
                }

                anime({
                    targets: current,
                    opacity: 0,
                    duration: 350,
                    delay: 50,
                    easing: 'easeInQuad'
                });
                anime({
                    targets: next,
                    opacity: 1,
                    duration: 350,
                    delay: 50,
                    easing: 'easeInQuad'
                });
                anime({
                    targets: this.$refs.ripple,
                    scale: [1.3, 3.5],
                    opacity: [0.5, 0],
                    borderWidth: ['18px', '2px'],
                    duration: 750,
                    easing: 'easeInOutBack'
                });
            }
        }
    };
</script>

<style scoped>
    .search-categories {
        padding: 24px;
        color: #ddd9cb;
        pointer-events: none;
    }

    .ripple {
        width: 40px;
        height: 40px;
        border: 20px solid currentColor;
        border-radius: 50%;
        position: absolute;
        top: 20px;
        left: 20px;
        z-index: 1;
        opacity: 0;
        transform-origin: center center;
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
        border-radius: 10px;
        position: absolute;
        top: calc(50% - 3px);
        left: calc(50% - 7px);
        background-color: currentColor;
        transform: translate(14px, -14px) rotate(-45deg);
        transform-origin: center center;
    }

    .overflow,
    .categories,
    .categories p {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
    }

    .overflow {
        overflow: hidden;
    }

    .categories {
        display: var(--placeholder-display, block);
        transform-origin: 40px 40px;
    }

    .categories p {
        padding-left: 84px;
        margin: 0;
        font-size: 28px;
        line-height: 80px;
        letter-spacing: 1px;
        transform-origin: 40px 40px;
    }

    .categories p:not(:nth-child(1)) {
        opacity: 0;
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
