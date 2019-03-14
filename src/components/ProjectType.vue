<template>
    <div class="project-type">
        <div class="icon-holder">
            <img :src="'/images/'+icon+'.svg'">
        </div>
        <div class="text-holder">
            <h4>{{ header }}</h4>
            <p>{{ description }}</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ProjectType',
  props: {
    icon: String,
    header: String,
    description: String,
  },
};
</script>

<style lang="scss" scoped>
    .project-type {
        padding: 50px 40px;
        text-align: center;
        background-color: #fff;
        width: 33.33%;
        border-right: 2px solid #F7F7F7;
        @media(max-width: 1075px) {
            width: 45%;
            border-radius: 4px;
            margin: 0 14px;
            margin-bottom: 28px;
        }
        @media(max-width: 720px) {
            width: 80%;
            margin: auto;
            margin-bottom: 28px;
        }
        @media(max-width: 520px) {
            width: 100%;
        }

        &:last-of-type {
            border-right: none;
        }

        .icon-holder {
            max-width: 40px;
            height: 40px;
            margin: auto;
            margin-bottom: 16px;

            img {
                max-width: 100%;
                max-height: 100%;
            }
        }

        h4 {
            font-weight: 600;
            color: #293347;
            margin-bottom: 24px;
        }

        p {
            font-size: 14px;
            font-weight: 300px;
            color: #293347;
            line-height: 1.8;
            max-width: 220px;
            margin: auto;
        }
    }
</style>
