<template>
  <div class="home">
    <Hero :header="header"
          :subhead="subhead"
          showButton
          showImage
          animations />
    <section class="about">
      <div class="container">
        <h2>Marcin Bonisławski</h2>
        <h3>24 lata, absolwent Politechniki Warszawskiej</h3>
        <p>Od 3 lat zajmuję się programowaniem webowym.
        Tworzę strony internetowe, koduję landing page oraz aplikacje www.
        Każdą wolną chwilę staram się poświęcać na poznawanie nowych zagadnień i technologii. </p>
      </div>
    </section>
    <section class="projects">
      <div class="container">
        <div class="projects-container f-row">
          <ProjectType v-for="project in projectTypes"
            :key="'item-'+project.icon"
            :header="project.header"
            :icon="project.icon"
            :description="project.description"/>
        </div>
      </div>
    </section>
    <section class="completed-projects">
      <div class="container">
        <h2>Zrealizowane projekty</h2>
        <div class="projects-holder f-row">
          <CompletedProject v-for="n in 3" :key="'item-'+n" />
        </div>
      </div>
      <router-link class="btn secondary" to="/portfolio">Zobacz więcej</router-link>
    </section>
    <section class="collaboration">
      <div class="container">
        <h2>Interesuje Cię współpraca?</h2>
        <p>Jeśli interesuje Cię współpraca lub masz jakieś pytania - skontaktuj się ze mną</p>
        <router-link class="btn" to="/kontakt">Kontakt</router-link>
      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import Hero from '@/components/Hero.vue';
import ProjectType from '@/components/ProjectType.vue';
import CompletedProject from '@/components/CompletedProject.vue';

export default {
  name: 'home',
  components: {
    Hero,
    ProjectType,
    CompletedProject,
  },
  data() {
    return {
      projectTypes: [
        {
          header: 'Design',
          icon: 'design-icon',
          description: 'Tworzę indywidualne, spersonalizowane projekty stron internetowych na podstawie wymagań klienta.',
        },
        {
          header: 'Statyczna strona www',
          icon: 'coding',
          description: 'Przenoszę pomysły z projektu graficznego do przeglądarki użytkownika dbając o optymalizację i jakość kodu.',
        },
        {
          header: 'System CMS',
          icon: 'cms',
          description: 'Wdrażam system zarządzania treścią (CMS), aby umożliwić użytkownikowi łatwą, samodzielną edycję treści.',
        },
      ],
      header: 'Cześć, jestem <span>Marcin</span>',
      subhead: 'Projektuję oraz koduję strony internetowe',
    };
  },
};
</script>

<style lang="scss">
  .about {
    background-color: #293347;
    padding: 60px 0;
    padding-bottom: 250px;
    @media(max-width: 720px) {
      padding-bottom: 80px;
    }

    h2 {
      font-size: 32px;
      color: #fff;
      margin-bottom: 8px;
      font-weight: 600;
      @media(max-width: 520px) {
        font-size: 28px;
      }
    }

    h3 {
      font-weight: 400;
      font-size: 16px;
      color: #fff;
      margin-bottom: 24px;
    }

    p {
      font-weight: 300;
      font-size: 16px;
      color: #fff;
      max-width: 600px;
      margin: auto;
      line-height: 1.64;
    }
  }

  .btn {
    margin-top: 60px;
    @media(max-width: 1075px) {
        margin-top: 30px;
    }
  }

  .projects-container {
    max-width: 1040px;
    justify-content: center;
    align-items: flex-start;
    margin: auto;
    border-radius: 4px;
    overflow: hidden;
    position: absolute;
    left: 0;
    right: 0;
    top: -150px;
    -webkit-box-shadow: 1px 1px 11px -4px rgba(41,51,71,.3);
    -moz-box-shadow: 1px 1px 11px -4px rgba(41,51,71,.3);
    box-shadow: 1px 1px 11px -4px rgba(41,51,71,.3);
    @media(max-width: 1075px) {
        flex-wrap: wrap;
        justify-content: center;
        box-shadow: none;
    }
    @media(max-width: 720px) {
        position: relative;
        flex-direction: column;
        align-items: center;
        top: unset;
        padding-top: 60px;
    }
  }

    .completed-projects {
      padding-top: 240px;
      padding-bottom: 60px;
      @media(max-width: 1075px) {
        padding-top: 530px;
      }
      @media(max-width: 720px) {
        padding-top: 60px;
      }

      h2 {
        font-size: 32px;
        color: #293347;
        @media(max-width: 520px) {
          font-size: 28px;
        }
      }
    }

    .projects-holder {
      padding-top: 50px;
      max-width: 1140px;
      margin: auto;
      justify-content: space-between;
      @media(max-width: 1200px) {
        width: 1000px;
      }
      @media(max-width: 1075px) {
        width: 100%;
        flex-wrap: wrap;
        flex-direction: column;
      }
    }

    .collaboration {
      background-color: #fff;
      padding: 60px 0;

      h2 {
        font-size: 32px;
        color: #293347;
        margin-bottom: 24px;
        @media(max-width: 520px) {
          font-size: 28px;
        }
      }
    }
</style>
