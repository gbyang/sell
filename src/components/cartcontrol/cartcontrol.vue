<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease" v-show="food.count > 0" @click.stop.prevent="decreaseCart">
          <i class="inner icon-remove_circle_outline"></i>
      </div>
    </transition>
    <div class="cart-count"  v-show="food.count > 0">{{ food.count }}</div>
    <div class="cart-add icon-add_circle" @click.stop.prevent="addCart"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      food: {
        type: Object
      }
    },
    methods: {
      addCart () {
        if (!this.food.count) {
          this.$set(this.food, 'count', 1)
          this.food.count = 1
        } else {
          this.food.count ++
        }
        this.$emit('add', event.target)
      },
      decreaseCart () {
        if (this.food.count > 0) {
          this.food.count --
        }
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartcontrol
    font-size: 0
    .cart-decrease
      display: inline-block
      padding: 6px
      &.move-enter-active, &.move-leave-active
        transition: all 0.5s ease
      &.move-enter, &.move-leave-to
        opacity: 0
        transform: translateX(36px) rotate(180deg)
      .inner
        line-height: 24px
        font-size: 24px
        color: rgb(0,160,220)
    .cart-count
      display: inline-block
      vertical-align: top
      width: 12px
      padding-top: 6px
      line-height: 24px
      text-align: center
      font-size: 10px
      color: rgb(147,153,159)
    .cart-add
      display: inline-block
      padding: 6px
      line-height: 24px
      font-size: 24px
      color: rgb(0,160,220)

</style>

