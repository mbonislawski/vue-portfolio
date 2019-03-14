<template>
  <div id="app">
    <div id="nav">
      <div class="container f-row">
        <router-link class="logo-holder" to="/">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 450 562.54"><defs></defs><title>MB</title><g id="Layer_2" data-name="Layer 2"><g id="art2"><path class="logo-fill" d="M225,0,32.72,111A65.44,65.44,0,0,0,0,167.7V394.86a65.44,65.44,0,0,0,32.72,56.67l17.28,10V171.06l50-28.87V490.38l50,28.87V113.32l50-28.87V548.11l25,14.43L417.19,452A65.44,65.44,0,0,0,450,395.26v-228a65.44,65.44,0,0,0-32.81-56.72Zm25,478.59V352.06a31.21,31.21,0,0,1,27.33-31l105.45-13.2A15.31,15.31,0,0,1,400,323.09v20a84.76,84.76,0,0,1-42.38,73.41ZM382.78,256.22,277.33,243a31.21,31.21,0,0,1-27.33-31V84l107.62,62.13A84.76,84.76,0,0,1,400,219.52V241A15.31,15.31,0,0,1,382.78,256.22Z"></path></g></g></svg>
        </router-link>
        <div class="menu-items">
          <router-link to="/">Home</router-link>
          <router-link to="/portfolio">Portfolio</router-link>
          <router-link to="/kontakt">Kontakt</router-link>
        </div>
      </div>
    </div>
    <router-view/>
    <footer>
      <div class="container">
        <div class="logo-holder">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 450 562.54"><defs></defs><title>MB</title><g id="Layer_2" data-name="Layer 2"><g id="art2"><path class="logo-fill" d="M225,0,32.72,111A65.44,65.44,0,0,0,0,167.7V394.86a65.44,65.44,0,0,0,32.72,56.67l17.28,10V171.06l50-28.87V490.38l50,28.87V113.32l50-28.87V548.11l25,14.43L417.19,452A65.44,65.44,0,0,0,450,395.26v-228a65.44,65.44,0,0,0-32.81-56.72Zm25,478.59V352.06a31.21,31.21,0,0,1,27.33-31l105.45-13.2A15.31,15.31,0,0,1,400,323.09v20a84.76,84.76,0,0,1-42.38,73.41ZM382.78,256.22,277.33,243a31.21,31.21,0,0,1-27.33-31V84l107.62,62.13A84.76,84.76,0,0,1,400,219.52V241A15.31,15.31,0,0,1,382.78,256.22Z"></path></g></g></svg>
        </div>
        <p>Znajdziesz mnie również</p>
        <div class="socials f-row">
          <a href="https://github.com/mbonislawski/" target="_blank" class="single-social github">
            <img src="../src/assets/images/github.svg">
          </a>
          <a href="https://www.linkedin.com/in/marcin-bonislawski/" target="_blank" class="single-social linkedin">
            <img src="../src/assets/images/linkedin.svg">
          </a>
          <a href="https://www.facebook.com/marcin.bonislawski" target="_blank" class="single-social facebook">
            <img src="../src/assets/images/facebook.svg">
          </a>
          <a href="https://www.instagram.com/cinkooooo/" target="_blank" class="single-social instagram">
            <img src="../src/assets/images/instagram.svg">
          </a>
          <a href="mailto:kontakt@mbonislawski.pl" class="single-social mail">
            <img src="../src/assets/images/mail.svg">
          </a>
        </div>
      </div>
      <div class="copy">
        <p>&copy; Handcrafted by Marcin Bonisławski {{currYear}}</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currYear: null,
    };
  },
  methods: {
    handleScroll() {
      const nav = document.getElementById('nav');
      if (window.scrollY > 0) {
        nav.classList.add('sticky');
      } else {
        nav.classList.remove('sticky');
      }
    },
  },
  created() {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  mounted() {
    this.currYear = new Date().getFullYear();
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Asap:400,500,600,700|Open+Sans:300,400,600,700&subset=latin-ext');

$green: #17B890;
$purple: #6F2DBD;
$dark: #293347;
$black: #202C39;
$grey: #F7F7F7;

// reset
body,
h1,
h2,
h3,
h4,
h5,
p,
a,
ul,
li {
  margin: 0;
  padding: 0;
}

body {
  background-color: #F7F7F7;
}

ul, li {
  list-style: none;
}

a {
  text-decoration: none;
  cursor: pointer;
}

* {
  box-sizing: border-box;
  max-width: 100%;
  outline: none;
}
// reset-end

#app {
  h1, h2, h3, h4, h5 {
    font-family: 'Asap', sans-serif;
  }

  font-family: 'Open Sans', sans-serif;
}

.container {
  max-width: 100%;
  width: 1340px;
  margin:auto;
  text-align: center;
  position: relative;

  @media(max-width: 1367px) {
    padding: 0 24px;
  }
}

.f-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#nav {
  padding: 24px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  margin: auto;
  transition: all .3s;
  z-index: 10;

  &.sticky {
    background-color: #fff;
    -webkit-box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
    -moz-box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
    box-shadow: 0px 1px 20px -9px rgba(41,51,71,0.4);
  }

  .logo-holder {
    width: 40px;
  }

  .logo-fill {
    fill: $green;
  }

  .menu-items {
    padding: 0 16px;

    a {
      font-weight: 600;
      color: $dark;
      padding: 0 16px;
      transition: color .3s;
      &:hover {
        color: $green;
      }
      &:last-of-type {
        padding-right: 0;
      }
      &.router-link-exact-active {
        color: $green;
      }
    }
  }

  .container {
    @media(max-width: 500px) {
      padding: 0;
    }
  }
}

footer {
  background-color: $dark;
  padding: 60px 0;
  padding-bottom: 0;
  text-align: center;

  .container {
    padding-bottom: 60px;
  }

  .logo-holder {
    width: 40px;
    margin: auto;
    margin-bottom: 24px;

    .logo-fill {
      fill: #FFFFFF;
    }
  }

  p {
    color: #fff;
  }

  .socials {
    padding: 40px 0;
    max-width: 300px;
    margin: auto;

    .single-social {
      width: 40px;
      height: 40px;
      border: 2px solid rgba(255, 255, 255, .5);
      border-radius: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all .3s;

      &:hover {
        background-color: $green;
        border-color: $green;
      }

      &.github {
        &:hover {
          background-color: #6cc644;
          border-color: #6cc644;
        }
      }

      &.facebook {
        &:hover {
          background-color: #3b5998;
          border-color: #3b5998;
        }
      }

      &.linkedin {
        &:hover {
          background-color: #0077B5;
          border-color: #0077B5;
        }
      }

      &.instagram {
        &:hover {
          background-color: #bc2a8d;
          border-color: #bc2a8d;
        }
      }

      img {
        max-width: 24px;
        margin: auto;
      }
    }
  }

  .copy {
    background-color: $black;
    padding: 12px 0;

    p {
      font-size: 12px;
      font-weight: 300;
      letter-spacing: .6px;
    }
  }
}
</style>
