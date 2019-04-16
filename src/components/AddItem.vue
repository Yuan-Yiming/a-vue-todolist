<template>
  <p>
    <span v-show="!isAdding" class="add-item" v-on:click="addIt">{{ note }}</span>
    <span v-show="isAdding" class="adding-item editing">
      <input type="" name="" value="" v-model="addingDraft">
      <button v-on:click="addSubmit()">确定</button>
      <button v-on:click="clearAdd()">取消</button>
    </span>
  </p>
</template>

<script>
export default {
  name: 'AddItem',
  props: ['items','editingItem','editingValue'],
  methods: {
    addIt: function () {
      this.isAdding = true;
      this.$emit('clear-editing',{});
    },
    addSubmit: function () {
      if (this.addingDraft.trim()) {
        this.items.push(
        {
          value: this.addingDraft,
          isDone: false,
          isEditing: false,
        });
        this.isAdding = false;
        this.addingDraft = "";
      }
    },
    clearAdd: function () {
      this.isAdding = false;
    },
  },
  data () {
    return {
      note: "Click me to add an item !",
      isAdding: false,
      addingDraft: "",
    }
  },
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p>span {
  display: inline-block;
  font-size: 12px;
  color: #42b983;
  cursor: pointer;
  /*margin-left: 5px;*/
  /*margin: 20px 0;*/
  position: absolute;
  bottom: 32px;
  margin-left: 2px;
  /*border: 1px solid red;*/
}
p>span.add-item {
  text-decoration: underline;
}
p>span.add-item:hover {
  font-size: 14px;
  /*color: orange;*/
  margin-bottom: 0;
  font-weight: bold;
  text-decoration: none;
}

p span.editing input {
  border: 1px solid #42b983;
  outline: none;
  padding: 3px;
  font-size: 12px;
  border-radius: 2px;
  /*border: none;*/
  width: 300px;
}
p span.editing button {
  border-radius: 2px;
  border: none;
  background-color: #42b983;
  padding: 3px;
  font-size: 12px;
  cursor: pointer;
  outline: none;
  
}
p span.adding-item button {
  vertical-align: -1px;
}
p span.editing button:hover {
  color: #fff;
  /*background-color: orange;*/
}
</style>
