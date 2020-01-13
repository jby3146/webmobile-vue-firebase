<template>
  <div id="homepage_slider" class="st_slider">
    <input
      v-for="item in slider"
      type="radio"
      class="cs_anchor radio"
      :key="item.key"
      :name="item.Slide"
      :id="item.id"
    />
    <input
      type="radio"
      class="cs_anchor radio"
      name="slider"
      id="play1"
      checked=""
    />
    <div class="images">
      <div class="images_inner">
        <div class="image_slide" v-for="about in aboutmes" :key="about.key">
          <v-layout id="about">
            <v-flex xs6 my-5 class="profile_hidden">
              <v-img :src="getImgUrl(about.imgadr)" aspect-ratio="1.5" />
            </v-flex>
            <v-flex my-5 xs12 class="about_me_left">
              <h2 my-5 class="headline mb-3 about-center">
                {{ about.Subtitle }}
              </h2>
              <p class="mr-4">
                {{ about.Subtitle }}<br />
                {{ about.contents }}
                <strong>{{ about.name }}</strong> 입니다.<br />
              </p>
            </v-flex>
          </v-layout>
        </div>
      </div>
    </div>
    <div class="labels">
      <div class="fake_radio">
        <label
          v-for="item in items"
          :key="item.SlideNumber"
          :for="item.SlideNumber"
          class="radio_btn"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      items: [
        { SlideNumber: "slide1" },
        { SlideNumber: "slide2" },
        { SlideNumber: "slide3" },
        { SlideNumber: "slide4" },
        { SlideNumber: "slide5" }
      ],
      slider: [
        { Slide: "slider", id: "slide1" },
        { Slide: "slider", id: "slide2" },
        { Slide: "slider", id: "slide3" },
        { Slide: "slider", id: "slide4" },
        { Slide: "slider", id: "slide5" }
      ],
      aboutmes: [
        {
          imgadr: "profile2.jpg",
          contents: "거인의 발이 되어 세상을 뛰어다니고 싶은",
          name: "JunSeok Wi",
          Subtitle: "Hello World"
        },
        {
          imgadr: "profile.jpg",
          contents: "거인의 어깨 위에서 개발을 하고 싶은",
          name: "TaeJune Joung",
          Subtitle: "안녕하세요"
        },
        {
          imgadr: "profile3.jpg",
          contents: "거인의 등이 되어 사람들을 엎고 다닐 수 있는",
          name: "ByeongYong Jo",
          Subtitle: "Well Come To"
        },
        {
          imgadr: "profile4.jpg",
          contents: "거인의 눈이 되어 세상을 한번에 알아보는",
          name: "JunYoung Kim",
          Subtitle: "Oh My Genius"
        },
        {
          imgadr: "profile5.jpg",
          contents: "거인의 손으로 세상을 주무르고 싶은",
          name: "DongSik Moon",
          Subtitle: "HA HA HA HA HA HA"
        }
      ]
    };
  },
  methods: {
    getImgUrl(img) {
      return require("../assets/" + img);
    }
  }
};
</script>

<style>
.about_me_left {
  padding-left: 50px;
  padding-top: 40px;
}
.cs_anchor {
  display: none;
}
.image {
  width: 100%;
  height: 200px;
}
.images {
  overflow: hidden;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
}
.images_inner {
  width: 500%;
  transition: all 800ms cubic-bezier(0.77, 0, 0.175, 1);
  transition-timing-function: cubic-bezier(0.77, 0, 0.175, 1);
}
.image_slide {
  width: 20%;
  float: left;
}
.image_slide,
.fake_radio,
.radio_btn {
  transition: all 0.1s ease-out;
}
.fake_radio {
  float: right;
}
#slide1:checked ~ .images .images_inner {
  margin-left: 0;
}

#slide2:checked ~ .images .images_inner {
  margin-left: -100%;
}
#slide3:checked ~ .images .images_inner {
  margin-left: -200%;
}
#slide4:checked ~ .images .images_inner {
  margin-left: -300%;
}
#slide5:checked ~ .images .images_inner {
  margin-left: -400%;
}
#slide1:checked~div .fake_radio .radio_btn:nth-child(1),
#slide2:checked~div .fake_radio .radio_btn:nth-child(2),
#slide3:checked~div .fake_radio .radio_btn:nth-child(3),
#slide4:checked~div .fake_radio .radio_btn:nth-child(4),
#slide5:checked~div .fake_radio .radio_btn:nth-child(5) {
  background: red;
}
.radio_btn {
  width: 9px;
  height: 9px;
  border-radius: 5px;
  background: gray;
  display: inline-block !important;
  margin: 0 1px;
  cursor: pointer;
}
@keyframes slide {
  0%,
  19.999999999999999% {
    margin-left: 0;
  }
  20%,
  39.999999999999999% {
    margin-left: -100%;
  }
  40%,
  59.999999999999999% {
    margin-left: -200%;
  }
  60%,
  79.999999999999999% {
    margin-left: -300%;
  }
  80%,
  99.999999999999999% {
    margin-left: -400%;
  }
}
.st_slider > #play1:checked ~ .images .images_inner {
  animation: slide 12300ms infinite;
}
@keyframes caption {
  0%,
  33.32333333333334% {
    opacity: 1;
  }
  33.333333333333336%,
  100% {
    opacity: 0;
  }
}
#play1:checked~.labels .label:nth-child(1) {
  animation: caption 12300ms infinite -1000ms;
}
#play1:checked~.labels .label:nth-child(2) {
  animation: caption 12300ms infinite 3100ms;
}
#play1:checked~.labels .label:nth-child(3) {
  animation: caption 12300ms infinite 7200ms;
}
.text_shadow {
  text-shadow: 0 0 15px rgb(255, 255, 255);
}
*[data-animation="ripple"] {
  height: 100%;
  width: 200px;
  display: block;
  outline: none;
  padding: 20px;
  color: #fff;
  text-transform: uppercase;
  background: linear-gradient(135deg, #e570e7 0%, #79f1fc 100%);
  box-sizing: border-box;
  text-align: center;
  line-height: 14px;
  font-family: roboto, helvetica;
  font-weight: 200;
  letter-spacing: 1px;
  text-decoration: none;
  box-shadow: 0 5px 3px rgba(0, 0, 0, 0.3);
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
  border-radius: 5px;
}
*[data-animation="ripple"]:focus {
  outline: none;
}
*[data-animation="ripple"]::selection {
  background: transparent;
  pointer-events: none;
}
</style>
