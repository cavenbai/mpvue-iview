<script lang="ts">
  import { Vue, Component } from 'vue-property-decorator'
  const debug = require('debug')('log:App')

  declare module "vue/types/vue" {
    interface Vue {
      $mp: any;
    }
  }

  // 必须使用装饰器的方式来指定components
  @Component({mpType: 'app'}as any)
  export default class App extends Vue {
    // app hook
    onLaunch() {
      let opt = this.$root.$mp.appOptions
      debug('onLaunch', opt)
    }

    onShow() {
      debug('onShow')
    }

    onHide() {
      debug('onHide')
    }

    mounted() { // vue hook
      debug('mounted')
    }
  }
</script>

<style>
  .container {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    padding: 200px 0;
    box-sizing: border-box;
  }

  /* this rule will be remove */
  * {
    transition: width 2s;
    -moz-transition: width 2s;
    -webkit-transition: width 2s;
    -o-transition: width 2s;
  }
</style>
