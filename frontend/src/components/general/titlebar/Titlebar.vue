<template>
  <div id="dash-titlebar">
      <i id="dash-titlebar-icon" :class="`bx ${currentMenuItem.icon} bx-md`"/>
      <div id="dash-titlebar-title" class="level-item">{{ currentMenuItem.name }}</div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "TitleBar",
  computed: mapGetters(["allMenuItems", "currentMenuItem"]),
  created() {
    this.updateTitleBar()
  },
  methods: {
    ...mapActions(["switchMenuItem"]),
    updateTitleBar(){
      this.menuItems = this.allMenuItems;
      for (let i = 0; i < this.menuItems.length; i++) {
        if (this.$route.name == this.menuItems[i].name) {
          this.switchMenuItem(this.menuItems[i]);
        }
      }
    }
  },
};
</script>

<style scoped>

#dash-titlebar {
    display: flex;
    gap: 20px;
    align-items: center;
    background: white;
    padding-left: 25px;
    padding-top: 15px;
    padding-bottom: 15px;
    padding-right: 25px;
    /*
    -webkit-box-shadow:0px 0.5px 0.5px #c7ecee;
    -moz-box-shadow:0px 0.5px 0.5px #c7ecee;
    box-shadow:0px 0.5px 0.5px #c7ecee;
    */
    box-shadow: rgba(0, 0, 0, 0.08) 0px 4px 12px;
}
#dash-titlebar-icon {

}
#dash-titlebar-title {
    flex-grow: 4;
    text-align: left;
    font-size: 20px;
    font-weight: 700;
    font-family: "Comic Sans MS", "Comic Sans", cursive;
}
</style>