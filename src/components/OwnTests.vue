<template>
    <div class="own-block" :class="getCssClasses">
        <a class="own-block__item" :href="link" target="_blank" v-on:mousemove.prevent="onMouseMove($event)">
            Google X:{{currentX}} Y:{{currentY}}
            <span v-on:mousemove.stop="">Dont change..</span>
        </a>
        <input  class="own-block__item" type="text"
                @keyup.enter.f1="onKeyUp($event)"
                v-model.lazy="inputValue"/>
        <h4>{{ inputValue }}</h4>
    </div>

</template>

<script>
  export default {
    name: "OwnTests",
    data: function () {
      return {
        link: 'https://google.com',
        currentX: 0,
        currentY: 0,
        inputValue: 'Initial Value',
        isActive: true
      }
    },
    computed: {
      getCssClasses: function () {
        return [{ active: this.isActive }, 'wrapper'];
      }
    },
    methods: {
      onMouseMove: function (e) {
        this.currentX = e.clientX;
        this.currentY = e.clientY;
      },
      onKeyUp: function (e) {
        let target = e.target;
        alert(target.value);
      }
    }
  }
</script>

<style lang="scss" scoped>
    .own-block {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: fit-content;
        padding: 10px;
        margin: 0 auto;
        &__item {
            max-width: 300px;
            margin-bottom: 10px;
        }
    }
    .active {
        background-color: rgba(1, 172, 0, 0.11);
        border-radius: 10px;
    }
</style>