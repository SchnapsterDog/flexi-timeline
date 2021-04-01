<template>
  <div :id="'item_' + index" class="flexi-timeline-item">
    <slot name="title" v-bind:inputData="inputData">
      <span
        v-if="options.title"
        v-text="inputData.title"
        class="flexi-timeline-item__title"
      />
    </slot>
    <slot name="subtitle" v-bind:inputData="inputData">
      <span
        v-if="options.subTitle"
        v-text="inputData.subTitle"
        class="flexi-timeline-item__subtitle"
      />
    </slot>
    <div class="flexi-timeline-item__description-wrapper">
      <div
        v-if="options.description"
        v-html="inputData.description"
        :class="{ active: active }"
        class="flexi-timeline-item__description-wrapper--description"
      />
      <transition :name="transitionName" mode="out-in">
        <div
          v-if="active && options.active"
          key="content1"
          class="flexi-timeline-item__description-wrapper--active"
        />
      </transition>
    </div>

    <slot name="button" v-bind:inputData="inputData">
      <a
        v-if="options.button"
        @click="handleClick(inputData, widgets, inputData.id, index)"
        class="flexi-timeline-item__button"
      >
        <span v-text="inputData.buttonText" />
      </a>
    </slot>
  </div>
</template>

<script>
export default {
  name: "flexi-timeline-item",
  props: {
    active: {
      type: Boolean,
    },
    index: {
      type: Number,
    },
    inputData: {
      type: Object,
    },
    options: {
      type: Object,
      default: () => {
        return {
          title: true,
          subTitle: true,
          description: true,
          button: true,
          active: true,
        };
      },
    },
    transitionName: {
      type: String,
      default: () => {
        return "active-fade";
      },
    },
    widgets: {
      type: Array,
    },
  },
  methods: {
    handleClick(singleData, array, id, index) {
      this.$emit("button-clicked", singleData, array, id, index);
    },
  },
};
</script>
<style scoped>
.flexi-timeline-item {
  width: 34%;
  margin: 50px 0;
  display: flex;
  flex-direction: column;
  position: relative;
  text-align: left;
  border-bottom: 1px solid grey;
  border-right: 1px solid grey;
}

.flexi-timeline-item:nth-child(even) {
  top: 150px;
}

.flexi-timeline-item__title {
  max-width: 100%;
  width: 450px;
  font-size: 26px;
  font-weight: 600;
  line-height: 1.4;
  color: black;
}

.flexi-timeline-item__button {
  width: auto;
  height: auto;
  position: relative;
  background: transparent;
  font-size: 18px;
  font-weight: 600;
  text-transform: lowercase;
  color: black;
  cursor: pointer;
  border-radius: 0;
  border: none;
}

.flexi-timeline-item__description-wrapper {
  display: flex;
  position: relative;
}

.flexi-timeline-item__description-wrapper--description,
.flexi-timeline-item__description-wrapper--description > ul,
.flexi-timeline-item__description-wrapper--description > p {
  max-width: 500px;
  width: 100%;
  color: black;
  margin: 0;
  padding: 40px 0;
  font-size: 20px;
  font-weight: 600;
  line-height: 1.5;
}

.flexi-timeline-item__description-wrapper--active {
  width: 100%;
  height: 100%;
  position: absolute;
  background: #fddc8f;
  z-index: -1;
  color: #05111f;
}

.active-fade-enter,
.active-fade-leave-to {
  opacity: 0;
}

.active-fade-enter-active,
.active-fade-leave-active {
  transition: opacity 0.3s;
}
</style>