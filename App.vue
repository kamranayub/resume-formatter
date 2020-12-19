<script>
import TextEditor from "./editors/TextEditor";

export default {
  data() {
    return {
      fullName: "Full Name",
      byline: "Byline",
    };
  },
  updated() {
    console.log(this.$data);
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
        <p>Overview and introduction</p>
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

<style>
body {
  padding: 1em;
  max-width: 1280px;
  margin: 0 auto;
  font: 95%/1.3 Source Sans Pro, Calibri, Arial, Verdana;
  background: white;
  color: #333;
}

* {
  box-sizing: border-box;
}

footer {
  clear: both;
  text-align: center;
  color: #808080;
  padding: 3em 0 2em 0;
}
footer span {
  color: firebrick;
}

@media screen {
  .hide-screen {
    display: none;
  }
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
}

a {
  color: brown;
  text-decoration: none;
}

p {
  margin: 0 0 0.5em 0;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

@media print, (min-width: 1070px) {
  .half {
    width: 50%;
  }
  .left {
    float: left;
  }
  .right {
    float: right;
  }
}

/**
 * Header styles
 */
header {
  position: relative;
  border-bottom: 2px solid #808080;
  overflow: hidden;
  padding-bottom: 1em;
  min-height: 170px;
  text-align: center;
}
header h1 {
  font-size: 2em;
}
header h1 img {
  display: block;
  margin: 0 auto;
  width: 80px;
  height: 80px;
  border-radius: 80px;
}
header h1 small {
  display: block;
  font-size: 0.5em;
  font-weight: normal;
  color: #808080;
  margin-top: 0.5em;
}

/**
 * Header responsive styles
 */
@media print, (min-width: 695px) {
  body {
    font-size: 130%;
  }

  header {
    text-align: left;
  }
  header h1 img {
    display: inline-block;
    vertical-align: middle;
    float: left;
    margin-bottom: 1em;
    margin-right: 0.5em;
  }
  header section {
    float: left;
    width: 60%;
  }
  header ul {
    float: right;
    width: 40%;
  }
  header ul li {
    text-align: right;
  }
}

/**
 * Section Styles
 */
.resume > section {
  clear: both;
  overflow: auto;
}
.resume > section .qr-code {
  float: right;
  width: 190px;
  text-align: right;
}
.resume > section .qr-code img {
  max-width: 100%;
}
.resume > section .qr-code em {
  font-style: normal;
  color: #808080;
}
.resume > section h2 {
  padding-top: 1em;
  border-top: 3px double #dadada;
}
.resume > section h2 img {
  max-width: 90%;
}
.resume > section h2 small {
  color: #c0c0c0;
  font-size: 0.5em;
  margin-top: 0.5em;
  line-height: 1em;
  display: block;
  font-weight: normal;
}
.resume > section:first-of-type h2 {
  border-top: 3px solid #c0c0c0;
}
.resume > section .content {
  padding-top: 1.2em;
  border-top: 3px solid #c0c0c0;
}
.resume > section .content h4 {
  margin-bottom: 0.5em;
  text-transform: uppercase;
}
.resume > section .section-header {
  margin-bottom: 0.5em;
  overflow: hidden;
  border-bottom: 1px solid #ccc;
  padding-bottom: 3px;
}
.resume > section .section-header.orphan {
  margin: 0;
  border: none;
}
.resume > section .section-header:not(:first-child) {
  padding-top: 1em;
}
.resume > section .section-header h3 {
  font-size: 1.5em;
  text-transform: uppercase;
}
.resume > section .section-header h4 {
  font-size: 0.9em;
}
.resume > section .section-header h5 {
  font-size: 0.9em;
  font-weight: normal;
  font-style: italic;
}
.resume > section .section-header .section-date {
  list-style-type: none;
  padding: 0;
  margin: 0;
  clear: none;
  font-size: 0.9em;
}
.resume > section .content ul {
  clear: left;
  list-style-type: square;
  margin-left: 1em;
  padding-left: 1em;
  margin-bottom: 1em;
}
.resume > section .highlight {
  margin-left: 2em;
  color: #666;
}

/**
 * Section Responsive Styles
 */
@media print, (min-width: 950px) {
  .resume > section h2 {
    float: left;
    width: 17%;
  }

  .resume > section .content {
    float: left;
    width: 83%;
    padding-left: 0.5em;
    border-left: 1px solid #dadada;
  }
}
@media print, (min-width: 640px) {
  div.words p,
  div.words ul {
    max-width: 80%;
  }
}
@media print, (min-width: 960px) {
  .resume > section .section-header .section-desc {
    float: left;
    width: 70%;
  }
  .resume > section .section-header .section-date {
    float: right;
    width: 30%;
  }
  .resume > section .section-header .section-date li {
    text-align: right;
  }

  div.words p,
  div.words ul {
    max-width: 65%;
  }
}

div.half h4 {
  margin-bottom: 1em;
}

ul.skills li em {
  color: #808080;
  font-style: normal;
  font-weight: bold;
}

.inline-skills {
  color: gray;
}

.extras img {
  margin: 1em 0;
}

.company > h2 img {
  max-width: 90%;
}
</style>
