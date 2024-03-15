<template>
  <div class="legend">
    <div class="legend__header" @click="toggleOpen">
      <div v-if="available" class="legend-available legend-arrow">
        <svg height="100%" :class="{ 'up': open }" viewBox="0 0 192 512" xmlns="http://www.w3.org/2000/svg">
          <path d="M0 384.662V127.338c0-17.818 21.543-26.741 34.142-14.142l128.662 128.662c7.81 7.81 7.81 20.474 0 28.284L34.142 398.804C21.543 411.404 0 402.48 0 384.662z"></path>
        </svg>
      </div>
      <div v-else class="legend-unavailable legend-arrow">
        <svg height="100%" :class="{ 'up': open }" viewBox="0 0 320 512" xmlns="http://www.w3.org/2000/svg">
          <path d="M143 256.3L7 120.3c-9.4-9.4-9.4-24.6 0-33.9l22.6-22.6c9.4-9.4 24.6-9.4 33.9 0l96.4 96.4 96.4-96.4c9.4-9.4 24.6-9.4 33.9 0L313 86.3c9.4 9.4 9.4 24.6 0 33.9l-136 136c-9.4 9.5-24.6 9.5-34 .1zm34 192l136-136c9.4-9.4 9.4-24.6 0-33.9l-22.6-22.6c-9.4-9.4-24.6-9.4-33.9 0L160 352.1l-96.4-96.4c-9.4-9.4-24.6-9.4-33.9 0L7 278.3c-9.4 9.4-9.4 24.6 0 33.9l136 136c9.4 9.5 24.6 9.5 34 .1z"></path>
        </svg>
      </div>
      <h4>{{ header }}</h4>
    </div>
    <transition name="slide">
      <div class="legend-text" :class="{ 'opened': open }" ref="textBlock" :style="{ maxHeight: open ? textHeight  : '0px'}">
        <span>{{ text }}</span>
      </div>
    </transition>
  </div>
</template>

<script setup lang="ts">
import { defineProps, ref, onMounted } from "vue";

const props = defineProps({
  header: {
    type: String,
    default: "select header"
  },
  text: {
    type: Object,
    default: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad, aliquam amet blanditiis deleniti dolores error expedita fuga fugiat fugit illo inventore natus nisi quae quaerat quasi quo soluta temporibus voluptatum?'
  },
  available: {
    type: Boolean,
    default: false
  }
});

let open = ref(true);
let textHeight = ref('0px');
let textBlock = ref();
function toggleOpen() {
  open.value = !open.value;
}

onMounted(() => {
  const computedStyle = window.getComputedStyle(textBlock.value);
  const lineHeight = parseInt(computedStyle.lineHeight);
  const paddingTop = parseInt(computedStyle.paddingTop);
  const paddingBottom = parseInt(computedStyle.paddingBottom);
  const textHeight1 = textBlock.value.scrollHeight - paddingTop - paddingBottom;
  // Подсчитываем высоту текста, вычитая верхний и нижний внутренний отступы
  const estimatedHeight = Math.ceil(textHeight1 / lineHeight) * lineHeight + paddingTop + paddingBottom;
  textHeight.value = estimatedHeight + 'px';
  open.value = false;
});
</script>

<style scoped lang="scss">
//.slide-enter-active, .slide-leave-active {
//  transition: height 0.3s ease, opacity 0.3s ease;
//}
//.slide-enter, .slide-leave-to {
//  height: 0;
//  opacity: 0;
//  overflow: hidden;
//}

.legend {
  padding: 15px;
  border: 2px solid #67768e;
  border-radius: 28px;
  margin-top: 30px;
  background: white;

  &-arrow {
    width: 18px;
    height: 18px;
    transition: transform 0.3s ease;
  }
  &-unavailable {
    fill: #e84609;
    transition: 0.2s linear;
    .up {
      transform: rotate(180deg);
    }
  }
  &-available {
    fill: #1DC808;
    transition: 0.2s linear;
    .up {
      transform: rotate(180deg);
    }
  }
  &-text {
    overflow: hidden;
    transition: 0.2s linear;
    max-height: 0;
    color: #1B8A26;
    margin-top: 0;
    &.opened {
      margin-top: 15px;
    }
  }

  &__header {
    display: flex;
    gap: 10px;
    cursor: pointer;
    color: #67768e;
    h4 {
      font-family: Roboto, sans-serif;
      font-size: 21px;
      font-weight: 600;
      text-decoration: underline;
    }
  }

  &-unavailable:hover {
    opacity: 0.8;
  }
}
</style>