<template>
  <Wrapper :light="true">
    <section class="project">
      <header
        class="page-header"
        :style=""
      >
        <div class="overlay_patern"></div>
        <div class="page-header-title">
          <ul class="breadcrumb">
            <li class="breadcrumb-item">
              <a :href="$site.base">Accueil</a>
            </li>
            <li class="breadcrumb-item">
              <a :href="$site.base + 'projects/'">Projet</a>
            </li>
            <li class="breadcrumb-item">{{ $page.title }}</li>
          </ul>
          <h1>{{ $page.title }}</h1>
          <p>{{ $page.frontmatter.description }}</p>
        </div>
      </header>
      <aside>
        <div class="bottom_header columns">
          <template v-if="!$page.frontmatter.wip">
            <p class="column col-sm-12 col-4 text-center">
              <span>Client //</span> {{ $page.frontmatter.client }}
            </p>
            <p class="column col-sm-12 col-4 text-center">
              <span>Rôle //</span> {{ $page.frontmatter.role }}
            </p>
          </template>
          <template v-else>
            <p class="column col-sm-12 col-8 text-left">
              Projet <span>en cours de développement</span>
            </p>
          </template>
          <p class="column col-sm-12 col-4 text-center">
            <a target="_blank" :href="$page.frontmatter.link">Voir le projet</a>
          </p>
        </div>
      </aside>
      <article class="page section page-content columns">
        <section class="column col-lg-12 col-6">
          <h2>Mission</h2>
          <Content />
        </section>
        <aside class="column col-lg-12 col-6">
          <img
            style="width: 100%"
            :src="
              $withBase('/img/projects/' + $page.frontmatter.missionPicture)
            "
            alt=""
          />
        </aside>
        <aside class="palette-list columns oneline">
          <div
            class="palette column col-lg-auto"
            v-for="e in $page.frontmatter.listElements"
          >
            <div class="color">
              <img
              :src="$withBase('/img/' + e.img)"
            >
            </div>
            <div class="palette-title">
              <h4>{{ e.name }}</h4>
              <p>{{ e.text }}</p>
            </div>
          </div>
        </aside>
        <footer class="column col-12">
          <img
            style="width: 100%"
            :src="$withBase('/img/projects/' + $page.frontmatter.bottomPicture)"
            alt=""
          />
        </footer>
      </article>
    </section>
  </Wrapper>
</template>

<script>
import Wrapper from "../components/Wrapper.vue";
export default {
  data() {
    return {
      nav: false,
      isSidebarOpen: false,
    };
  },
  components: {
    Wrapper,
  },
};
</script>

<style
  src="../websylvain-styles/base/spectre/spectre.min.css"
  lang="css"
></style>
<style
  src="../websylvain-styles/base/spectre/spectre-icons.min.css"
  lang="css"
></style>
<style
  src="../websylvain-styles/base/spectre/spectre-exp.min.css"
  lang="css"
></style>
<style src="../websylvain-styles/app.styl" lang="stylus"></style>

<style lang="stylus">
@require '../websylvain-styles/theme/variables.styl'
.project
    .page-header
        height: 100vh;
        text-align: center;
        position relative
        margin: 0px;
        .page-header-title
            position: absolute;
            top: 50%;
            left: 50%;
            width: 100%;
            transform: translate(-50%, -50%);
            -webkit-transform: translate(-50%, -50%);
            padding : 10%;

    .bottom_header
        background-color: $main_color;
        width: 100%;
        margin: 0px 0px 130px 0px;
        padding: 0% 10% 0% 10%;
        p.column
            margin-top :1.2rem;
            span
                text-transform : uppercase;

    .palette-list
        margin: 50px 0px 50px 0px;
        .palette
            .palette-title
                margin-top : 50px;
                text-align: center;
            .color
                width: 160px;
                height: 160px;
                margin: 0 auto;
                background-color: $main_color;
                box-shadow: 0 5px 20px 0 rgba(0,0,0,.33);
                border-radius: 50%;
                overflow: hidden;
                display: flex;
                flex-direction: column;  
                justify-content: center;
                align-items: center;
                img
                  max-width: 50%;


@media screen and (min-width: $MQMobile) {
    .project{
        .page-header{
            height : 70vh!important;
        }
    }
}


.site-content
  .page, .post
    padding: 0px 11%;
  .toped
    padding-top:200px;
</style>
