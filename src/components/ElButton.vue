<template>
  <button @click="handleClick" :type="nativeType" class="el-button" :class= "[type?'el-button--' + type : '',
  {'is-disabled':buttonDisabled,'is-loading':isloading}
  ]" :disabled="buttonDisabled">
    <i class="el-icon-loading" v-if="isloading"></i>
    <i v-if="icon&&!isloading" :class="icon"></i>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'ElButton',
  props: {
    disabled: Boolean,
    type: {
      type: String,
      default: 'default'
    },
    isloading: Boolean,
    icon: {
      type: String,
      default: ''
    },
    nativeType: {
      type: String,
      default: 'button'
    }
  },
  computed: {
    buttonDisabled () {
      return this.disabled;
    }
  },
  methods: {
    handleClick (evt) {
      // console.log(evt);
      this.$emit('click',evt)
    }
  }
}
</script>

<style>

</style>
