<!-- CopyRight (C) 2017-2022 Alibaba Group Holding Limited. -->
<template>
  <div class="wxc-demo">
    <scroller class="scroller">
      <title title="wxc-countdown"></title>
      <category title="基础使用"></category>
      <text class="demo-desc">默认样式，时间戳传5秒后，倒计时完传回调</text>
      <div class="demo-3">
        <text class="cb-text">{{demoText}}:</text>
        <wxc-countdown
          :time="demoTime"
          @wxcOnComplete="onCompletedTwo">
        </wxc-countdown>
      </div>

      <category title="自定义配置"></category>
      <text class="demo-desc">配置样式，设置倒计时频率</text>
      <wxc-countdown
        :interval="2000"
        tpl="{h}时{m}分{s}秒"
        :timeBoxStyle="{backgroundColor: '#C3413D', height: '50px', width: '50px'}"
        :timeTextStyle="{fontSize: '24px', color: '#FFB706'}"
        :dotTextStyle="{color: '#C3413D', fontSize: '26px'}"
        :dotBoxStyle="{width: '30px'}"
        :style="{marginTop: '10px', justifyContent: 'center'}"
        :time="TIME">
      </wxc-countdown>

    </scroller>
  </div>
</template>

<style scoped>
  .wxc-demo {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: #fff;
  }

  .demo-desc {
    font-size: 32px;
    margin-top: 20px;
    margin-bottom: 10px;
    margin-left: 30px;
    margin-right: 30px;
    color: rgb(102, 102, 102);
    text-align: center;
  }

  .demo-3 {
    margin-top: 30px;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .scroller {
    flex: 1;
  }
</style>

<script>
  const modal = weex.requireModule('modal');
  import { setTitle } from '../_mods/set-nav';

  import Title from '../_mods/title.vue';
  import Category from '../_mods/category.vue';

  import { WxcCountdown } from 'Eros/weex-ui'

  export default {
    components: { Title, Category, WxcCountdown },
    data: () => ({
      // TIME: new Date().getTime() + 86400000 + ''
      TIME: new Date().getTime() + 10000,
      demoTime: new Date().getTime() + 5000,
      callbackText: '',
      demoText: '距离开始'
    }),
    created () {
      setTitle('Countdown');
    },
    methods: {
      onCompleted () {
        this.callbackText = '倒计时完成了';
        modal.toast({
          message: '倒计时完成了'
        })
      },
      onCompletedTwo () {
        this.demoTime = new Date().getTime() + 5000;
        this.demoText = this.demoText === '距离开始' ? '距离结束' : '距离开始';
        modal.toast({
          message: '倒计时完成了'
        })
      }
    }
  }
</script>
