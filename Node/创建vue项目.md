```cmd
npm init vite employee

√ Select a framework: » Vue
√ Select a variant: » Customize with create-vue ↗
Need to install the following packages:
create-vue@3.8.0
Ok to proceed? (y) y

Vue.js - The Progressive JavaScript Framework

√ 是否使用 TypeScript 语法？ ... 否 / 是
√ 是否启用 JSX 支持？ ... 否 / 是
√ 是否引入 Pinia 用于状态管理？ ... 否 / 是
√ 是否引入 Vitest 用于单元测试？ ... 否 / 是
? 是否要引入一款端到端（End to End）测试工具？ » - Use arrow-keys. Return to s√ 是否要引入一款端到端（End to End）测试工具？ » 不需要
√ 是否引入 ESLint 用于代码质量检测？ ... 否 / 是

正在构建项目 E:\E\ProjectFile\SB_front\employee_front\employee...

项目构建完成，可执行以下命令：

  cd employee
  npm install
  npm run dev
```

```cmd
// 用于通过 npm安装名为 element-plus 的软件包，并将其保存到    项目的 package.json 文件中的 dependencies 部分
npm install element-plus --save
```

```vue
import { ref, reactive, getCurrentInstance, nextTick } from "vue"
const { proxy } = getCurrentInstance();
```



- `import { ref, reactive, getCurrentInstance, nextTick } from "vue"`：这行代码从 Vue 模块中导入了一些功能。这些功能包括：
  - `ref`: 创建一个响应式的数据引用。
  - `reactive`: 创建一个响应式的对象。
  - `getCurrentInstance`: 获取当前组件实例。
  - `nextTick`: 在 DOM 更新后执行回调函数。
- `const { proxy } = getCurrentInstance();`：这行代码从当前 Vue 组件实例中获取了 `proxy` 对象。

`proxy` 对象是 Vue 3 中 Composition API 的一部分。它提供了对当前组件实例上所有响应式属性和方法的访问。通过这种方式，你可以访问到组件的响应式数据和方法，并在组件中进行操作和处理。