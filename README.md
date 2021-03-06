[toc]

## 修饰器
修饰器(Decorator)是一个函数，用来修饰类的行为

修饰器是一个对类进行处理的函数，修饰器函数的第一个参数，就是所要修饰的目标类

修饰器本质是编译时执行的函数

如果想添加实例属性，可以通过目标类的prototype对象操作

## Proxy
Proxy是一个类

Proxy 可以理解成，在目标对象之前架设一层`拦截`，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写

### new Proxy({})
`new Proxy`接收三个参数

会返回一个对象，这个对象和目标对象没有撒区别，只是在你访问(get)或则设置(set)其值的时候，会执行我们通过`new Proxy({})`时注入的额外的逻辑

- 【要拦截的对象】

- 【get方法】用于拦截某个属性的读取操作，可以接收三个参数，依次为
  - 目标对象
  - 属性名
  - proxy实例本身

- 【set方法】用来拦截某个属性的赋值操作，可以接收四个参数，依次为
  - 目标对象
  - 属性名
  - 属性值
  - Proxy实例本身

## mobx
- observable
- observe
- computed
  两种方式:
  1. ↓可用observe监听
  ```
  //类外
    let phone = computed(() => {
      return p1.area + '-' + p1.number;
    });
  ```
  2. ↓不可用observe监听，推荐使用autorun间接进行监听
  ```
  //类里
    @computed get home(){
      return this.province + '-' + this.city;
    }
  ```
- autorun
  当系统启动之后自动运行此函数

  然后当它依赖的数据发生改变时又会再次执行

- when
  when会等待条件满足，一旦满足就会执行回调并自动销毁监听

  when会返回一个disposer销毁函数以供自主销毁

- reaction
  **autorun** 的变种，**autorun** 会自动触发，**reaction** 对于如何追踪 **observe** 赋予更细粒的控制

  它接收两个函数参数，第一个(数据 函数)是用来追踪并返回数据作为第二个函数(效果 函数)的输入

  不同于 **autorun** ,当创建时效果函数不会直接运行，只有在数据表达式首次返回一个新值后才会运行

  可以用在登录信息存储和写缓存逻辑

- action
  前面的方式每次修改都会触发 autorun 和 reaction 执行

  用户一次操作需要修改多个变量，但是视图更新只需要一次

  任何应用都有动作，动作是任何用来修改状态的东西

  动作会【分批处理】变化并只在(最外层的)动作完成后通知计算值和反应

  这将确保在动作完成之前，在动作期间生成的中间值或未完成的值对应用的其余部分是不可见的

- runInAction

- spy
  spy(ev=>console.log(ev));
   全局监听，会监听所有，调试时用
## mobx-react
- observer

