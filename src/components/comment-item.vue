<template>
  <box :url="detail.user.avatar">
    <div slot="header-left" style="padding: 10px 0">
      <a href="https://github.com/jmingzi" target="_blank">{{ detail.user.name }}</a>
      <span class="vue-comment__time">commented on {{ detail.createdTimeStamp }}</span>
    </div>
    <div slot="header-right" class="vue-comment__opt" style="padding: 10px 0">
      <template v-if="isSelf">
        <span v-if="false" @click="handleOpt('edit')">编辑</span>
        <span @click="handleOpt('del')">删除</span>
      </template>
      <span v-else @click="handleOpt('reply')">回复</span>
    </div>
    <div
      class="markdown-body editor__style"
      style="padding: 0;"
      v-html="detail.inputCompiler"
    />
  </box>
</template>

<script lang='ts'>
import Vue from 'vue'
import Box from './box.vue'

export default Vue.extend({
  data () {
    return {
    }
  },

  components: {
    Box
  },

  props: {
    detail: {
      type: Object
    },
    isSelf: {
      type: Boolean
    }
  },

  methods: {
    handleOpt (type: string) {
      this.$emit('opt', type)
    }
  }
})
</script>
