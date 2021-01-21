<template>
  <v-container class="justify-center align-center mt-0 pt-0 fluid">
    <v-row align="start" align-content="start" justify="center">
      <v-container class="ma-0 pa-0  elevation-12" style=" max-width:761px" fluid align="center" justify="center">
        <v-row class="ma-0 pa-0" align="start" align-content="start" justify="center">
          <v-col class="ma-0 pa-0">
            <v-img src="static/img/bg1.jpg" contain position="center top">
              <snow style="position:absolute !important"></snow>
              <v-container fill-height class="justify-center align-end mt-0 pt-0 fluid text-center">
                <v-row align="end" align-content="end">
                  <v-col>
                    <span class="dday" id="kscfont">
                      {{getDayGapText}}
                    </span>
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
          </v-col>
        </v-row>
        <v-spacer></v-spacer>
        <v-row class="ma-0 pa-0" align="center" align-content="center" justify="center">
          <v-col class="ma-0 pa-0">
            <v-img src="static/img/bg2.jpg" contain position="center top">
              <snow style="position:absolute !important"></snow>
              <v-container fill-height class="justify-center align-center ma-0 pa-0 fluid text-center">
                <v-row align="center" align-content="center" class="ma-0 pa-0">
                  <v-col class="ma-0 pa-0">
                    <v-carousel v-model="photopage" hide-delimiter-background>
                      <v-carousel-item @click="openOverlay(img)" v-for="(img,index) in imgList" :key="'card-'+index"
                        delimiter-icon="mdi-minus">
                        <v-container fill-height class="justify-center align-center ma-0 pa-0 fluid text-center">
                          <v-row align="center" align-content="center" class="ma-0 pa-0">
                            <v-col class="ma-0 pa-0">
                              <v-img :src="getImgUrl(img.src)" aspect-ratio="1.7778" position="center bottom" contain>
                              </v-img>
                            </v-col>
                          </v-row>
                        </v-container>
                      </v-carousel-item>
                    </v-carousel>
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
          </v-col>
        </v-row>
        <v-dialog v-model="overlay" overlay-opacity="1" scrollable transition="fade">
          <v-img v-if="overlay" :src="getImgUrl(overlayImg.src)" :width="width" contain></v-img>
        </v-dialog>
      </v-container>
    </v-row>
  </v-container>
</template>

<script>
import Snow from './snow'
  export default {
    name: 'Announcement',
    components:{
      Snow
    },
    props:[
      'dday',
      'rawD'
    ],
    data: () => ({
      photopage: 0,
      width: window.innerWidth,
      height: window.innerHeight,
      imgList:[
        {src:"DSC03976.jpg"},
        {src:"DSC04195.jpg"},
        {src:"DSC04231.jpg"},
        {src:"DSC04378.jpg"},
        {src:"DSC04059.jpg"},
        {src:"DSC04656.jpg"},
      ],
      overlay:false,
      overlayImg: null,
    }),
    created:function(){
      window.addEventListener('resize', () =>{
            this.height = window.innerHeight
            this.width = window.innerWidth
        })
    },
    computed:{
      getDayGapText(){
        const dday = this.rawD
        if(dday<1) return dday == 0?"오늘은 우리 결혼하는 날!":"우리 결혼한지 벌써 "+(-1*dday) +"일째!"
        return "결혼식날 까지 앞으로 "+dday+"일!";
      }
    },
    methods:{
      getThomUrl(src){
        return 'static/img/thom/'+src
      },
      getImgUrl(src){
        return 'static/img/'+src
      },
      openOverlay(img){
        this.overlay =true
        this.overlayImg = img
      },
      hideOverlay(){
        this.overlay = false
        this.overlayImg = null
      },
    }
  }
</script>
<style scoped>
@font-face {
  font-family: 'haeun';
  src: url('../assets/nanum.ttf');
}
.dday {
  font-family: haeun;
     font-size: 2em;
}
#footer{
  font-family: haeun !important;
  background-color:rgb(165, 120, 64);
  color:rgba(255, 255, 255,0.6);
    font-size: 20px;
}
.target_date{
  color:rgb(170, 170, 170);
  font-size: 36px;
}
.announce{
  color:rgb(170, 170, 170);
  font-size: 36px;
}
.and{
  margin-top:20px;
  margin-bottom:25px;
}
.name{
  font-size: 20px;
  padding-top:15px;
  padding-bottom:15px;
}
.gallery_title{
    font-family: "Noto Sans KR", sans-serif;
    font-weight: 400;
    height: 60px;
    font-size:16px;
    padding-top:20px;
    padding-bottom:20px;

}
</style>