<script>
import {marked} from 'marked'
import {debounce} from 'lodash-es'

export default
{
  data()
  {
    return {
      input: '# hello',
    }
  },
  computed:
  {
    output()
    {
      return marked(this.input)
    }
  },
  methods:
  {
    update: debounce(function(e)
    {
      this.input = e.target.value
    })
  },
}
</script>

<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<style>
body
{
  margin: 0;
}
.editor
{
  display: flex;
  height: 100vh
}

.input, .output
{
  box-size: border-box;
  height: 100%;
  width: 50%;
  overflow: auto;
  padding: 0 20px;
}

.input
{
  resize: none;
  border: none;
  border-rigth: 1px solid #858585;
  background: #C4BBBB;
  font-size: 20px;
  padding: 20px;
  outline: none;
  font-family: "Times New Roman";
}
</style>