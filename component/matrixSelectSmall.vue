<script setup lang="ts">
import { defineProps, onMounted, ref, watch, defineEmits } from 'vue';

const emits = defineEmits();

const props = defineProps({
  name: {
    type: String,
    default: "select header"
  },
  modelValue: {
    type: Object,
    default: () => ({})
  }
});
const selected = ref('');
let selecting = ref(false);

function onClickAway(event: MouseEvent) {
  if (selecting.value) {
    console.log(selecting.value + " " + props.modelValue.name);
    selecting.value = false;
    console.log(selecting.value + " " + props.modelValue.name);
  }
}

onMounted(() => {
  watch(() => props.modelValue, (newVal) => {
    for (const [key, value] of Object.entries(newVal)) {
      if (value) {
        selected.value = key;
      }
    }
  }, { immediate: true });
});

function selectItem(itemName: string) {
  selecting.value = false;
  props.modelValue[selected.value] = false;
  selected.value = itemName;
  props.modelValue[itemName] = true;
  emits('update:modelValue', props.modelValue);
}
</script>

<template>
  <div class="select" v-click-away="onClickAway" @click="selecting = !selecting">
    <span class="select__header">
      {{ props.name }}
    </span>
    <div class="select__selected">
      <span class="select__title">{{ selected }}</span>
      <div class="select__dropdown__arrow" :class="selecting?'active':''">
        >
      </div>
    </div>
    <div class="select__dropdown" :class="selecting?'active':''">
      <div class="select__dropdown__item" v-for="(value, name) in props.modelValue" :class="value?'selected':''"
           @click.stop="selectItem(name)">
        {{ name }}
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.select {
  position: relative;
  display: flex;
  flex-direction: column;
  font-family: Roboto, sans-serif;
  &__header {
    color: #6F6F6F;
    text-align: center;
    margin-bottom: 5px;
    font-size: 12px;
  }

  &__selected {
    border: 1px solid #6f6f6f;
    display: inline-flex;
    justify-content: center;
    padding: 7px 18px;
    border-radius: 20px;
    cursor: pointer;
    user-select: none;
    font-size: 19px;
    span {

    }
  }

  &__dropdown {
    display: none;
    position: absolute;
    width: 110%;
    height: 180px;
    overflow-y: scroll;
    top: 55px;
    z-index: 90;
    background: white;
    &.active {
      display: block;
    }

    &__item {
      padding: 10px;
      border: 1px solid lightgray;
      border-radius: 20px;
      text-align: center;
      margin-bottom: 10px;
      background: white;
      cursor: pointer;
      &.selected {
        background: #1AA217;
        color: white;
      }
    }
  }

  &__dropdown__arrow {
    margin: 0 0 0 20px;
    transform: rotate(-90deg);
    transition: 0.3s;

    &.active {
      transform: rotate(90deg);
    }
  }

}
</style>
