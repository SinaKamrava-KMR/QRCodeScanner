<template>
  <div class="w-1/2 h-1/2 rounded-lg overflow-hidden">
    <qrcode-stream></qrcode-stream>
  </div>
</template>

<script>
import { QrcodeStream } from "vue-qrcode-reader";
export default {
  components: {
    QrcodeStream,
  },
};
</script>
