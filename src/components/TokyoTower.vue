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