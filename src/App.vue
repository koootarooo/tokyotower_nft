<template>
  <div id="app">
    <TokyoTower/>
    <dl>
      <dt>緯度</dt>
      <dd id="latitude">-</dd>

      <dt>経度</dt>
      <dd id="longitude">-</dd>

      <dt>緯度・経度の精度</dt>
      <dd id="accuracy">-</dd>

      <dt>GPS 高度</dt>
      <dd id="altitude">-</dd>

      <dt>GPS 高度の精度</dt>
      <dd id="altitudeAccuracy">-</dd>

      <dt>移動方向</dt>
      <dd id="heading">-</dd>

      <dt>移動速度</dt>
      <dd id="speed">-</dd>

      <dt>タイムスタンプ</dt>
      <dd id="timestamp">-</dd>
    </dl>
  </div>
</template>

<script>
import TokyoTower  from './components/TokyoTower'

export default {
  name: 'App',
  components: {
    TokyoTower
  }
}
</script>

<script>
document.addEventListener("DOMContentLoaded", function() {
	// オプション・パラメータをセット
	var position_options = {
		// 高精度を要求する
		enableHighAccuracy: true,
		// 最大待ち時間（ミリ秒）
		timeout: 60000,
		// キャッシュ有効期間（ミリ秒）
		maximumAge: 0
	};
	// 現在位置情報を取得
	navigator.geolocation.watchPosition(monitor, null, position_options);
}, false);

// 位置情報取得完了時の処理
function monitor(event) {
	// 緯度
	var latitude = event.coords.latitude;
	document.querySelector('#latitude').textContent = latitude;
	// 経度
	var longitude = event.coords.longitude;
	document.querySelector('#longitude').textContent = longitude;
	// 緯度・経度の精度
	var accuracy = event.coords.accuracy;
	document.querySelector('#accuracy').textContent = accuracy;
	// GPS 高度
	var altitude = event.coords.altitude;
	document.querySelector('#altitude').textContent = altitude;
	// GPS 高度の精度
	var altitudeAccuracy = event.coords.altitudeAccuracy;
	document.querySelector('#altitudeAccuracy').textContent = altitudeAccuracy;
	// 移動方向
	var heading = event.coords.heading;
	document.querySelector('#heading').textContent = heading;
	// 移動速度
	var speed = event.coords.speed;
	document.querySelector('#speed').textContent = speed;
	// タイムスタンプ
	var date = event.timestamp;
	if( typeof(date) == "number" ) {
		date = new Date(date);
	}
	document.querySelector('#timestamp').textContent = date.toString();
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
