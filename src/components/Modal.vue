<template>
    <div class="modal-holder">
        <div class="modal" v-if="modalType === 'success'">
            <div class="close" @click="closeModal()">
                <img src="../assets/images/close.svg">
            </div>
            <img src="../assets/images/success.svg">
            <h2>Dziękuję!</h2>
            <p :class="modalType">Wiadomość wysłana <span>poprawnie.</span></p>
        </div>
        <div v-else class="modal">
            <div class="close" @click="closeModal()">
                <img src="../assets/images/close.svg">
            </div>
            <img src="../assets/images/error.svg">
            <h2>Ups!</h2>
            <p :class="modalType">Wystąpił <span>błąd</span> podczas wysyłania wiadomości.</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'modal',
  props: {
    message: String,
    modalActive: Boolean,
    modalType: String,
  },
  methods: {
    closeModal() {
      this.$emit('modal-close');
    },
  },
};
</script>

<style lang="scss">
.modal-holder {
    z-index: 15;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(26,26,26,.5);
    cursor: pointer;
}

.modal {
    width: 400px;
    height: 200px;
    -webkit-box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
    -moz-box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
    box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
    z-index: 1;
    background-color: #fff;
    position: fixed;
    left: 0;
    right: 0;
    top: 30%;
    margin: auto;
    border-radius: 4px;
    padding: 24px;
    text-align: center;
    cursor: default;

    .close {
        position: absolute;
        right: 16px;
        top: 16px;
        width: 28px;
        height: 28px;
        cursor: pointer;
    }

    img {
        width: 50px;
        margin: auto;
        margin-bottom: 16px;
    }

    h2 {
        color: #293347;
        margin-bottom: 16px;
    }

    p {
        font-weight: 400;
        font-size: 16px;
        color: #293347;
        max-width: 600px;
        margin: auto;
        line-height: 1.64;

        &.success {
            span {
                color: #17B890;
            }
        }

        &.error {
            span {
                color: #FF3A20;
            }
        }
    }
}

</style>
