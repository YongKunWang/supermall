<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="slot-icon"></slot></div>
    <div v-else><slot name="slot-icon-activate"></slot></div>
    <div :style="activateStyle"><slot name="slot-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path: String,
    activateColor: {
      type: String,
      default: 'red'
    }
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path)
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activateStyle() {
      return this.isActive ? { color: this.activateColor } : {}
    }
  }
}
</script>

<style>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}
</style>
