在组件中直接引入 waterMark.ts 解构出相应的方法进行使用即可，其中 waterMark() 方法的参数情况如下表：

|  方法名  | waterMark                                                    |
| :------: | ------------------------------------------------------------ |
|   参数   | `str: string` - 水印文本<br>`createTime: boolean` - 是否添加水印生成时间<br>`container?: HTMLElement` - 水印容器（可选，默认为整个页面） |
|  返回值  | 无                                                           |
|   功能   | 创建水印，并根据需要定时检查是否存在具有相同标识符的元素。监听窗口大小调整，以确保水印的适应性，并在组件销毁时清除监听。 |
| 注意事项 | - `str`参数为水印文本，可以是任意字符串。<br/>- `createTime`参数用于控制是否添加水印生成时间。<br/>- `container`参数是一个可选的参数，用于指定水印的容器，默认为整个页面。如果提供了容器，水印将被添加到指定容器中。如果未提供容器，水印将添加到整个页面中。<br/>- 组件销毁时会自动清除监听，无需手动清除。 |



实际应用例子如下：

```vue
<template>
  <div class="box" ref="boxRef"></div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import { getMark } from "../utils/waterMark";
const boxRef = ref(null); 
const { waterMark } = getMark();
onMounted(() => {
  waterMark("PandaGuo", false, boxRef.value!); //添加水印
});
</script>
<style scoped>
.box {
  width: 500px;
  height: 500px;
  background-color: black;
}
</style>
```

