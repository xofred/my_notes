```vue
        <el-form-item label="唯一标识">
          <el-radio-group v-model="form.id_name" @change="setEpisode">
            <el-radio label="OTHER">无需配置</el-radio>
            <el-radio label="WHEEL">转盘抽奖</el-radio>
            <el-radio label="WORD">集字</el-radio>
          </el-radio-group>
        </el-form-item>
```

Reference: [use v-on:click on radiobutton](https://laracasts.com/discuss/channels/vue/use-v-onclick-on-radiobutton)