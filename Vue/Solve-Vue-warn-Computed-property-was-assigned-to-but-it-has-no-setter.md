getters:
```javascript
const getters = {
  // wheel
  wheel: state => state.wheel.detail,
  // wheel prize
  prizes: state => state.wheelPrize.list,
  prizeTotal: state => state.wheelPrize.prizeTotal
}

export default getters
```

page template:
```vue
    <p>活动名称：{{ wheel.name }}</p>
```

before:
```vue
  computed: {
    ...mapGetters(['prizes', 'prizeTotal', 'wheel'])
  },
```

after:
```vue
  computed: {
    ...mapGetters(['prizes', 'prizeTotal']),
    wheel: {
      get: function() {
        return this.$store.getters.wheel
      },
      set: function() {
        // no need, read only
      }
    }
  },
```

Reference:

[Getter · Vuex](https://vuex.vuejs.org/zh-cn/getters.html)

[计算属性和侦听器 — Vue.js](https://cn.vuejs.org/v2/guide/computed.html)