<template>
  <span class="door-main">
    <div
      :class="{ 'door-select': select && !open, 'door-open': open }"
      class="door"
      @click="select = !select"
    >
      <span
        :class="{ 'door-number-select': select, 'door-number-open': open }"
        class="door-number"
      >
        {{ number }}
      </span>
      <div
        :class="{ 'doorknob-select': select, 'doorknob-open': open }"
        class="doorknob"
        @click="open = true"
      />
    </div>
    <div class="footer" />
    <div class="prize" v-if="number === prize">
      <div class="top">
        <div class="vertical-line" />
      </div>
      <div class="body">
        <div class="horizontal-line" />
        <div class="vertical-line" />
      </div>
    </div>
  </span>
</template>

<script>
export default {
  props: ["number", "prize"],
  data() {
    return {
      select: false,
      open: false,
    };
  },
};
</script>

<style>
.door-main {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 155px;
  margin: 5px;
  margin-bottom: 15px;
  position: relative;
}
.door {
  width: 125px;
  height: 215px;
  background: rgb(198, 109, 50);
  border: solid 2px brown;
  border-bottom: 0;
  color: white;
  display: flex;
  flex-direction: column;
  z-index: 1;
}
.door-number {
  user-select: none;
  font-size: 18pt;
  justify-self: center;
  margin-top: 15px;
  margin-left: auto;
  margin-right: auto;
}
.door-number-select {
  color: #f1c40f;
}
.door-number-open {
  color: transparent;
}
.doorknob {
  height: 12px;
  width: 12px;
  border-radius: 50%;
  background: brown;
  margin-top: 50px;
  margin-left: 10px;
  z-index: 5;
}
.doorknob-select {
  background-color: #f1c40f;
}
.doorknob-open {
  background-color: transparent;
}
.footer {
  height: 10px;
  width: 155px;
  background: gray;
}
.prize {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  bottom: 10px;
  margin: 0;
  padding: 0;
  z-index: -3;
}
.top {
  height: 20px;
  width: 70px;
  background-color: #2ecc71;
  display: flex;
  align-content: center;
  justify-content: center;
}
.body {
  position: relative;
  height: 50px;
  width: 65px;
  background-color: #27ae60;
  display: flex;
  align-content: center;
  justify-content: center;
}
.door-select {
  border-color: #f1c40f;
}
.door-open {
  background-color: rgba(0, 0, 0, 0.096);
}
.horizontal-line {
  width: 100%;
  height: 10px;
  background: #e74c3c;
  margin: auto;
}
.vertical-line {
  width: 10px;
  height: 100%;
  background: #e74c3c;
  position: absolute;
  margin: auto;
}
</style>