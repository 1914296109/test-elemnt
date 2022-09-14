<template>
  <div class="dashboard-container">
    <el-tree
      :props="props"
      :load="loadNode"
      lazy
      show-checkbox
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      props: {
        label: 'name',
        children: 'children',
        isLeaf: 'leaf'
      }
    }
  },
  methods: {
    loadNode(node, resolve) {
      console.log(node, resolve)
      if (node.level === 0) {
        return resolve([{ name: 'region' }])
      }
      // if (node.level > 1) return resolve([])

      setTimeout(() => {
        const data = [{
          name: 'leaf',
          leaf: true
        }, {
          name: 'zone',
          leaf: false,
          children: [
            {
              name: 'leaf',
              leaf: true
            }, {
              name: 'zone'
            }, {
              name: 'zone'
            }, {
              name: 'zone'
            }
          ]
        }]

        resolve(data)
      }, 500)
    }
  }
}
</script>
