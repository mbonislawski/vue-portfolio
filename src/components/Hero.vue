<template>
    <div class="hero">
        <div class="container">
            <div class="user-holder" v-if="showImage">
                <img src="../assets/images/user.svg">
            </div>
            <h1 :class="{'anime': animations}" v-html="header"></h1>
            <p :class="{'anime': animations}">{{ subhead }}</p>
            <router-link class="btn" to="/portfolio" v-if="showButton">Portfolio</router-link>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Hero',
  props: {
    header: String,
    subhead: String,
    showButton: Boolean,
    showImage: Boolean,
    animations: Boolean,
  },
};
</script>

<style lang="scss">
    .hero {
        width: 100%;
        height: 100vh;
        text-align: center;
        padding: 200px 0;


        .user-holder {
            width: 190px;
            margin: auto;

            img {
                width: 100%;
            }
        }

        h1 {
            font-weight: 700;
            color: #293347;
            font-size: 60px;
            margin: auto;
            margin-bottom: 16px;
            @media(max-width: 720px) {
              font-size: 40px;
            }
            @media(max-width: 520px) {
              font-size: 34px;
            }
            &.anime {
              width: 570px;
              opacity: 0;
              overflow: hidden;
              white-space: nowrap;
              -webkit-animation: type2 2s steps(40, end);
              animation: type2 2s steps(40, end);
              -webkit-animation-delay: 1s;
              animation-delay: 1s;
              -webkit-animation-fill-mode: forwards;
              animation-fill-mode: forwards;
            }

            span {
                color: #17B890;
            }
        }

        p {
            font-weight: 300;
            color: #293347;
            font-size: 24px;
            width: 470px;
            margin: auto;
            margin-bottom: 16px;
            @media(max-width: 720px) {
              font-size: 20px;
              width: 400px;
            }
            @media(max-width: 520px) {
              font-size: 16px;
              width: 330px;
            }
            &.anime {
              overflow: hidden;
              white-space: nowrap;
              opacity: 0;
              -webkit-animation: type 2s steps(20, end), blink .5s step-end infinite alternate;
              animation: type 2s steps(20, end), blink .5s step-end infinite alternate;
              -webkit-animation-delay: 3s;
              animation-delay: 3s;
              -webkit-animation-fill-mode: forwards;
              animation-fill-mode: forwards;
              border-right: 2px solid #17B890;
            }
        }
    }

    .btn {
        width: 240px;
        height: 48px;
        line-height: 44px;
        font-size: 16px;
        color: #fff;
        font-weight: 500;
        background-color: #17B890;
        border-radius: 24px;
        display: block;
        margin: auto;
        transition: all .3s;
        margin-top: 40px;
        text-align: center;
        border: 2px solid #17B890;

        &:hover {
            opacity: .8;
        }

        &.secondary {
            background-color: transparent;
            color: #17B890;
            border-color: #17B890;

            &:hover {
                background-color: #17B890;
                color: #fff;
                opacity: 1;
            }
        }
    }

@keyframes type {
    0% {
        width: 0;
    }
    1% {
        opacity: 1;
    }
    100% {
        opacity: 1;
    }
}

@-webkit-keyframes type {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}
@-webkit-keyframes blink {
  50% {
    border-color: tranparent;
  }
}

@keyframes type2 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
    border-right: 4px solid #17B890;
  }
  20% {
    border: none;
  }
  40% {
    border-right: 4px solid #17B890;
  }
  60% {
    border: none;
  }
  80% {
    border-right: 4px solid #17B890;
  }
  100% {
    opacity: 1;
    border: none;
  }
}

@-webkit-keyframes type2 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
    border-right: 4px solid #17B890;
  }
  20% {
    border: none;
  }
  40% {
    border-right: 4px solid #17B890;
  }
  60% {
    border: none;
  }
  80% {
    border-right: 4px solid #17B890;
  }
  100% {
    opacity: 1;
    border: none;
  }
}
</style>
