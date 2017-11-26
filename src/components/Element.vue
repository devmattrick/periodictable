<template>
  <div class="element" :class="categoryClass">
    <div class="element__atomic-number">
      {{ element.atomicNumber }}
    </div>
    <div class="element__symbol" :class="phaseClass">
      {{ element.symbol }}
    </div>
    <div class="element__name">
      {{ element.name }}
    </div>
    <div class="element__atomic-mass">
      {{ element.atomicMass }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'element',
  props: {
    element: {
      type: Object,
      default() {
        return {
          atomicNumber: 1,
          symbol: 'H',
          name: 'Hydrogen',
          atomicMass: 1.00794,
          category: 'nonmetal',
          phase: 'gas',
        };
      },
    },
  },
  computed: {
    categoryClass() {
      const classes = {};
      classes[`element--${this.element.category}`] = true;

      return classes;
    },
    phaseClass() {
      const classes = {};
      classes[`element__symbol--${this.element.phase}`] = true;

      return classes;
    },
  },
};
</script>

<style lang="scss">
  .element {
    padding: 10px 5px;
    width: 100%;
    background-color: #{"rgb(var(--background-color))"};
    cursor: pointer;
    position: relative;
    box-sizing: border-box;

    &:after {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      box-shadow: 0 0 50px #{"rgba(var(--background-color), 0.4)"};
      z-index: -1;
    }

    &.element--alkali-metal {
      --background-color: 255,64,95;
    }

    &.element--alkaline-metal {
      --background-color: 251,139,82;
    }

    &.element--transition-metal {
      --background-color: 64,180,249;
    }

    &.element--basic-metal {
      --background-color: 25,229,86;
    }

    &.element--semimetal {
      --background-color: 188,25,229;
    }

    &.element--nonmetal {
      --background-color: 254,50,193;
    }

    &.element--halogen {
      --background-color: 86,25,229;
    }

    &.element--noble-gas {
      --background-color: 0,229,168;
    }

    &.element--lanthanide {
      --background-color: 101,100,254;
    }

    &.element--actinide {
      --background-color: 199,1,63;
    }

    .element__atomic-number, .element__name, .element__atomic-mass {
      font-size: 0.8em;
      font-weight: 300;
      color: #FFF;
      word-wrap: none;
      text-overflow: ellipsis;
    }

    .element__symbol {
      font-size: 1.5em;
      color: #11111D;

      &.element__symbol--solid {
        color: #FFF;
      }

      &.element__symbol--liquid {
        color: #FFF;
      }

      &.element__symbol--gas {
        color: #FFF;
      }
    }
  }
</style>
