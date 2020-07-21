# 问题记录

### 1.v-html注意
    v-html不建议使用字符串模板引擎或进行动态传值，会存在注入攻击的风险，应该尽量使用组件
    v-html一般只用在某些固定值的显示或可信内容的显示上，而不要针对用户可修改的内容进行使用
### 2.计算属性computed
    计算属性中方法必须有返回值
    计算属性中不能修改data中数据内容
    计算属性有默认有get，可以手动添加set方法，用于将计算属性返回值赋值给data中相应数据
### 3.v-if和v-for
    注意v-if和v-for不能混合使用
### 4.组件及props传值
    一般情况下，props中子组件不可直接改变props中的值，只能由父组件更改（父->子单向传递）
    子组件中props中内容是供父组件调用改变的值的接口数据
    若实现父子组件双向传递：
    1.父组件使用v-model传递；
    2.子组件中使用中间变量接收父组件传过来的值；
    3.子组件watch监听两个值的改变并调用父组件中相应的v-on及回调method；
    4.在父method中完成数据的接收并使用
### 5.插槽slot
    slot在组件中可以设置默认值（原始内容），当调用处不设置任何值时，插槽中默认内容会显示；
    当调用处设置具体值时，插槽中内容会被替换
### 6.组件（动态/异步）
    动态组件使用<keep-alive>标签包裹，可以缓存标签内的内容，下次回来依然保持上次的状态而不被重新渲染
### 7.ref和$refs（仅限于dom操作）
    ref作用于任何标签，相当于为dom绑定一个唯一id
    使用$refs访问已经绑定标签的ref名称，可以实现对标签的dom访问和操作
    对于组件绑定ref，可以通过对象方式访问组件内任何对象或方法
    当ref和v-for一起使用时，得到的ref是一个子组件的数组
    $refs只在组件渲染完成后才能生效
### 8.filter过滤器
    要过滤的字段后面跟“|”，过滤器后面跟的方法是串联形式
    Vue实例或组件中在filters中定义过滤器方法
    过滤器方法可以有参数，默认第一个参数是要过滤的字段，后面参数为自定义参数，可省略也可以根据要求添加
### 9.Vuex-store
    引入VueX，使用Vue.use(Vuex)，使用Vuex，实例化store，在根组件中引入store并定义
    store中state为根状态管理，可以用来管理全局变量，但不能在组件中直接访问
    getter，类似组件的computed，可提供方法供组件计算属性调用或使用...mapGetters
    mutations,同步操作，子组件中方法使用commit(functionName,args..)形式调用或用于操作stats中数据，可以使用...mapMutations
    actions，与mutations不同，可以异步操作，可以使用...mapActions
    项目中如有必要可以将getter、mutations、actions抽离为单独的js文件
### 10.