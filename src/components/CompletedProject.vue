<template>
    <div class="single-project">
        <div class="project-thumbnail"></div>
        <p class="btn secondary" target="_blank" to="/portfolio">Wkrótce</p>
    </div>
</template>

<script>
export default {
  name: 'CompletedProject',
  props: {
    thumbnail: String,
    url: String,
  },
};
</script>

<style lang="scss" scoped>
    .single-project {
        cursor: pointer;
        transition: all .3s;
        position: relative;
        overflow: hidden;

        &:hover {
            transform: scale(1.1);

            .btn {
                opacity: 1;
                transform: translateY(0);
            }
        }
    }

    .project-thumbnail {
        width: 360px;
        height: 220px;
        background-color: #CECECE;
        border-radius: 4px;
        @media(max-width: 1200px) {
            width: 300px;
            height: 190px;
        }
        @media(max-width: 1075px) {
            width: 400px;
            height: 220px;
            margin-bottom: 32px;
        }
        @media(max-width: 520px) {
          width: 340px;
        }
    }

    .btn {
        position: absolute;
        bottom: 20px;
        left: 0;
        height: 36px;
        line-height: 32px;
        width: 120px;
        font-size: 14px;
        right: 0;
        opacity: 0;
        transform: translateY(200px);
        @media(max-width: 1075px) {
            bottom: 60px;
        }

        &:hover {
            line-height: 32px;
        }
    }
</style>
