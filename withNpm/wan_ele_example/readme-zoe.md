**使用**
```
cd withNpm/wan_ele_example
// 第一次运行时需要 install
npm install
npm run serve
```

**目录说明**
1. src/components/sample

    示例文件

2. src/components/history

    Zoe 开发过的模板，放到这里做一个统一的展示，后面能用到就直接 copy


**开发过程**
```
// 开始我想一个一个的安装
npm install
npm i element-ui -S

// 后面发现文档中提供了更快捷的安装方式，用下面的指令就可以了
npm install -g @vue/cli
vue create wan_ele_example
npm install highlight.js
cd wan_ele_example
npm run serve

npm install vue-router
```
