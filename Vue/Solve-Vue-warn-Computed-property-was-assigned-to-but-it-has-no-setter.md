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