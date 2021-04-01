<template>
  <div id="flexi-timeline" class="flexi-timeline">
    <flexi-timeline-item
      v-for="(value, key) in widgets"
      :key="key"
      :index="key"
      :active="currentIndex === key"
      :data-aos="widgetsAos ? widgetsAosType : ''"
      :data-aos-duration="widgetsAosDuration"
      :inputData="value"
      :options="widgetOption"
      :widgets="widgets"
      @button-clicked="handleClick"
    />

    <flexi-pagination
      :currentIndex="currentIndex"
      :widgets="widgets"
      @toggle-back="backPagination"
      @toggle-next="nextPagination"
    />
  </div>
</template>

<script>
import FlexiTimelineItem from "../atoms/flexi-timeline-item";
import FlexiPagination from "../atoms/flexi-pagination";

export default {
  name: "FlexiTimeline",
  components: {
    FlexiPagination,
    FlexiTimelineItem,
  },
  props: {
    widgets: {
      type: Array,
      default: () => {
        return [
          {
            title: "Title 1",
            subTitle: "Subtitle",
            description: "Your awesome description comes here",
            buttonText: "Learn more",
          },
          {
            title: "Title 2",
            subTitle: "Subtitle 2",
            description: "Your awesome description comes here 2",
            buttonText: "Learn more",
          },
          {
            title: "Title 3",
            subTitle: "Subtitle 3",
            description: "Your awesome description comes here 3",
            buttonText: "Learn more",
          },
          {
            title: "Title 4",
            subTitle: "Subtitle 4",
            description: "Your awesome description comes here 4",
            buttonText: "Learn more",
          },
        ];
      },
    },
    widgetOption: {
      type: Object,
      default: () => {
        return {
          title: true,
          subTitle: false,
          description: true,
          button: true,
          active: true,
        };
      },
    },
    widgetsAos: {
      type: Boolean,
      default: () => {
        return false;
      },
    },
    widgetsAosType: {
      type: String,
      default: () => {
        return "fade-up";
      },
    },
    widgetsAosDuration: {
      type: String,
      default: () => {
        return "1500";
      },
    },
  },
  data() {
    return {
      currentIndex: 0,
      currentData: null,
    };
  },
  methods: {
    backPagination() {
      if (this.currentIndex > 0) {
        this.scrollBack("item_" + this.currentIndex);
        this.currentIndex -= 1;
        this.widgets.filter((element, key) => {
          if (key === this.currentIndex) {
            this.currentData = element;
          }
        });
      }
    },
    nextPagination() {
      if (this.currentIndex < this.widgets.length - 1) {
        this.scrollNext("item_" + this.currentIndex);
        this.currentIndex += 1;
        this.widgets.filter((element, key) => {
          if (key === this.currentIndex) {
            this.currentData = element;
          }
        });
      }
    },
    handleClick(singleData, array, id, index) {
      this.$emit("button-clicked", singleData, array, id, index);
    },
    scrollNext(id) {
      const yOffset = -50;
      const element = document.getElementById(id);
      const y =
        element.getBoundingClientRect().top + window.pageYOffset + yOffset;
      window.scrollTo({ top: y, behavior: "smooth" });
    },
    scrollBack(id) {
      const yOffset = -600;
      const element = document.getElementById(id);
      const y =
        element.getBoundingClientRect().top + window.pageYOffset + yOffset;
      window.scrollTo({ top: y, behavior: "smooth" });
    },
  },
  mounted() {
    this.currentData = this.widgets[0];
  },
};
</script>
<style scoped>
.flexi-timeline {
  display: flex;
  max-width: 1300px;
  width: 100%;
  height: 100%;
  padding-top: 120px;
  justify-content: space-between;
  margin: 0 auto;
  flex-wrap: wrap;
  position: relative;
}
</style>
