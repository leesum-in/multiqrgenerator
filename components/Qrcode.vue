<template>
  <div class="qr-container">
    <vue-qr logo-src="./heart.jpg" :logo-scale="1" :text="text" :size="100" :margin="0" :dot-scale="1" :correct-level="3"/>
    <div v-if="param" class="qr-name">
      <span v-for="p in params" :key="p">
        {{ p }}
      </span>
    </div>
  </div>
</template>

<script>

    export default {
        name: "Qrcode",
        props: {
            url: {
                type: String,
                default: 'https://sumin-bohee.wemarry.in/with/'
            },
            param: {
                type: String,
                default: null
            }
        },
        data() {
            return {
                qr: null
            }
        },
        computed: {
            params() {
                return this.param.split('');
            },
            text() {
                return encodeURI(this.url + this.param);
            }
        }
    }
</script>

<style>
  .qr-container {
    padding: 10px;
    margin: 0;
    border: 1px dotted #aaa;
    float: left;
  }

  .qr-name {
    font-size: 15px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>
