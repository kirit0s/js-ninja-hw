<template>
  <autocomplete-input
    v-model="text"
    :get-items="getItems"/>
</template>

<script>
import AutocompleteInput from './AutocompleteInput/AutocompleteInput';

export default {
  name: 'PageHomeWorkOne',
  components: {
    AutocompleteInput,
  },
  data: () => ({
    text: 'from parent',
  }),
  // computed: {
  //   getItems() {
  //     return this.db.filter(item => item.name.includes(this.text));
  //   },
  // },
  created() {
    // предпочитаю не писать в корне объекта
    this.db = [
      {
        name: 'BTC',
        value: 1,
      },
      {
        name: 'ETH',
        value: 2,
      },
      {
        name: 'ABC',
        value: 3,
      },
      {
        name: 'XYZ',
        value: 4,
      },
    ];
  },
  methods: {
    getItems(text) {
      // if (text === '') return Promise.reject(new Error('введите значение'));
      const searchedText = new RegExp(`^${text}`, 'i');
      const data = this.db.filter(item => item.name.match(searchedText));
      if (data.length === 0)
        return Promise.resolve(['такого значение не найдено']);
      return Promise.resolve(data);
    },
  },
};
</script>

<style>

</style>
