<template>
  <div class="w-full h-full flex flex-col items-center justify-center gap-10">
    <p class="text-white text-left">
      QR Code Result : <a :href="result" target="_blank">{{ result }}</a>
    </p>

    <div class="w-1/2 h-1/2 rounded-lg overflow-hidden">
      <qrcode-stream @detect="onDetect" :track="drawoutline"></qrcode-stream>
    </div>
  </div>
</template>

<script>
import { QrcodeStream } from "vue-qrcode-reader";
export default {
  components: {
    QrcodeStream,
  },

  data() {
    return {
      paused: false,
      result: "",
    };
  },

  methods: {
    
    async onDetect(detectedCodes) {
      console.log(detectedCodes);
      this.result = detectedCodes[0].rawValue;
      this.paused = true;
      setTimeout(() => {
        this.paused = false;
      }, 300);
    },

    drawoutline(detectedCodes, ctx) {

      for (const detectedCode of detectedCodes) {
        const [firstPoint, ...otherPoints] = detectedCode.cornerPoints

        ctx.strokeStyle = 'blue'

        ctx.beginPath()
        ctx.moveTo(firstPoint.x, firstPoint.y)
        for (const { x, y } of otherPoints) {
          ctx.lineTo(x, y)
        }
        ctx.lineTo(firstPoint.x, firstPoint.y)
        ctx.closePath()
        ctx.stroke()
      }

    },
  },
};
</script>
