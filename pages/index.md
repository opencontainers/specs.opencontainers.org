---
layout: home
title: RFC Jekyll
permalink: /
---

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap");

/* Adapted from https://codepen.io/havardob/pen/BapJYMg*/

body {
  font-family: "Inter", sans-serif;
  line-height: 1.5;
  min-height: 100vh;
  display: flex;
  align-items: top;
  justify-content: center;
}

.checkbox-group {
  justify-content: left;
  width: 90%;
  margin-left: auto;
  margin-right: auto;
  max-width: 600px;
  height: 100%;
  margin-top:200px;
}

@media (min-width: 600px) {
  .checkbox-group {
    display: flex;
  }
}

.checkbox-group > * {
  margin: 0.5rem 0.5rem;
}

.checkbox-group-legend {
  font-size: 1.5rem;
  font-weight: 700;
  color: #9c9c9c;
  text-align: left;
  line-height: 1.125;
  margin-bottom: 1.25rem;
}

.checkbox-input {
  clip: rect(0 0 0 0);
  -webkit-clip-path: inset(100%);
          clip-path: inset(100%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
.checkbox-input:checked + .checkbox-tile {
  border-color: #2260ff;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
}
.checkbox-input:checked + .checkbox-tile:before {
  transform: scale(1);
  opacity: 1;
  background-color: #2260ff;
  border-color: #2260ff;
}
.checkbox-input:checked + .checkbox-tile .checkbox-icon, .checkbox-input:checked + .checkbox-tile .checkbox-label {
  color: #2260ff;
}
.checkbox-input:focus + .checkbox-tile {
  border-color: #2260ff;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1), 0 0 0 4px #b5c9fc;
}
.checkbox-input:focus + .checkbox-tile:before {
  transform: scale(1);
  opacity: 1;
}

.checkbox-tile {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 10rem;
  min-height: 10rem;
  border-radius: 0.5rem;
  border: 2px solid #b5bfd9;
  background-color: #fff;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  transition: 0.15s ease;
  position: relative;
}
.checkbox-tile:before {
  content: "";
  position: absolute;
  display: block;
  width: 1.25rem;
  height: 1.25rem;
  border-radius: 50%;
  top: 0.25rem;
  left: 0.25rem;
  opacity: 0;
  transform: scale(0);
  transition: 0.25s ease;
}
.checkbox-tile:hover {
  border-color: #2260ff;
}
.checkbox-tile:hover:before {
  transform: scale(1);
  opacity: 1;
}

.checkbox-icon {
  transition: 0.375s ease;
  color: #494949;
}
.checkbox-icon svg {
  width: 3rem;
  height: 3rem;
}

.checkbox-label {
  color: #707070;
  transition: 0.375s ease;
  text-align: center;
}
</style>

<fieldset class="checkbox-group" style="border:none">
  <legend class="checkbox-group-legend">OpenContainers Specifications</legend>
  {% for spec in site.data.specs %}
  <div class="checkbox" id="spec-{{ spec[0] }}">
    <label class="checkbox-wrapper">
      <input type="checkbox" class="checkbox-input" />
      <span class="checkbox-tile">
        <span class="checkbox-icon">
        </span>
        <span class="checkbox-label">{{ spec[1].name }}</span>
        {% for version in spec[1].versions %}
         <a class="clickme" href="#" data-id="{{ spec[0] }}" version-id="{{ version }}">{{ version }}</a>{% endfor %}
      </span>
    </label>
  </div>
{% endfor %}
</fieldset>

<script
  src="{{ site.baseurl }}/assets/js/jquery-3.3.1/jquery-3.3.1.min.js"
  integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8="
  crossorigin="anonymous"></script>

<script>
$(".clickme").click(function(){
    var url = $(this).attr("data-id") + "?v=" + $(this).attr('version-id'); 
    document.location = "{{ site.baseurl }}/" + url;
})
</script>
