<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Tree 
    :data="tree1data" 
    draggable 
    cross-tree
    >
      <div slot-scope="{data, store}">
        <template v-if="!data.isDragPlaceHolder">
          <b v-if="data.children && data.children.length" @click="store.toggleOpen(data)">
            {{data.open ? '-' : '+'}}&nbsp;
            <span>
              {{data.text}}
            </span>
          </b>
        </template>
      </div>
    </Tree>
  </div>
</template>
<script>
import { DraggableTreeNode } from 'vue-draggable-nested-tree';
export default {
  el: '#app',
  components: {Tree: DraggableTreeNode.DraggableTree},
  data() {
    return {
      tree1data: [
          {text: 'node 1'},
          {text: 'node 2'},
          {text: 'node 3 undraggable', draggable: false},
          {text: 'node 4'},
          {text: 'node 4 undroppable', droppable: false},
          {text: 'node 5', children: [
            {text: 'node 1'},
            {text: 'node 2', children: [
              {text: 'node 3'},
              {text: 'node 4'},
            ]},
            {text: 'node 2 undroppable', droppable: false, children: [
              {text: 'node 3'},
              {text: 'node 4'},
            ]},
            {text: 'node 2', children: [
              {text: 'node 3'},
              {text: 'node 4 undroppable', droppable: false},
            ]},
            {text: 'node 3'},
            {text: 'node 4'},
            {text: 'node 3'},
            {text: 'node 4'},
            {text: 'node 3'},
            {text: 'node 4'},
            {text: 'node 3'},
            {text: 'node 4'},
          ]},
        ],
    }
  },
  methods: {
    // add child to tree2
  },
}
</script>

<style lang="scss">
</style>
