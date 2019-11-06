<template>
  <div class="container">
    <div class="menu hidden-print">
      <div class="form-control">
        <label for="input-url">URL</label>
        <input id="input-url" type="text" v-model="url" />
      </div>
      <div class="form-control">
        <label for="input-names">초대</label>
        <textarea id="input-names" v-model="names" placeholder="엔터로 이름 구분" rows="50" cols="35"></textarea>
      </div>
      <button @click="print" v-if="names">인쇄</button>
    </div>
    <div class="render-area">
      <qrcode v-for="name in params" v-if="name" :key="name" :param="name" />
    </div>

  </div>
</template>

<script>
    import Qrcode from "../components/Qrcode";

    export default {
        components: {
            Qrcode
        },
        data() {
            return {
                url: 'https://sumin-bohee.wemarry.in/with/',
                names: '이수민\n이보희'
            }
        },
        computed: {
            params() {
                if(this.names) {
                    return this.names.split('\n');
                }
            }
        },
        methods: {
            print() {
                window.print();
            }
        }
    }
</script>

<style>
  .container {
    margin: 0;
    min-height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
  }
  .menu {
    max-width: 300px;
    flex: 1;
    padding: 10px;
    border-right: 1px solid #3b8070;
  }

  .render-area {
    flex: 1;
  }

  .form-control {
    margin-bottom: 10px;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
  }
</style>
