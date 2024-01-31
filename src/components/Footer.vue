<template>
  <footer class="nav-footer" id="footer">
    <!--
    <section class="sitemap">
      <router-link to="/">
        <img svg-inline class="logoicon" src="@/assets/logoicon.svg" alt="Guardian-scan-logoicon">
      </router-link>
      <div>
        <h3>Docs</h3>
        <a href="https://developers.Guardiansql.io/docs/intro">Getting Started</a>
        <a href="https://developers.Guardiansql.io/docs/api-json-rpc">API Reference</a>
      </div>
      <div>
        <h3>Community</h3>
        <a
          href="https://stackoverflow.com/search?q=Guardiansql"
          target="_blank"
          rel="noreferrer noopener"
        >Stack Overflow</a>
        <a href="https://gitter.im/GuardianSQL/GuardianSQL">Gitter Chat</a>
        <a href="https://twitter.com/GuardianLabs" target="_blank" rel="noreferrer noopener">Twitter</a>
      </div>
      <div>
        <h3>More</h3>
        <a href="https://medium.com/@Guardian_labs">Blog</a>
        <a
          class="github-button"
          href="https://github.com/GuardianSQL/GuardianSQL"
          data-icon="octicon-star"
          data-count-href="/GuardianSQL/GuardianSQL/stargazers"
          data-show-count="true"
          data-count-aria-label="# stargazers on GitHub"
          aria-label="Star this project on GitHub"
        >Star</a>
      </div>
    </section>
    
    <a
      href="https://Guardiansql.io"
      target="_blank"
      rel="noreferrer noopener"
      class="Guardian-icon"
    >
      <img
        src="https://developers.Guardiansql.io/img/horizontal_logo.svg"
        alt="GuardianSQL"
        width="170"
        height="45"
      >
    </a>
    -->
    <section class="copyright">{{ `Copyright © ${new Date().getFullYear()} Guardian SQL` }}</section>
  </footer>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Footer extends Vue {}
</script>

<style lang="scss" scoped>
.nav-footer {
  background: #20232a;
  border: none;
  color: #202020;
  font-size: 15px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-weight: 400;
  line-height: 24px;
  padding-bottom: 2em;
  padding-top: 2em;
  position: relative;
}
@media only screen and (min-width: 1024px) {
  .nav-footer {
    flex-shrink: 0;
  }
}
.nav-footer .sitemap {
  display: flex;
  justify-content: space-between;
  margin: 0 auto 3em;
  max-width: 1080px;
}
.nav-footer .sitemap .logoicon {
  height: 58px;
  margin-right: 32px;
  margin-bottom: 32px;
  opacity: 0.9;
  transition: opacity 0.15s ease-in-out;
}
.nav-footer .sitemap .logoicon:hover {
  opacity: 1;
}
.nav-footer .sitemap div {
  flex: 1;
}
.nav-footer .sitemap .nav-home {
  display: table;
  height: 72px;
  margin: -12px 20px 0 0;
  opacity: 0.4;
  padding: 10px;
  transition: opacity 0.15s ease-in-out;
  width: 72px;
}
.nav-footer .sitemap .nav-home:focus,
.nav-footer .sitemap .nav-home:hover {
  opacity: 1;
}
@media only screen and (max-width: 735px) {
  .nav-footer .sitemap {
    display: flex;
    flex-direction: column;
    margin: 0 2em 3em;
    width: calc(100% - 4em);
  }
  .nav-footer .sitemap > div {
    margin-bottom: 18px;
  }
}
.nav-footer .sitemap a {
  color: hsla(0, 0%, 100%, 0.6);
  display: block;
  margin: 2px -10px;
  padding: 3px 10px;
}
.nav-footer .sitemap a:focus,
.nav-footer .sitemap a:hover,
.nav-footer .sitemap h3 > a:focus,
.nav-footer .sitemap h3 > a:hover {
  color: #fff;
  text-decoration: none;
}
.nav-footer .sitemap h3,
.nav-footer .sitemap h6 {
  margin: 0 0 10px;
}
.nav-footer .sitemap h3,
.nav-footer .sitemap h3 > a,
.nav-footer .sitemap h6,
.nav-footer .sitemap h6 > a {
  color: #fff;
}
.nav-footer .sitemap h3 > a,
.nav-footer .sitemap h6 > a {
  margin: 0 -10px;
}
.nav-footer .guardian-icon {
  display: block;
  margin: 1em auto;
  opacity: 0.4;
  transition: opacity 0.15s ease-in-out;
  width: 170px;
}
.nav-footer .guardian-icon:hover {
  opacity: 1;
}
.nav-footer .copyright {
  color: hsla(0, 0%, 100%, 0.4);
  text-align: center;
}
.nav-footer .social {
  padding: 5px 0;
}
</style>
