<template>
  <figure id="videoContainer" data-fullscreen="false">
		<video id="video" controls preload="metadata" poster="img/poster.jpg">
			<source src="http://techslides.com/demos/sample-videos/small.mp4" type=video/mp4>
		</video>
	</figure>
</template>

<script>
export default {
    methods: {
    a(){
  	// Obtain handles to main elements
   	var video = document.getElementById('video');
   	var videoControls = document.getElementById('video-controls');

   	// Hide the default controls
   	video.controls = false;

   	// Display the user defined video controls
   	videoControls.style.display = 'block';

   	// Obtain handles to buttons and other elements
   	var playpause = document.getElementById('playpause');
   	var mute = document.getElementById('mute');
   	var progress = document.getElementById('progress');
    // Add events for all buttons
    playpause.addEventListener('click', function(e) {
      if (video.paused || video.ended) video.play();
      else video.pause();
    });

    if(Hls.isSupported()) {
    var video = document.getElementById('video');
    var hls = new Hls();
    hls.loadSource('https://d3ag4xv79rahjs.cloudfront.net/659e5758-1faa-4252-bf75-ea4e72cd085d/hls/609245154a621683bbbabd8b_Ott_Hls_Ts_Avc_Aac_9x16_720x1280p_30Hz_6.5Mbps_qvbr.m3u8');
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED,function() {
      video.play();
    });
    // The Media API has no 'stop()' function, so pause the video and reset its time and the progress bar
    // stop.addEventListener('click', function(e) {
    // 	video.pause();
    // 	video.currentTime = 0;
    // 	progress.value = 0;
    // });
    mute.addEventListener('click', function(e) {
      video.muted = !video.muted;
    });
   	}
  }
    }
}
</script>

<style>

</style>
