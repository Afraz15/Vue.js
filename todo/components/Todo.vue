<template>
  <div>
    <h3>Todo List</h3>
    <br />
    <form @submit.prevent="sub" action="#">
      <label for="text"><b>Input Task:</b></label>
      &nbsp;
      <input
        v-model="text"
        type="text"
        placeholder="Enter your todo"
        id="text"
      />
      <br /><br />
      <button class="btn btn-success">Submit</button>
    </form>
    <table :key="i.id" v-for="i in todo">
      <tr>
        <td>
          <span :class="{ done: i.stat }"
            ><b> {{ i.title }} </b>
          </span>
        </td>
        <td></td>
        <td><input class="check" type="checkbox" v-model="i.stat" /></td>
      </tr>
      <tr>
        <td>
          <button @click="rem(i)" class="btn btn-danger">Remove</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "Todo",
  data: () => ({
    text: "",
    todo: [],
  }),
  methods: {
    sub() {
      this.todo.push({
        title: this.text,
        stat: false,
      });
      this.text = "";
    },
    rem(todo) {
      const index = this.todo.indexOf(todo);
      this.todo.splice(index, 1);
    },
  },
};
</script>

<style>
div {
  margin: auto;
  width: 50%;
  margin-top: 8rem;
}

b {
  font-size: 1.2rem;
}

h3,
form {
  text-align: center;
}

table {
  margin: 1rem;
}

ul {
  list-style-type: none;
}

.check {
  width: 3rem;
  height: 1.5rem;
}

.done {
  text-decoration: line-through;
}
</style>

