<template>
  <section>
    <article class="about-introduce-container">
      <div class="block-container name" :class="{'hide-overfloww': showName }">
        <div :class="{'block-reveal top name' : showBlock}"></div>
        <div :class="{'block-reveal bottom name' : showBlock}"></div>
        <h2
          class="about-introduce-name"
          :class="{ 'hidden': !showName }">Takeshi Oide</h2>
        <p
          class="about-introduce-role"
          :class="{ 'hidden': !showName }">Front-end Creative Developer</p>
      </div>
      <div class="block-container en" :class="{'hide-overfloww': showText }">
        <div :class="{'block-reveal top' : showName}"></div>
        <div :class="{'block-reveal bottom' : showName}"></div>
      <p class="about-introduce en" :class="{ 'hidden': !showText }">
        Hi there. I am Takeshi from Japan. Just call me Tak. <br>
        Currently, I am in Vancouver as a freelancer.
        I am good at creating unique designs, understanding business goals,
        developing rich user experiences, and coding with JavaScript.
        I am always looking for something interesting and beautiful.</p>
      </div>
      <div class="block-container" :class="{'hide-overfloww': showText }">
        <div :class="{'block-reveal top' : showName}"></div>
        <div :class="{'block-reveal bottom' : showName}"></div>
        <p class="about-introduce jp" :class="{ 'hidden': !showText }">
          こんにちは。Takと呼ばれています。<br>
          カナダでWebデザインとデベロップメントをするフリーランス活動をしています。
          ビジネスの信念に寄り添い、ゴールを常に意識したデザインと、JavaScriptで創るクリエイティブでリッチなユーザー体験が強みです。
          ウェブだけではなく、面白いこと美しいことをいつも探しています。
        </p>
      </div>
    </article>
      <div class="video-container">
        <transition name="fade-in" appear>
          <video autoplay loop>
            <source src="../../assets/img/assets/portfolio_2.mp4" type="video/mp4">
          </video>
        </transition>
      </div>
  </section>
</template>

<script>
import video from '../../assets/img/assets/portfolio_2.mp4';

export default {
  data() {
    return {
      showBlock: false,
      showName: false,
      showText: false,
    };
  },
  methods: {
    triggerCollage() {
      this.showBlock = true;
      setTimeout(() => {
        this.showName = true;
      }, 500);
      setTimeout(() => {
        this.showText = true;
      }, 1000);
    },
  },
  mounted() {
    setTimeout(() => {
      this.triggerCollage();
    }, 500);
  },
  beforeRouteEnter(to, from, next) {
    Promise.all[video].then(() => next());
  },
};
</script>

<style scoped lang="scss">
  .hidden {
    opacity: 0;
  }
  .hide-overfloww {
    overflow: hidden;
  }
  /* ====  animation =====*/
  .block-container {
    position: relative;
  }
  .block-reveal {
    position: absolute;
    right: 0;
    width: 100%;
    height: 50%;
    background: $text;
    &.top {
      top: 0;
      transform: translateX(-100%);
    }
    &.bottom {
      top: 50%;
      transform: translateX(100%);
    }
  }
  .block-reveal {
    &.name {
      &.top {
        animation: block-reveal-top forwards ;
        animation-duration: 1s;
      }
      &.bottom {
        animation: block-reveal-bottom forwards;
        animation-duration: 1s;
      }
    }
    &.top {
      animation: block-reveal-top forwards ;
      animation-duration: 1s;
    }
    &.bottom {
      animation: block-reveal-bottom forwards;
      animation-duration: 1s;
    }
  }
  @keyframes block-reveal-top {
    from {
      transform: translateX(-100%);
    }
    50% {
      transform: translateX(0);
    }
    to {
      transform: translateX(100%);
    }
  }
  @keyframes block-reveal-bottom {
    from {
      transform: translateX(100%);
    }
    50% {
      transform: translateX(0);
    }
    to {
      transform: translateX(-100%);
    }
  }
  @keyframes block-reveal-right {
    from {
      left: 100%;
    }
    50% {
      left: 0;
    }
    to {
      left: -100%;
    }
  }
  /* ====  regular styling =====*/
  .block-container {
    &.name {
      margin-bottom: 110px;
    }
    &.en {
      margin-bottom: 30px;
    }
  }
  .about-introduce-container {
    width: 480px;
    margin-left: 13%;
    margin-top: 20%;
    @media screen and (max-width: 1500px) {
      margin-left: 10%;
    }
  }
  .about-introduce-name {
    font-weight: 800;
    font-size: 3rem;
    margin-bottom: 10px;
    margin-top: 0;
  }
  .about-introduce-role {
    font-weight: 400;
    font-style: italic;
    font-size: 1.2rem;
    margin-top: 0;
    margin-bottom: 0;
  }
  .about-introduce {
    margin: 0;
    &.en {
      background: rgba(255,255,255, 0.7);
    }
  }

  .video-container {
    position: absolute;
    top: 90px;
    right: 0;
    width: 65%;
    height: 700px;
    z-index: -10;
    video {
      width: 100%;
    }
  }

</style>
