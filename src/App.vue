<script>
import TextEditor from "./editors/TextEditor.vue";

const STORAGE_CONTAINER = "resume-0.1";
const DEFAULTS = {
  fullName: "Full Name",
  byline: "Byline",
  aboutMe: "Introduction and overview",
  links: [
    {
      text: "name@company.com",
    },
    {
      text: "555-444-9999",
    },
  ],
  history: [
    {
      employer: "Employer",
      location: "Location",
      start: "Start",
      end: "End",
      positions: [
        {
          name: "Team or position",
          byline: "Explanation",
          skills: "Skills used in role",
          description: "Role overview and accomplishments",
          start: "Start",
          end: "End",
        },
      ],
    },
  ],
  sections: [
    {
      name: "Section",
      groups: [
        {
          heading: "Section heading",
          byline: "Section byline",
          items: [{ text: "List item" }],
        },
        {
          heading: "Section heading",
          byline: "Section byline",
          items: [{ text: "List item" }],
        },
      ],
    },
  ],
  education: {
    school: "School of Subtle Knox",
    byline: "College of Socks on Fox",
    degree: "Bachelors of Tweedle Beedle Puddle Battles",
    location: "Grox, MT",
    date: "May 2010",
  },
};

export default {
  name: "App",
  data() {
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
  methods: {
    reset() {
      const areYouSure = window.confirm(
        "Are you sure? This will remove all your saved data."
      );

      if (areYouSure && window.localStorage) {
        window.localStorage.setItem(
          STORAGE_CONTAINER,
          JSON.stringify(DEFAULTS)
        );
        window.location.reload();
      }
    },
    print() {
      window.print();
    },
    addContactInfo() {
      this.links.push({
        text: "123 Abc Ln N",
      });
    },
    removeContactInfo(index) {
      this.links.splice(index, 1);
    },
    addEmployer() {
      this.history.push({
        ...DEFAULTS.history[0],
      });
    },
    addPosition(employer) {
      employer.positions.push({
        ...DEFAULTS.history[0].positions[0],
      });
    },
    addSection() {
      this.sections.push({ ...DEFAULTS.sections[0] });
    },
  },
  components: {
    TextEditor,
  },
};
</script>

<template>
  <div class="top-of-page">
    <button @click="reset">Start over</button>
    <button @click="print">Print to PDF</button>
  </div>

  <div class="resume">
    <header>
      <section>
        <h1>
          <text-editor v-model="fullName" />
          <small><text-editor v-model="byline" /></small>
        </h1>
      </section>

      <ul id="contact">
        <li v-for="(link, index) in links">
          <button
            @click="removeContactInfo(index)"
            title="Remove contact info"
            aria-label="remove item"
          >
            <i class="fa fa-minus-circle"></i>
          </button>
          <text-editor v-model="link.text" />
        </li>
        <li>
          <button @click="addContactInfo">
            <i class="fa fa-plus-circle"></i> add contact info
          </button>
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
        <div v-for="item in history">
          <div class="section-header">
            <div class="section-desc">
              <h3><text-editor v-model="item.employer" /></h3>
            </div>
            <ul class="section-date">
              <li><text-editor v-model="item.location" /></li>
              <li>
                <text-editor v-model="item.start" /> &mdash;
                <text-editor v-model="item.end" />
              </li>
            </ul>
          </div>

          <div v-for="position in item.positions">
            <div class="section-header">
              <div class="section-desc">
                <h4><text-editor v-model="position.name" /></h4>
                <h5><text-editor v-model="position.byline" /></h5>
              </div>
              <ul class="section-date">
                <li>
                  <text-editor v-model="position.start" /> &mdash;
                  <text-editor v-model="position.end" />
                </li>
              </ul>
            </div>

            <p class="inline-skills">
              <text-editor v-model="position.skills" />
            </p>

            <div class="words">
              <!--<img class="right" src="img/icon.svg" width="90" />-->

              <text-editor v-model="position.description" />
            </div>
          </div>

          <p>
            <button @click="addPosition(item)">
              <i class="fa fa-plus-circle"></i> add position
            </button>
          </p>
        </div>
        <p>
          <button @click="addEmployer">
            <i class="fa fa-plus-circle"></i> add employer
          </button>
        </p>
      </div>
    </section>

    <section class="page-break" v-for="section in sections">
      <h2><text-editor v-model="section.name" /></h2>

      <div class="content">
        <div class="half" v-for="group in section.groups">
          <h4><text-editor v-model="group.heading" /></h4>

          <p><text-editor v-model="group.byline" /></p>

          <ul class="skills">
            <li v-for="item in group.items">
              <text-editor v-model="item.text" />
            </li>
          </ul>
        </div>
      </div>
    </section>

    <button class="add-section" @click="addSection">
      <i class="fa fa-plus-circle"></i> add section
    </button>

    <section>
      <h2>Education</h2>

      <div class="content">
        <div class="section-header orphan">
          <div class="section-desc">
            <h3><text-editor v-model="education.school" /></h3>
            <p>
              <em><text-editor v-model="education.byline" /></em>
              <br /><text-editor v-model="education.degree" />
            </p>
          </div>
          <ul class="section-date">
            <li><text-editor v-model="education.location" /></li>
            <li><text-editor v-model="education.date" /></li>
          </ul>
        </div>
      </div>
    </section>

    <footer class="hide-print">
      Designed with 💘 by Kamran Ayub. Print in browser for PDF.
    </footer>
  </div>
</template>
