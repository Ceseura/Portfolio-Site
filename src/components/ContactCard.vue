<template>
    <div class='contact-card'>
        <!-- <div class='circle-decor' />
        <div class='info-card left'>
            <div> Name: </div>
            <div> Email: </div>
            <div> Github: </div>
            <div> Resume: </div>
        </div>
        <div class='info-card right'>
             <div> Alexander Liang </div>
             <div> myboringemail4@gmail.com </div>
             <div><a href='https://github.com/Karavis/'> Karavis </a></div>
             <div><a href='https://drive.google.com/file/d/0Bzt4QEceUnY6NFhXRTIwSy1JMXM/view'> Here </a></div>
        </div> -->
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
  background-image: url('../assets/tilable2.jpg');

  margin-top: -100vh;
  position: sticky;
  top: 0;
}

.info-card {
  display: inline-block;
  width: 25%;
  position: absolute;
  padding: 40px 20px;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
  font-size: 1.3em;
}

.left {
  left: 25%;
  text-align: right;
}

.right {
  left: 50%;
  text-align: left;
}

.circle-decor {
  background-color: darkcyan;
  width: 70px;
  height: 70px;
  border-radius: 35px;
  margin: auto;
}
</style>

