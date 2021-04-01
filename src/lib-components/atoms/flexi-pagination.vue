<template>
  <div class="flexi-pagination">
    <slot name="back-button">
      <a class="flexi-pagination__back" @click="toggleBack">
        <div class="pagination-button">
          <div
            class="pagination-button__svg"
            :class="{ disabled: disabledPrev }"
          />
        </div>
      </a>
    </slot>
    <slot name="next-button">
      <a class="flexi-pagination__next" @click="toggleNext">
        <div class="pagination-button pagination-button--rotated">
          <div
            class="pagination-button__svg"
            :class="{ disabled: disabledNext }"
          />
        </div>
      </a>
    </slot>
  </div>
</template>
<script>
export default {
  name: "flexi-pagination",
  props: {
    currentIndex: {
      type: Number,
      default: () => {
        return 0;
      },
    },
    widgets: {
      type: Array,
    },
  },
  computed: {
    disabledPrev() {
      return this.currentIndex === 0;
    },
    disabledNext() {
      return this.currentIndex === this.widgets.length - 1;
    },
  },
  methods: {
    toggleBack() {
      this.$emit("toggle-back");
    },
    toggleNext() {
      this.$emit("toggle-next");
    },
  },
};
</script>
<style scoped>
.flexi-pagination {
  position: absolute;
  left: 100%;
}

.flexi-pagination__back:active,
.flexi-pagination__next:active {
  background-color: transparent;
}

.pagination-button:hover {
  opacity: 0.8;
}

.pagination-button__svg {
  position: relative;
  cursor: pointer;
  width: 60px;
  height: 60px;
  transform: rotate(90deg);
  background: #d4145a;
  border-radius: 0;
}

.pagination-button__svg::before {
  width: 30px;
  height: 2px;
  margin: auto;
  display: block;
  content: "";
  position: absolute;
  top: 1px;
  left: 4px;
  right: 0;
  bottom: 0;
  z-index: 2;
  background: white;
  transition: all 0.7s;
}

.pagination-button__svg::after {
  width: 0;
  height: 0;
  border-top: 7px solid transparent;
  border-bottom: 7px solid transparent;
  border-right: 13px solid white;
  margin: auto;
  display: block;
  content: "";
  position: absolute;
  top: 1px;
  left: 15px;
  bottom: 0;
  z-index: 2;
  transition: all 0.7s;
}

.pagination-button--rotated {
  transform: rotate(180deg);
}

.disabled {
  opacity: 0.7;
}
</style>