<template>
    <div :style="style" @dblclick="$emit('toggle-reminder', list.id)" :class="[list.reminder ? 'reminder' : '', 'list']">
        <h3>
            {{ list.text }}
            <i @click="$emit('delete-list', list.id)" class="fa fa-times">

            </i>
        </h3>
    </div>
</template>

<script>
    export default {
        name: 'AppList',
        props: {
            list: Object,
        },
        computed: {
          style() {
            return 'background-color: ' + this.list.color
          }
        }
    }
</script>

<style scope>
.fas {
  color: red;
}
.list {
  border-radius: 25px;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.list.reminder {
  border-left: 5px solid greenyellow;
}
.list h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>