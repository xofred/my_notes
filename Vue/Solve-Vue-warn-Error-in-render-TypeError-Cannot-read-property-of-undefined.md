page template:
```vue
      <p>活动名称：{{ prize.wheel.name }}</p>
```

before:
```vue
  data() {
    return {
      prize: {},
    }
  },
```

after:
```vue
  data() {
    return {
      prize: {
        wheel: {}
      },
    }
  },
```

I guess response json which contains nested data can't be found when page initialing