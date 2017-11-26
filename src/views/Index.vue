<template>
  <div class="table">
    <div class="table-wrapper">
      {{ generate }}
      <table class="elements">
        <tbody>
          <tr class="elements__group">
            <td class="elements__period"></td>
            <td v-for="group in 18">{{ group }}</td>
          </tr>
          <tr v-for="(period, index) in elements">
            <td class="elements__period">
              <template v-if="index < 7">
                {{ index + 1 }}
              </template>
            </td>
            <td v-for="element in period"><xelement :element="element"></xelement></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Element from '@/components/Element';

const elements = require('../assets/elements.json');

export default {
  name: 'index',
  components: {
    xelement: Element,
  },
  data() {
    return {
      elements,
    };
  },
  computed: {
    generate() {
    },
  },
};
</script>

<style lang="scss">
  .table {
    display: flex;
    height: 100%;
    flex-direction: column;

    .table__header {
      text-align: center;
      font-size: 1.5em;
      color: #FFF;

      h1 {
        font-weight: 300;
      }
    }
  }

  .table-wrapper {
    width: 100%;
    overflow-x: auto;
    flex: 1;
  }

  .elements {
    width: 100%;
    color: #FFF;
    padding: 0 20px;
    box-sizing: border-box;
    border-spacing: 0;
    margin: 0 auto;
    table-layout: fixed;

    td {
      padding: 0;
    }

    .elements__group {
      text-align: center;

      td {
        padding: 20px 0;
        width: 100px;
      }
    }

    td.elements__period {
      width: 40px;
      padding-right: 20px;
      text-align: center;
      box-sizing: border-box;
    }
  }
</style>
