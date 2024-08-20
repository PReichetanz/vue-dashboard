<template>
  <div>
    <table class="table">
      <tr>
        <th v-for="(header, i) in headers" :key="`${header}${i}`" class="table__header">
          {{ header }}
        </th>
      </tr>
      <tr v-for="entity in data" :key="`entity-${entity.name}`" class="table__row">
        <td v-for="(header, i) in headers" :key="`${header}-${i}`" class="table__data">
          <slot :name="`column${i}`" :entity="entity"></slot>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'PatientIssueTable',
  props: {
    headers: {
      type: Array,
      required: true
    },
    data: {
      type: Array,
      required: true
    }
  }
}
</script>

<style>
.table {
  border-collapse: collapse;
  width: 100%;
  table-layout: auto;
  word-wrap: break-word;
  background-color: var(--color-background-soft);
}

.table__data {
  padding: 24px;
  text-align: center;
  border-bottom: 1px solid var(--color-border);
}

.table__header {
  padding: 30px 20px;
  font-size: 12px;
  background-color: var(--color-background-mute);
  color: var(--color-heading);
  text-transform: uppercase;
}

.table__row:nth-child(odd) {
  background-color: var(--color-background-soft);
}
</style>
