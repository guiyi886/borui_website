<template>
  <div class="overlay">
    <div class="overlay-content">
      <div class="slogan sofiaBold">
        <div class="slogan-title">湛江市博瑞机械设备有限公司</div>
        <div class="slogan-subtitle">Provide The Best Products</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup name="">
</script>

<style lang="less" scoped>
.overlay {
  position: absolute;
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-align: center;
  align-items: center;
  -ms-flex-pack: center;
  justify-content: center;
  text-align: center;
  cursor: default;

  //background: rgba(51,112,255,.2);
  .slogan {
    font-size: 78px;
    line-height: 88px;
    color: rgba(255, 255, 255, 0.87);
    margin-bottom: 488px; //调高度
    letter-spacing: 8px;
    font-weight: 648;

    .slogan-subtitle {
      letter-spacing: 16px;
      text-indent: 16px;
      font-size: 28px;
      line-height: 88px;
      opacity: .8;
      margin-top: 14px;
      position: relative;
    }
  }
}

.slogan .slogan-subtitle:after,
.slogan .slogan-subtitle:before {
  content: "";
  display: block;
  width: 74px;
  height: 2px;
  position: absolute;
  top: calc(50% - 1px);
  background-image: linear-gradient(270deg, hsla(0, 0%, 100%, 0), #fff 47%, hsla(0, 0%, 100%, 0));

}

.slogan .slogan-subtitle:before {
  left: -50px;
}

.slogan .slogan-subtitle:after {
  right: -50px;
}
</style>
