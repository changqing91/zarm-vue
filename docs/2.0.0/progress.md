<script>
export default {
  data() {
    return {
      percent: 10,
      theme: 'primary',
      shape: 'round',
      weight: 'normal',
      prefixCls: 'za-progress',
      dataSource:[
        { value: 'default', label: 'default' },
        { value: 'primary', label: 'primary' },
        { value: 'info', label: 'info' },
        { value: 'warning', label: 'warning' },
        { value: 'error', label: 'error' },
      ],
      shapeSource:[
        { value: 'rect', label: 'rect' },
        { value: 'round', label: 'round' },
      ],
      weightSource:[
        { value: 'normal', label: 'normal' },
        { value: 'thin', label: 'thin' },
        { value: 12, label: '12' },
      ],
    }
  },
  methods: {
    handleStepChange(e) {

    },
    handleOk(v) {
      this.theme = v.value;
    },
    handleShape(v) {
      this.shape = v.value;
    },
    handleWeight(v) {
      this.weight = v.value;
    },

  },
};
</script>

## 进度条 Progress

:::demo 基本
```html
  <div class="progress" style="padding:20px 0;">
    <za-progress :percent='percent' :theme='theme' :shape='shape' :weight='weight' :prefixCls='prefixCls' >
      {{percent + '%'}}
    </za-progress>
  </div>
  <div class="progress">
    <za-progress type='circle' :percent='percent' :theme='theme' :shape='shape' :weight='weight' :prefixCls='prefixCls'>
      <div class="progress-content">
        <span class="progress-text">{{percent}}</span><span class="progress-percent">%</span>
      </div>
    </za-progress>
  </div>
  <div class="progress">
    <za-progress type='semi-circle' :percent='percent' :theme='theme' :shape='shape' :weight='weight' :prefixCls='prefixCls'>
      <div class="progress-content">
        <span class="progress-text">{{percent}}</span><span class="progress-percent">%</span>
      </div>
    </za-progress>
  </div>

  <za-cell title='进度'>
    <za-stepper
      shape="radius"
      :step='10'
      :min='0'
      :max='100'
      v-model='percent'
      @step-change='handleStepChange'
    />

  </za-cell>
  <za-cell title='主题'>
    <za-select
      :defaultValue='theme'
      :data-source='dataSource'
      @ok='handleOk'
    />
  </za-cell>
  <za-cell title='线条形状'>
    <za-select
      :defaultValue='shape'
      :data-source='shapeSource'
      @ok='handleShape'
    />
  </za-cell>
  <za-cell title='线条粗细'>
    <za-select
      :defaultValue='weight'
      :data-source='weightSource'
      @ok='handleWeight'
    />
  </za-cell>
  <za-cell title='修改类名前缀'>
    <za-input type="text" placeholder="请输入修改类名前缀" v-model='prefixCls'></za-input>
  </za-cell>
```
:::

### API

| 属性 | 类型 | 默认值 | 可选值／参数 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| prefixCls | string | za-progress | | 类名前缀 |
| theme | string | 'primary' | 'default', 'primary', 'info', 'success', 'warning', 'error' | 主题 |
| percent | number | 0 | | 进度百分比（范围：0～100） |
| shape | string | 'rect' | 'rect', 'round' | 线条形状 |
| weight | string or number | 'normal' | 'normal', 'thin' , 线条粗细(px) | 线条粗细 |
| type | string | 'line' | 'line', 'circle' , 'semi-circle' | 类型 |
