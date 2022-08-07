<template>
  <div :key="list.id" v-for="list in lists">
    <List
      @toggle-reminder="$emit('toggle-reminder', list.id)"
      @delete-list="$emit('delete-list', list.id)"
      :list="list"
    />
  </div>
</template>

<script>
import List from './AppList'

export default {
  name: 'AppLists',
  props: {
    lists: Array,
  },
  components: {
    List,
  },
  emits: ['delete-list', 'toggle-reminder'],
}
</script>