<script>
import TextEditor from "./editors/TextEditor.vue";

const STORAGE_CONTAINER = "resume-0.1";

export default {
  name: "App",
  data() {
    const DEFAULTS = {
      fullName: "Full Name",
      byline: "Byline",
      aboutMe: "Introduction and overview",
    };

    let dataFromStorage;
    if (window.localStorage) {
      dataFromStorage = window.localStorage.getItem(STORAGE_CONTAINER);
      if (dataFromStorage) {
        dataFromStorage = JSON.parse(dataFromStorage);
        return { ...DEFAULTS, ...dataFromStorage };
      }
    }

    return DEFAULTS;
  },
  updated() {
    if (window.localStorage) {
      window.localStorage.setItem(
        STORAGE_CONTAINER,
        JSON.stringify(this.$data)
      );
    }
  },
  components: {
    TextEditor,
  },
};
</script>

<template>
  <div class="resume">
    <header>
      <section>
        <h1>
          <text-editor v-model="fullName" />
          <small><text-editor v-model="byline" /></small>
        </h1>
      </section>

      <ul id="contact">
        <li>
          <i class="fa fa-icon">icon</i> label/<a href="https://link">name</a>
        </li>
      </ul>
    </header>

    <section>
      <h2>About Me</h2>

      <div class="content words">
        <p><text-editor v-model="aboutMe" /></p>
      </div>
    </section>

    <section>
      <h2>
        Relevant Experience
        <small
          >For complete employment history, see my
          <a href="https://linkedin.com/">LinkedIn</a>
          profile</small
        >
      </h2>

      <div class="content">
        <div class="section-header">
          <div class="section-desc">
            <h3>Employer</h3>
          </div>
          <ul class="section-date">
            <li>Location</li>
            <li>Start &mdash; End</li>
          </ul>
        </div>

        <div class="section-header">
          <div class="section-desc">
            <h4>Team or Position</h4>
            <h5>Role</h5>
          </div>
          <ul class="section-date">
            <li>Start &mdash; End</li>
          </ul>
        </div>

        <p class="inline-skills">Skills used in role</p>

        <div class="words">
          <!--<img class="right" src="img/icon.svg" width="90" />-->

          <p>Role overview and accomplishments</p>
        </div>
      </div>
    </section>
    <section class="page-break">
      <h2>Section</h2>

      <div class="content">
        <div class="half left">
          <h4>Section heading</h4>

          <p>Section byline</p>

          <ul class="skills">
            <li>List item</li>
          </ul>
        </div>
        <div class="half right">
          <h4>Section heading</h4>

          <p>Section byline</p>

          <ul class="skills">
            <li>List item</li>
          </ul>
        </div>
      </div>
    </section>

    <section>
      <h2>Education</h2>

      <div class="content">
        <div class="section-header orphan">
          <div class="section-desc">
            <h3>School</h3>
            <p>
              <em>Department</em> <br />Degree, Major in
              <strong>Major</strong> and minor in <strong>Minor</strong>
            </p>
          </div>
          <ul class="section-date">
            <li>Location</li>
            <li>Graduation date</li>
          </ul>
        </div>
      </div>
    </section>

    <footer class="hide-print">
      Designed with 💘 by Kamran Ayub. Print in browser for PDF.
    </footer>
  </div>
</template>
