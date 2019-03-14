<template>
  <div class="contact">
        <Hero :header="header"
          :subhead="subhead" />
        <div class="container">
        <form id="email-form" v-on:submit.prevent="formSubmit()">
            <div class="f-row inputs-row">
                <div>
                    <label>Imię i nazwisko</label>
                    <input name="name" v-model="name" type="text" required>
                </div>
                <div>
                    <label>Email</label>
                    <input name="email" v-model="email" type="email" required>
                </div>
            </div>
            <label>Wiadomość</label>
            <textarea name="message" v-model="message"></textarea>
            <div class="f-row checkbox-row">
                <label class="checkbox-container">
                    <input type="checkbox" id="accept" name="accept" required v-model="checkbox">
                    <div class="checkmark"></div>
                </label>
                <label class="checkbox-label" for="accept">Wyrażam zgodę na przetwarzanie
                danych osobowych zgodnie z
                ustawą o ochronie danych osobowych
                w związku z wysłaniem zapytania przez formularz kontaktowy. Podanie danych jest
                dobrowolne, ale niezbędne
                do przetworzenia zapytania. Zostałem poinformowany/a,
                że przysługuje mi prawo dostępu do swoich danych, możliwości ich poprawiania,
                żądania zaprzestania ich przetwarzania. Administratorem danych osobowych
                jest Marcin Bonisławski, ul.
                Bolesława Krzywoustego 8, 06-200 Maków Mazowiecki.</label>
            </div>
            <input type="text" name="fk-btn" id="fk-btn">
            <button type="submit" class="btn">Wyślij</button>
        </form>
    </div>
    <Modal
      v-on:modal-close="modalActive = false"
      v-if="modalActive"
      :modalType="modalType" />
  </div>
</template>

<script>
import Hero from '@/components/Hero.vue';
import axios from 'axios';
import Modal from '@/components/Modal.vue';

export default {
  name: 'kontakt',
  components: {
    Hero,
    Modal,
  },
  data() {
    return {
      header: 'Formularz kontaktowy',
      subhead: 'Skontaktuj się ze mną korzystając z formularza',
      name: null,
      email: null,
      message: null,
      checkbox: null,
      modalActive: false,
      modalType: null,
    };
  },
  methods: {
    formSubmit() {
      axios.post('/php/mailer.php', {
        name: this.name,
        email: this.email,
        message: this.message,
        checkbox: this.checkbox,
      })
        .then((response) => {
          if (response.status === 200) {
            if (response.data === true) {
              this.name = null;
              this.email = null;
              this.message = null;
              this.checkbox = null;
              this.modalActive = true;
              this.modalType = 'success';
            }
          } else {
            this.modalActive = true;
            this.modalType = 'error';
          }
        })
        .catch(() => {
          this.modalActive = true;
          this.modalType = 'error';
        });
    },
  },
};
</script>

<style lang="scss" scoped>
    .contact {
        background-color: #fff;
    }

    .hero {
        height: 450px;
        background-color: #fff;
        @media(max-width: 750px) {
            height: 400px;
        }
        @media(max-width: 500px) {
            height: 350px;
            padding-top: 145px;
        }
    }

    form {
        max-width: 700px;
        margin: auto;
        padding-bottom: 100px;

        #fk-btn {
            display: none;
        }

        .inputs-row {
            width: 100%;
            @media(max-width: 750px) {
                flex-direction: column;
            }

            & > div {
                @media(max-width: 750px) {
                    width: 100%;
                }
            }
        }

        .checkbox-row {
            align-items: flex-start;
            margin-top: 16px;
        }

        .checkbox-label {
            cursor: pointer;
            width: calc(100% - 33px);
            font-size: 14px;
            color: rgba(41,51,71,0.65);
        }

        label, input, textarea {
            width: 100%;
            text-align: left;
        }

        input {
            height: 50px;
            box-shadow: none;
            outline: none;
            border: 1px solid #E6ECF8;
            color: #293347;
            width: 330px;
            display: block;
            border-radius: 4px;
            padding-left: 16px;
            font-size: 16px;
            color: #E6ECF8;
            color: rgba(41,51,71,0.65);
            margin-bottom: 32px;
            transition: all .3s;
            @media(max-width: 750px) {
                width: 100%;
            }

            &:focus {
                border-color: #17B890;
            }
        }

        label:not(.checkbox-container):not(.checkbox-label) {
            color: #E6ECF8;
            color: rgba(41,51,71,0.65);
            display: block;
            width: 320px;
            margin: 0;
            margin-bottom: 12px;
            font-size: 16px;
            @media(max-width: 750px) {
                margin-left: auto;
                margin-right: auto;
                width: 100%;
            }
        }

        textarea {
            width: 100%;
            color: #E6ECF8;
            color: rgba(41,51,71,0.65);
            padding: 16px;
            font-size: 16px;
            min-width: 100%;
            border: 1px solid #E6ECF8;
            min-height: 300px;
            transition: all .3s;
            border-radius: 4px;
            // @media(max-width: 750px) {
            //     width: 330px;
            //     min-width: 330px;
            // }

            &:focus {
                border-color: #17B890;
            }
        }

        button {
            margin-top: 40px;
            cursor: pointer;
        }
    }

    .checkbox-container {
        display: block;
        position: relative;
        padding-left: 35px;
        margin-bottom: 12px;
        cursor: pointer;
        font-size: 22px;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        width: 25px;
        margin-right: 8px;
    }

    .checkbox-container input {
        position: absolute;
        opacity: 0;
        cursor: pointer;
        height: 0;
        width: 0;
    }

    .checkmark {
        position: absolute;
        top: 0;
        left: 0;
        height: 25px;
        width: 25px;
        background-color: #E6ECF8;
        border-radius: 4px;
    }

    .checkbox-container:hover input ~ .checkmark {
        background-color: #E6ECF8;
    }

    .checkbox-container input:checked ~ .checkmark {
        background-color: #17B890;
    }

    .checkbox-checkmark:after {
        content: "";
        position: absolute;
        display: none;
    }

    .checkmark:after {
        content: '';
        display: none;
    }

    .checkbox-container input:checked ~ .checkmark:after {
        display: block;
    }

    .checkbox-container .checkmark:after {
        left: 9px;
        top: 5px;
        width: 5px;
        height: 10px;
        border: solid white;
        border-width: 0 3px 3px 0;
        -webkit-transform: rotate(45deg);
        -ms-transform: rotate(45deg);
        transform: rotate(45deg);
        position: absolute;
    }
</style>
