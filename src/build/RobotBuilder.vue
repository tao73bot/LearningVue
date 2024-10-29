<template>
      <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head" alt=""/>
        <button v-on:click="selectPreviousHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="availableParts.arms[selectedArmIndexL].src" title="left arm" alt=""/>
        <button v-on:click="selectPreviousArmL()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextArmL()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="availableParts.torsos[selectedTorsoIndex].src" title="left arm" alt=""/>
        <button v-on:click="selectPreviousTorso()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="availableParts.arms[selectedArmIndexR].src" title="left arm" alt=""/>
        <button v-on:click="selectPreviousArmR()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextArmR()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="availableParts.bases[selectedBaseIndex].src" title="left arm" alt=""/>
        <button v-on:click="selectPreviousBase()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextBase()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';

const getPreviousValidIndex = (currentIndex, length) => {
  const newIndex = currentIndex - 1;
  console.log('Clicked previous');
  return newIndex < 0 ? length - 1 : newIndex;
};

const getNextValidIndex = (currentIndex, length) => {
  const newIndex = currentIndex + 1;
  console.log('Clicked next');
  return newIndex >= length ? 0 : newIndex;
};

export default {
  name: 'RobotBuilder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedArmIndexL: 0,
      selectedArmIndexR: 0,
      selectedTorsoIndex: 0,
      selectedBaseIndex: 0,
    };
  },
  props: {
    msg: String,
  },
  methods: {
    selectNextHead() {
      this.selectedHeadIndex =
        getNextValidIndex(this.selectedHeadIndex, this.availableParts.heads.length);
    },
    selectPreviousHead() {
      this.selectedHeadIndex =
        getPreviousValidIndex(this.selectedHeadIndex, this.availableParts.heads.length);
    },
    selectNextArmL() {
      this.selectedArmIndexL =
        getNextValidIndex(this.selectedArmIndexL, this.availableParts.arms.length);
    },
    selectPreviousArmL() {
      this.selectedArmIndexL =
        getPreviousValidIndex(this.selectedArmIndexL, this.availableParts.arms.length);
    },
    selectNextArmR() {
      this.selectedArmIndexR =
        getNextValidIndex(this.selectedArmIndexR, this.availableParts.arms.length);
    },
    selectPreviousArmR() {
      this.selectedArmIndexR =
        getPreviousValidIndex(this.selectedArmIndexR, this.availableParts.arms.length);
    },
    selectNextTorso() {
      this.selectedTorsoIndex =
        getNextValidIndex(this.selectedTorsoIndex, this.availableParts.torsos.length);
    },
    selectPreviousTorso() {
      this.selectedTorsoIndex =
        getPreviousValidIndex(this.selectedTorsoIndex, this.availableParts.torsos.length);
    },
    selectNextBase() {
      this.selectedBaseIndex =
        getNextValidIndex(this.selectedBaseIndex, this.availableParts.bases.length);
    },
    selectPreviousBase() {
      this.selectedBaseIndex =
        getPreviousValidIndex(this.selectedBaseIndex, this.availableParts.bases.length);
    },
  },
};
</script>
<style>
.part {
  position: relative;
  width:165px;
  height:165px;
  border: 3px solid #aaa;
}
.part img {
  width:165px;
}
.top-row {
  display:flex;
  justify-content: space-around;
}
.middle-row {
  display:flex;
  justify-content: center;
}
.bottom-row {
  display:flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector, .center .next-selector {
  opacity:0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
</style>
