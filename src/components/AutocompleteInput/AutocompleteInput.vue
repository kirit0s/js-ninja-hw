<template>
  <section class="autocomplete">
    <input
      v-model="text"
      class="autocomplete__input"
      type="text"
      @input="getList">
    <div v-if="text !== ''">
      <div
        v-for="item in list"
        :key="item.name"
        class="autocomplete__list">
        {{ item.name }}
      </div>
    </div>
    <div v-else>введите значение</div>
  </section>
</template>

<script>
export default {
  name: 'AutocompleteInput',
  props: {
    value: {
      type: String,
      default: null,
    },
    getItems: {
      type: Function,
      required: true,
    },
  },
  data: () => ({
    text: '',
    list: '',
    error: '',
  }),
  created() {
    this.text = this.value;
  },
  methods: {
    getList() {
      this.getItems(this.text)
        .then(list => {
          console.log(list);
          this.list = list;
        })
        .catch(err => {
          this.error = err.message;
        });
    },
  },
};
</script>

<style>
* {
  font-family: Segoe UI;
  font-size: 12px;
}

.autocomplete {
  border: 1px solid silver;
  outline: none;
  margin: 0;
  background: #fff;
}

.autocomplete_list {
  border: 1px solid silver;
  border-top: 0;
  position: absolute;
  overflow: auto;
  max-height: 93px;
  background: #fff;
}

#autocomplete, #autocomplete_result {
  width: 200px;
  box-sizing: border-box;
}

#autocomplete, #autocomplete_result p {
  padding: 4px;
  margin: 0;
  color: #000;
}

#autocomplete_result p:nth-child(2n-1) {
  background: #f6f6f6;
}

#autocomplete_result p:hover {
  background: #e5e5e5;
}
</style>
