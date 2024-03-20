<script>
export default {
  name: 'App',
  methods: {
    injectRuffle() {
      // create script element
      const ruffleScript = document.createElement('script');
      ruffleScript.src = 'https://unpkg.com/@ruffle-rs/ruffle';
      ruffleScript.onload = () => {
        console.log('Ruffle has been injected and loaded');
      };

      // inject script to iframe
      this.$refs.iframe.contentWindow.document.body.appendChild(ruffleScript);
    }
  }
}
</script>

<template>
  <div>
    <iframe ref="iframe" src="http://localhost:5173/flash-page.html" width="800" height="600" @load="injectRuffle">
    </iframe>
  </div>
</template>
