<template>
  <button class="comp-item pulsating-button button" :style="buttonRoundStyle">
    <div class="btn-txt">
      <slot></slot>
    </div>
    <div class="box-shadow" :style="buttonRoundStyle"></div>
  </button>
</template>
<script lang="ts" setup>
import { defineProps, ref } from 'vue'

interface Props {
  isRound?: Boolean
  size?: number
}

const props = defineProps<Props>()
const {
  isRound,
  size
} = props

// 设置圆形样式
const buttonRoundStyle = ref(isRound && {
    width: size + 'px',
    height: size + 'px',
    borderRadius:'50%'
  })

</script>

<style lang="scss" scoped>
.comp-item {
  position: relative;
  margin: 20px;
}

.button {
  position: relative;
  padding: 10px 14px;
  color: #ffffff;
  font-size: 14px;
  border-width: 0;
  border-radius: 10px;
  outline: none;
  cursor: pointer;
  background: rgba(59, 130, 246);
}

.box-shadow {
  width: 100%;
  height: 100%;
  position: absolute;
  animation: pulse 1.5s infinite;
  border: 0px solid rgb(123, 167, 237);
  background: rgba(59, 130, 246, 1);
  z-index: -1;
  border-radius: 10px;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

@keyframes pulse {
  0% {
    border-width: 0px;
    opacity: 1;
  }

  50% {
    border-width: 8px;
    opacity: 0.89;
  }

  100% {
    border-width: 0px;
    opacity: 1;
  }
}
</style>