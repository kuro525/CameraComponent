<template>
  <video ref="video" id="video" width="400" height="400" playsinline muted autoplay></video>
</template>

<script>
export default {
  name: 'Camera',
  data() {
    return {
      video: {}
    };
  },
  mounted() {
    this.video = this.$refs.video;
    navigator.mediaDevices
      .getUserMedia({ video: true, audio: false })
      .then(stream => {
        this.video.srcObject = stream;
        this.video.play();
      })
      .catch(err => {
        console.log('エラー! ' + err);
      });
    console.log(this.$refs.video);
  }
};
</script>
