<template>
  <v-app>
    <v-app-bar
      app
      color="#FBFBFB"
      flat
      dense
      outline
      style="color:#a7ad98"
      align="cetner"
    >
    WEDDING ANNOUNCEMENT
    <v-spacer></v-spacer>
      <span class="dday">
            D{{dday}}
      </span>
    </v-app-bar>
    <v-main style="background-color:#F2F2F2" >
      <Announcement :dday="dday" :rawD="rawD"/>
    </v-main>
  </v-app>
</template>

<script>
import Announcement from './components/Announcement';

export default {
  name: 'App',

  components: {
    Announcement
  },

  data: () => ({
    dday:"",
    rawD:''
  }),
  created:function(){
    this.getDayGap()
  },
  methods:{
      getDayGap(){
        let dday = new Date("December 12, 2020 00:00:00").getTime();//디데이
        let nowday = new Date();//현재
        nowday = nowday.getTime();//밀리세컨드 단위변환
        let distance = dday - nowday;//디데이에서 현재까지 뺀다.
        let d = Math.floor(distance / (1000 * 60 * 60 * 24));//일
        this.rawD = d
        this.dday = this.dDayTypeHandler(d)
      },
      dDayTypeHandler(d){
        if(d<1) return d == 0?"-day":"+"+(d*-1)
        return "-"+d+"";
      }
  }
};
</script>
<style>
@font-face { font-family: 'Heebo';
src: url('/assets/DXKPMB-KSCpc-EUC-H.eot');
src: url('/assets/DXKPMB-KSCpc-EUC-H.eot') format('embedded-opentype'),
url('/assets/DXKPMB-KSCpc-EUC-H.woff') format('ttf');}

* {

  font-family: "Heebo", "Noto Sans KR", sans-serif
}
</style>
