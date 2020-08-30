<template>
    <div class="body-container">
      <div class="body-black__left"></div>
      <div class="body-img"></div>
      <div id="app">
        <div class="app__img"></div>
        <Header />
        <Main @finish="finish" />
        <Footer :footer="views" />
      </div>
      <div class="body-black__right"></div>
    </div>
</template>

<script>
import Header from './components/Header'
import Main from './components/Main'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header, Main, Footer
  },
  data: () => ({
    views: null
  }),
  methods: {
    finish(value){
        this.views = value;
    }
  },
  mounted() {
    this.finish();
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }

  @font-face {
    font-family: "Roboto";
    src: url('./assets/font/Roboto-Medium.ttf') format('truetype');
    font-weight: 500;
    font-style: normal;
}

@font-face {
    font-family: "Roboto";
    src: url('./assets/font/Roboto-Regular.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}

@font-face {
    font-family: "Roboto";
    src: url('./assets/font/Roboto-Bold.ttf') format('truetype');
    font-weight: bold;
    font-style: normal;
}

  input,
  select,
  button {
    outline: none;
    font-family: "Roboto";
  }

  p,
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    margin: 0;
    font-family: "Roboto";
  }

  button {
    padding: 0;
  }

  div,
  span {
    font-family: "Roboto";
  }

  html, 
  body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    background-color: black;
  }

  .body-black__left {
    position: absolute;
    z-index: 3;
    width: 50%;
    height: 100%;
    background-color: black;
  }

  .body-black__right {
    position: absolute;
    z-index: 3;
    width: 50%;
    height: 100%;
    background-color: black;
  }

  .body-container {
    position: relative;
    height: 100%;
    width: 100%;
    overflow: hidden;
  }

  .body-img {
    position: absolute;
    background-image: url(./assets/image/app-bg.jpg);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-position: center;
    height: 100%;
    width: 100%;
    min-width: 414px;
    margin: 0 auto;
    left: 0;
    right: 0;
    z-index: 2;


    @media (max-width: 414px) {
      min-width: 414px;
    }

    @media (max-width: 320px) {
      min-width: 320px;
    }
  }

  #app {
    display: inline-block;
    overflow-x: hidden;
    position: absolute;
    margin: 0 auto;
    left: 0;
    right: 0;
    width: 100%;
    height: 100%;
    min-width: 320px;
    max-width: 414px;
    z-index: 4;

    &::-webkit-scrollbar {
      width: 0px;
    }
  }

  #app::before {
    content: " ";
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(149.04deg, rgba(238, 69, 64, 0.198) 4.79%, rgba(130, 19, 52, 0.42) 28.17%, rgba(45, 19, 44, 0.456) 56.93%, rgba(0, 2, 43, 0.372) 91.24%);
    z-index: 1;
  }
</style>
