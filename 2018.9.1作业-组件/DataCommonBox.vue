<template>
    <div>
      <often-played-game :credit_status="credit_status" :favorite_games="credit_detail_data.favorite_games"></often-played-game>
      <day-play-time :credit_status="credit_status" :day_play_time="credit_detail_data.day_play_time"></day-play-time>
      <month-play-time :credit_status="credit_status" :month_play_time="credit_detail_data.month_play_time"></month-play-time>
      <certify-status :credit_status="credit_status" @to-promote-creit="$emit('to-promote-creit',$event)"></certify-status>
      <punish-gameList :credit_status="credit_status"></punish-gameList>
    </div>
</template>

<script>
  import OftenPlayedGame from './OftenPlayedGame'
  import DayPlayTime from './DayPlayTime'
  import MonthPlayTime from './MonthPlayTime'
  import CertifyStatus from './CertifyStatus'
  import PunishGameList from './PunishGameList'
    export default {
        name: "dataCommonBox",
      props:["credit_status"],
      components:{
        'often-played-game':OftenPlayedGame,
        'day-play-time': DayPlayTime,
        'month-play-time':MonthPlayTime,
        'certify-status':CertifyStatus,
        'punish-gameList':PunishGameList
      },
      data(){
          return{
            credit_detail_data:{
              day_play_time: "",
              month_play_time: "",
              favorite_games: "",
            },
          }
      },
      mounted(){
          console.log(this.credit_status)
          //if(this.credit_status == 0){
            this.query_credit_detail();
          //}
      },
      methods:{
          query_credit_detail(){
            var url='/api/msdk/proxy/query_common_credit_detail';
            var params = this.paramChangeJson();
            this.$axios.get(url,{params:params})
              .then(response => {

              })
              .catch(error => {
                //todo
                var response = {
                  "err":0,
                  "data": {
                    "day_play_time": 4504.56,
                    "month_play_time": 30,
                    "favorite_games": [28,2577,5,28,2577,2577],
                  }
                };
                console.log(response);
                console.log(11111111111)
                if(response.err == 0){
                  this.credit_detail_data = response.data;
                }

              })
          }
      },
    }
</script>

<style scoped>

</style>
