<script setup>
// eslint-disable-next-line no-unused-vars
const props = defineProps({
  names: {
    type: Array,
    required: true
  },
  selectedTab: {
    type: Object,
    required: false
  }
})

const emit = defineEmits(['changeTab'])

const clickOnTab = (tab) => {
  emit('changeTab', tab)
}
</script>

<template>
  <div class="tab-nav">
      <span
        v-for="tab in names"
        :key="tab.name"
        :class="['tab-nav__item', {'selected': tab.name === selectedTab.name}]"
        @click="clickOnTab(tab)"
      >
        {{ tab.label }}
      </span>
  </div>
</template>

<style lang="less" scoped>
.tab-nav {
  width: 100%;
  display: flex;
  justify-content: start;
  gap: 15px;
  border-radius: 10px;
}

.tab-nav__item {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding: 12px 20px;
  border-radius: 10px;
  outline: 1px solid black;
  outline-offset: -1px;
  transition: background-color 0.2s;
  color: black;
  font-size: @font-size-small;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  gap: 10px;
}

.tab-nav-fit-content {
  .tab-nav__item {
    width: fit-content;
  }
}

.small-tabs {
  gap: 10px;
  .tab-nav__item {
    height: 30px;
    padding: 15px;
  }
}

.tab-nav-centered {
  justify-content: center;
}
.tab-nav-wrap {
  flex-wrap: wrap;
}

.tab-nav__item.selected {
  background-color: @secondary-color;
  outline: none;
  color: white;
}
</style>
