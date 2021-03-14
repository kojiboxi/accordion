<template>
  <div id="accordion">
    <div id="title" @click="say">
      <p class="title-text">アコーディオン</p>
      <div class="arrow">
        <span></span>
      </div>
    </div>
    <transition
      v-on:before-enter="onBeforeEnter"
      v-on:enter="onEnter"
      v-on:bofore-leave="onBeforeLeave"
      v-on:leave="onLeave"
    >
      <div v-show="show" class="accordion-wrapper">
        <div class="accordion-title">
          <p>アコーディオンの中身が入ります</p>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false
    };
  },
  methods: {
    say: function() {
      this.show = !this.show;
    },
    onBeforeEnter: function(el) {
      el.style.height = 0;
    },
    onEnter: function(el) {
      el.style.height = "100px";
    },
    onBeforeLeave: function(el) {
      el.style.height = "100px";
    },
    onLeave: function(el) {
      el.style.height = 0;
    }
  }
};
</script>

<style scoped>
#accordion {
  height: 310px;
}
#title {
  display: flex;
  width: 400px;
  border: solid;
  border-bottom: none;
  border-width: thin;
  background-color: rgba(171, 171, 194, 0.459);
}

.title-text {
  margin: 20px;
  margin-top: auto;
  margin-bottom: auto;
}

.arrow {
  position: relative;
  height: 90px;
}

.arrow span {
  position: absolute;
  border-style: solid;
  border-width: 15px 9px 0 9px;
  border-color: #7fa3d3 transparent transparent transparent;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
.accordion-wrapper {
  height: 90px;
  width: 400px;
  background-color: white;
  border: solid;
  border-width: thin;
  border-top: none;
}
.accordion-title {
  height: 100%;
  position: relative;
}
.accordion-title p {
  position: absolute;
  margin: 20px;
}
</style>