<template>
  <h1>Hello</h1>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  width: 8.5in;

  font: 12pt/1.4em Calibri, Helvetica, Arial, Verdana;
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
  color: inherit;
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

.left {
  float: left;
}
.right {
  float: right;
}

.half {
  width: 50%;
}

div#header {
  border-bottom: 2px solid #808080;
  overflow: hidden;
  padding-bottom: 1em;
}
div#header h1 {
  font-size: 2em;
  float: left;
}
div#header ul {
  float: right;
}
div#header ul li {
  text-align: right;
}

div.section {
  clear: both;
}
div.section h2 {
  float: left;
  width: 20%;
  padding-top: 15px;
  border-top: 3px double #dadada;
}
div.section h2#top {
  border-top: 3px solid #c0c0c0;
}
div.section .content {
  float: left;
  width: 80%;
  padding: 15px 0 0 5px;
  border-top: 3px solid #c0c0c0;
  border-left: 1px solid #dadada;
}
div.section .section-header {
  margin-bottom: 0.5em;
  overflow: hidden;
  border-bottom: 1px solid #ccc;
  padding-bottom: 3px;
}
div.section .section-header.orphan {
  margin: 0;
  border: none;
}
div.section .section-header h3 {
  font-size: 1.1em;
  text-transform: uppercase;
}
div.section .section-header h4 {
  font-size: 0.9em;
}
div.section .section-header h5 {
  font-size: 0.9em;
  font-weight: normal;
  font-style: italic;
}
div.section .section-header ul.date-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
  float: right;
  clear: none;
}
div.section .section-header ul.date-list li {
  text-align: right;
}
div.section .content ul {
  clear: left;
  list-style-type: square;
  margin-left: 1em;
  padding-left: 1em;
  margin-bottom: 1em;
}

div.half h4 {
  margin-bottom: 1em;
}
</style>
