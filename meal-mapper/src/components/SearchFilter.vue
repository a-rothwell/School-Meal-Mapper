<template>
  <div class="border-right" id="search-filter-wrapper">
    <div
      class="tab bg-dialogs border-right border-top border-bottom"
      @click="$emit('toggle')"
    >
      <i class="fas fa-caret-down" />
    </div>

    <InfoPanel :infotype="'note'" :icon="'fa-info-circle'">
      {{ $t("sidebar.info-about-us") }}
      <a href="#" @click="$bvModal.show('about-us')">{{
        $t("sidebar.info-link-text")
      }}</a
      >{{ $t("sidebar.info-end-text") }}
    </InfoPanel>

    <InfoPanel :infotype="'handwash'" :icon="'fa-hands-wash'">
      <b class="themeFont">{{ $t("sidebar.shopsafe") }}</b>
      <br />
      (1) {{ $t("sidebar.stayhome") }}<br />
      (2) {{ $t("sidebar.sixfeet") }}<br />
      (3) {{ $t("sidebar.washhands") }}<br />
    </InfoPanel>
  </div>
</template>

<script>
import InfoPanel from "./InfoPanel.vue";

export default {
  name: "search-filter",
  components: {
    InfoPanel,
  },
  props: {
    isFilterOpen: Boolean,
  },
  computed: {
    tabtitle() {
      return this.isFilterOpen
        ? this.$t("sidebar.close-panel")
        : this.$t("sidebar.open-panel");
    },
  },
};
</script>

<style lang="scss" scoped>
.custom-select {
  font-size: 0.8rem;
  cursor: pointer;
}

#search-filter-wrapper {
  margin-left: -290px;
  -webkit-transition: margin 0.25s ease-out;
  -moz-transition: margin 0.25s ease-out;
  -o-transition: margin 0.25s ease-out;
  transition: margin 0.25s ease-out;
  z-index: 1035;
  max-height: 100vh;
  max-width: 294px;
  padding-top: 80px;
  background: theme-color("secondary");
  @media (prefers-color-scheme: dark) {
    background: theme-color("secondaryDark");
  }
}

#wrapper.toggled #search-filter-wrapper {
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
  @media (prefers-color-scheme: dark) {
    box-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
  }
}

.tab,
#wrapper.toggled .tab {
  z-index: 0;
  box-shadow: 0px 0px 14px 0px rgba(0, 0, 0, 0.4);
  @media (prefers-color-scheme: dark) {
    box-shadow: 0px 0px 14px 0px rgba(255, 255, 255, 0.5);
  }
}

.sidebar-heading {
  padding: 0.875rem 1.25rem;
  font-size: 1.2rem;
}

.list-group {
  width: 290px;
  /* border-bottom: solid 1px rgba(0, 0, 0, 0.125); */
  padding: 0;
}

.list-group-item {
  border: none !important;
  padding: 0 1.25rem;
  border-bottom: none;
  &.need-type {
    margin-bottom: 8px;
  }
}

.list-group.need-day-group {
  padding: 1rem 0 0 0 !important;
}

.list-group-flush.need-day-group .list-group-item:first-child {
  padding-bottom: 1rem !important;
}

.side-nav {
  background: theme-color("secondary");
  @media (prefers-color-scheme: dark) {
    background: theme-color("secondaryDark");
  }
}

.tab {
  font-size: 0.8rem;
  width: 30px;
  height: 60px;
  position: absolute;
  top: 169px;
  z-index: 500;
  left: 0;
  background: theme-color("secondary");
  @media (prefers-color-scheme: dark) {
    background: theme-color("secondaryDark");
  }
  transition: left 0.25s ease-out;
  cursor: pointer;
}

#wrapper.toggled .tab {
  left: 290px;
}

#wrapper.toggled .tab i {
  transform: rotate(90deg);
}
.tab i {
  font-size: 1.5rem;
  color: theme-color("buttons");
  transform: rotate(-90deg);
  margin-top: 18px;
  margin-left: 7px;
}

@media (min-width: 768px) {
  .tab {
    margin-left: 0;
    font-size: 1rem;
  }
}
</style>
