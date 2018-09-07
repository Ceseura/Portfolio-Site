<template>
    <div class='contact-card'>
      <div class='my-name'> Alexander Liang </div>
      <div class='contact-icon-box'>
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
  width: 100%;
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
  left: 65%;
  transform: translate(-50%, -50%);
}

.circle-decor {
  background-color: cyan;
  width: 20px;
  height: 20px;
  border-radius: 10px;
  margin: 15px 20px;
  display: inline-block;
}

.email {
  background-image: url('../assets/email_dark.png');
  background-size: 50px 50px;
}
.email:hover {
  background-image: url('../assets/email_light.png');
}

.github {
  background-image: url('../assets/github_dark.png');
  background-size: 50px 50px;
}
.github:hover {
  background-image: url('../assets/github_light.png');
}

.linkedin {
  background-image: url('../assets/linkedin_dark.png');
  background-size: 50px 50px;
}
.linkedin:hover {
  background-image: url('../assets/linkedin_light.png');
}

.resume {
  background-image: url('../assets/resume_dark.png');
  background-size: 50px 50px;
}
.resume:hover {
  background-image: url('../assets/resume_light.png');
}

.link-circle {
  height: 50px;
  width: 50px;
  margin: 0 20px;
  display: inline-block;
}

.link-circle:hover {
  cursor: pointer;
}
</style>

