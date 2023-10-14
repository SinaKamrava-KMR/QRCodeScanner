<script>
import QRCodeScanner from "./components/QRCodeScanner.vue";
export default {
  name: "app",
  components: {
    qrcodescanner: QRCodeScanner,
  },
};
</script>

<template>
<main class="bg-slate-800 flex h-screen w-screen justify-center items-center">

  <qrcodescanner />
</main>
</template>
