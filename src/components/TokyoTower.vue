<template>
    <div class="container">
        <h1>TokyoTowerNFT</h1>
        <img class="question" src="../assets/question.jpeg" width="200" height="200" alt="">
        <p>MINT済み：{{ count_minted }} / 100</p>
        <p>{{Mintable ? 'MINT可能です' : 'もっと東京タワーに近づいてください'}}</p>
        <p>東京タワーまであと {{ distance }}km</p>
        <input type="button" value="MINT" class="mint_button" @click="mint" :disabled="!Mintable">
    </div>
</template>
<script language="javascript" type="text/javascript" src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>
<script>
export default {
  name: 'TokyoTower',
  data () {
    return {
        count_minted: 0,
        distance: 1000,
        isMintable: false,
        web3: null,
        nftContract: null,
        endpoint: "https://ropsten.infura.io/v3/2e78310c36c64ae6929c92662c4f9cff",
        contractAddress: "0x13D7964fEd6c8A92097E5f0659FD53D1E54505af"
    }
  },
  methods: {
    changeDistance(pos) {
      var tt_lat = 35.658584;
      var tt_lng = 139.7454316;
      var curloc_lat = pos.coords.latitude;
      var curloc_lng = pos.coords.longitude;
      var current_distance = this.calculateDistance(tt_lat,tt_lng,curloc_lat,curloc_lng).toFixed(3);
      this.distance = current_distance;
    },
    calculateDistance(lat1, lng1, lat2, lng2) {
      lat1 *= Math.PI / 180;
      lng1 *= Math.PI / 180;
      lat2 *= Math.PI / 180;
      lng2 *= Math.PI / 180;
      return 6371 * Math.acos(Math.cos(lat1) * Math.cos(lat2) * Math.cos(lng2 - lng1) + Math.sin(lat1) * Math.sin(lat2));
    },
    startWatchingPosition() {
      try {
        navigator.geolocation.watchPosition(this.changeDistance, function(e) { alert(e.message); }, {"enableHighAccuracy": true, "timeout": 20000, "maximumAge": 2000});
        console.log("method ends.");
      } catch(e) {
        console.log(e);
      }
    }
  },
  async created() {
    //位置情報のモニタリングを開始
    this.startWatchingPosition();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mint_button {
  border: none;
  align-items: center;
  margin: 0 auto;
  padding: 1em 2em;
  width: 50%;
  font-size: 18px;
  font-weight: 700;
  background-color: #4676d7;
  border-radius: 50vh;
  color: white;
}

.mint_button:disabled {
  border: none;
  align-items: center;
  margin: 0 auto;
  padding: 1em 2em;
  width: 50%;
  font-size: 18px;
  font-weight: 700;
  background-color: #aaaeb4;
  border-radius: 50vh;
  color: white;
}

.mint_button:hover {
  background-color: #2d64d1;
}

</style>