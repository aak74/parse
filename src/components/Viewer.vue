<template>
  <div class="viewer">
    <v-btn
      color="info"
      @click="getData"
    >
      Обновить данные
    </v-btn>
    <v-data-table
      :headers="headers"
      :items="items"
      item-key="id"
      hide-actions
    >
      <template v-slot:items="props">
        <td>{{ props.item.fio }}</td>
        <td>{{ props.item.total }}</td>
        <td>{{ props.item.docType }}</td>
        <td>{{ props.item.agreement }}</td>
      </template>
    </v-data-table>
  </div>
</template>

<script>
export default {
  name: 'Viwer',
  data() {
    return {
      headers: [
        { text: 'ФИО', value: 'fio' },
        { text: 'Сумма', value: 'total' },
        { text: 'Вид документа', value: 'docType' },
        { text: 'Согласие', value: 'agreement' },
      ],
    };
  },
  computed: {
    items() {
      return this.$store.state.list;
    },
    getPagination() {
      return [50, { text: 'All', value: -1 }];
    },
  },
  methods: {
    getData() {
      console.log('getData');
      return this.$store.dispatch('getData');
    },
  },
};
</script>
