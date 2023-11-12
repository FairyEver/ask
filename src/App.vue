<script setup lang="ts">
import { ref } from 'vue'

import type { Ref } from 'vue'

interface SlotItem {
  name: string
  props?: {
    [key: string]: any
  }
  slots?: {
    [key: string]: SlotItem[]
  }
}

interface BoxItem {
  id: string
  height: number
  width: number
  left: number
  top: number
  slots?: {
    [key: string]: SlotItem[]
  }
}
interface EditorData {
  boxes: BoxItem[]
}

// 下面的代码报 demo 类型错误

// const demo: Ref<EditorData> = ref({
//   boxes: [
//     {
//       height: 300,
//       id: '',
//       left: 500,
//       slots: {
//         default: [
//           {
//             name: 'DemoA',
//             slots: {
//               second: [ // second 两个键名设置成不同的
//                 {
//                   name: 'DemoPlay',
//                 },
//               ],
//             },
//           },
//           {
//             name: 'DemoB',
//             slots: {
//               default: [ // default 两个键名设置成不同的
//                 {
//                   name: 'DemoPlay',
//                 },
//               ],
//             },
//           },
//         ],
//       },
//       top: 100,
//       width: 200,
//     },
//   ],
// })

// 但是这样就不报错 奇怪

const demo: EditorData = {
  boxes: [
    {
      height: 300,
      id: '',
      left: 500,
      slots: {
        default: [
          {
            name: 'DemoA',
            slots: {
              second: [
                {
                  name: 'DemoPlay',
                },
              ],
            },
          },
          {
            name: 'DemoB',
            slots: {
              default: [
                {
                  name: 'DemoPlay',
                },
              ],
            },
          },
        ],
      },
      top: 100,
      width: 200,
    },
  ],
}
</script>

<template>
  {{ demo }}
</template>
