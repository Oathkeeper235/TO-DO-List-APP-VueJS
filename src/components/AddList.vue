<template>
    <form @submit="onSubmit" class="add-list">
    <div class="form-control">
      <label>List Name</label>
      <input type="text" v-model="text" name="text" placeholder="NAME" />
    </div>
    <div class="form-control">
      <label>Choose color</label> 
      <select name="colors" v-model="color">
        <option value="red">RED</option>
        <option value="green">GREEN</option>
        <option value="blue">BLUE</option>
        <option value="pink">PINK</option>
      </select>
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save List" class="btn btn-block" />
  </form>
</template>

<script>
    export default {
        name: 'AddList',
        data() {
            return {
                text: '',
                color: '',
                reminder: '',
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()

                if(!this.text) {
                    alert('Please add a list')
                    return
                }

                const newList = {
                    id: Math.floor(Math.random() * 100000),
                    text: this.text,
                    color: this.color,
                    reminder: this.reminder,
                }

                this.$emit('add-list', newList)

                this.text = ''
                this.color = ''
                this.reminder = false
            }
        }
    }
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input, select {
  background-color: lightblue;
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
  border-radius: 25px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>