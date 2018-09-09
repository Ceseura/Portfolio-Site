<template>
    <div class='contact-card'>
      <div class='my-name'> Alexander Liang </div>
      <div class='contact-icon-box cib-responsive'>
        <div class='circle-decor'/>
        <a href='https://github.com/Karavis'>
          <div class='github link-circle'/>
        </a>
        <a href='mailto:myboringemail4@gmail.com'>
          <div class='email link-circle'/>
        </a>
        <a href='https://www.linkedin.com/in/alexander-liang-7070b9167/'>
          <div class='linkedin link-circle'/>
        </a>
        <a href='https://drive.google.com/file/d/0Bzt4QEceUnY6NFhXRTIwSy1JMXM/view'>
          <div class='resume link-circle'/>
        </a>
        <div class='circle-decor'/>
        <!-- Email/Github/Linkedin/Resume -->
      </div>
    </div>
</template>

<script>
export default {};
</script>

<style scoped>
.contact-card {
  width: 100vw;
  max-width: 100%;
  height: 100vh;
  background-image: url('../assets/tilable1.jpg');

  margin-top: -100vh;
  position: sticky;
  top: 0;
}

.my-name {
  width: 80%;
  padding: 0 10%;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: calc(3em + 2vw);
  color: white;
  font-family: 'Montserrat', sans-serif;
  letter-spacing: 0.1em;
  word-spacing: 0.5em;
}

.contact-icon-box {
  position: absolute;
  top: 62.5%;
  transform: translate(-50%, -50%);
  width: 50%;
  max-width: 500px;
}

@media (min-width: 1400px) {
  .cib-responsive {
    left: 65%;
  }
}

@media (max-width: 1399px) {
  .cib-responsive {
    left: 50%;
  }
}

.circle-decor {
  background-color: cyan;
  width: 3%;
  padding-top: 3%;
  border-radius: 50%;
  margin: 15px 1.5%;
  display: inline-block;
}

.email {
  background-image: url('../assets/button-presets/email_dark.png');
  background-size: cover;
}
.email:hover {
  background-image: url('../assets/button-presets/email_light.png');
}

.github {
  background-image: url('../assets/button-presets/github_dark.png');
  background-size: cover;
}
.github:hover {
  background-image: url('../assets/button-presets/github_light.png');
}

.linkedin {
  background-image: url('../assets/button-presets/linkedin_dark.png');
  background-size: cover;
}
.linkedin:hover {
  background-image: url('../assets/button-presets/linkedin_light.png');
}

.resume {
  background-image: url('../assets/button-presets/resume_dark.png');
  background-size: cover;
}
.resume:hover {
  background-image: url('../assets/button-presets/resume_light.png');
}

.link-circle {
  width: 10%;
  padding-top: 10%;
  margin: 0 5%;
  display: inline-block;
}

.link-circle:hover {
  cursor: pointer;
}
</style>
