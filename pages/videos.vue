<template>
    <div id="videoContainer" data-fullscreen="false" >
		<video id="video" preload="metadata" @click="mute">
		</video>
    <button @click="pause">pause</button>
	</div>
    
</template>

<script>
export default {
    data(){
        return{
            paused: false,
        }
    },
    methods:{
        pause(){
          var video = document.getElementById("video")
            if(this.paused){
                video.play();
                this.paused = !this.paused;
            } else {
                video.pause();
                this.paused = !this.paused;
            }
        },
        mute(){
            var video=document.getElementById("video")
            if(video.muted){
                video.muted = false;
            } else {
                video.muted = true;
            }
        }},
    mounted() {
   	var video = document.getElementById('video');
   	video.controls = false;
    if(Hls.isSupported()) {
    var video = document.getElementById('video');
    var hls = new Hls();
    hls.loadSource('https://d3ag4xv79rahjs.cloudfront.net/7d86d6f8-697e-48f1-ba53-d35cadf304c4/hls/60a4a09f54927853d7daf67d_Ott_Hls_Ts_Avc_Aac_16x9_1920x1080p_30Hz_8.5Mbps_qvbr.m3u8');
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED,function() {
      video.muted = true;
      video.loop = true;
      video.play();
    });
   	}
  }
}

</script>

<style>

</style>
