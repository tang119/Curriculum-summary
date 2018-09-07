<template>
  <!--最近常玩的游戏 S-->
  <div class="data-item">
    <i class="ico ico-recent"></i>
    <div class="data-detail">
      <h3>最近常玩的<strong>游戏</strong></h3>
      <ul class="game-data game-list clearfix" v-if="credit_status === 0"><!--game-data 有数据-->
        <li v-if="Boolean(favorite_games)" v-for="favorite_game in favorite_games" :key="favorite_game">
          <img :src="require('../assets/images/games/gm_'+favorite_game+'.jpg')" alt="" />
          <p>{{favorite_game}}</p>
        </li>
        <!--<li>
          <img src="../assets/images/games/gm_2131.jpg" alt="" />
          <p>绝地求生全军出击</p>
        </li>
        <li>
          <img src="../assets/images/games/gm_23.jpg" alt="" />
          <p>英雄联盟</p>
        </li>-->

      </ul>
      <ul class="game-data game-list clearfix" v-if="credit_status === 0 && favorite_games.length === 0"><!-- 无数据 -->
        <li>无</li>
      </ul>
      <ul class="game-none" v-if="credit_status !== 0"><!--game-none 无数据 横线-->
        <li></li>
      </ul>
    </div>
  </div>
  <!--最近常玩的游戏 E-->
</template>

<script>
    export default {
        name: "oftenPlayedGame",
      props:["credit_status","favorite_games"],
      data(){
          return{
            //src:require("../assets/images/games/gm_2128.jpg")
          }
      },
      computed:{
        /*game_class(){
          if(this.credit_status != 0){
            return "game-none"
          }else{
            return "game-data game-list clearfix"
          }

        }*/
      },
      mounted(){
          console.log(this.favorite_games)
      }

    }
</script>

<style scoped>

</style>
