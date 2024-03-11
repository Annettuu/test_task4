<template>
  <div class="app">
    <div class="app__text">
      <span class="app__title">
        {{ title }}
        <span class="app__author">{{ author }}</span>
        <div class="app__checkboxes">
          <div v-for="(stanza, index) of stanzas" :key="stanza.text">
          <v-checkbox
              v-model="stanza.visible"
              @click="value => checkVisibility(value, index)"
          />
          </div>
        </div>
      </span>
      <div v-for="stanza of stanzas">
        <p v-if="stanza.visible" :key="stanza.text">
          {{ stanza.text }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue';
import VCheckbox from "@/components/v-checkbox.vue";

const title = ref('Invictus');
const author = ref('By William Ernest Henley');
const stanzas = ref([
  {
    text: 'Out of the night that covers me,\n' +
        'Black as the pit from pole to pole,\n' +
        'I thank whatever gods may be\n' +
        'For my unconquerable soul.',
    visible: true
  },
  {
    text: 'In the fell clutch of circumstance\n' +
        'I have not winced nor cried aloud.\n' +
        'Under the bludgeonings of chance\n' +
        'My head is bloody, but unbowed.',
    visible: true
  },
  {
    text: 'Beyond this place of wrath and tears\n' +
        'Looms but the Horror of the shade,\n' +
        'And yet the menace of the years\n' +
        'Finds and shall find me unafraid.',
    visible: true
  },
  {
    text: 'It matters not how strait the gate,\n' +
        'How charged with punishments the scroll,\n' +
        'I am the master of my fate,\n' +
        'I am the captain of my soul.',
    visible: true
  }
]);


const checkVisibility = (value, index) => {
  const visibleCount = stanzas.value.filter(s => s.visible).length;
  if (visibleCount === 1) {
    stanzas.value[index].visible = value;

    return;
  }
  stanzas.value[index].visible = !stanzas.value[index].visible;
};
</script>

<style lang="scss" scoped>
.app {
  &__checkboxes {
    display: flex;
    gap: 20px;
    position: absolute;
    right: 230px;
  }

  &__text {
    text-align: center;
    white-space: pre-wrap;
    font-size: 21px;
  }

  &__title {
    font-size: 35px;
    position: relative;
  }

  &__author {
    font-size: 17px;
    position: absolute;
    left: 140px;
    top: 15px;
    width: max-content;
  }

  @media (max-width: 650px) {
    &__title {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    &__checkboxes, &__author {
      position: unset;
    }
  }
}

</style>

