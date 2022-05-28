# 编程相关知识点

## C Sharp

### 1. 访问修饰符

* private：对象本身在对象内部可以访问；

* public：所有对象都可以访问；

* protected：只有该类对象及其子类对象可以访问；

* internal：同一个程序集的对象可以访问；

* protected internal：访问限于当前程序集或派生自包含类的类型；

> 没有写访问修饰符则默认为 private

### 2. 属性（Properties）

在变量名（约定属性变量大写首字母）后使用花括号以声明属性：

```csharp
public string Name
{
    get{ return name; }
    set{ name = value; }
}


string s = Name  // 这里通过 get 获取了 name 的值
Name = "Hello World!"  // 这里通过 set 给 name 赋值
```

* 通过属性，可以简单地设置变量的读写

```csharp
// 读写
public string Name
{
    get{ return name; }
    set{ name = value; }
}
// 只读
public string Name
{
    get{ return name; }
}
// 只写
public string Name
{
    set{ name = value; }
}    
```

* 可以通过以下方法，简单声明属性

```csharp
public string Name{ get; set; }
```

### 3. 静态变量、函数、类

静态静态变量、函数、类属于类本身，会在程序运行一开始就载入内存，可以直接通过类名调用。非静态属于类的实例，需要先生成类的实例才能被调用。

### 4. 多态

子类实例可以被转换为父类实例（被转化后可以通过强制转换回去）

通过这一特性，在父类定义虚函数。可以实现以下操作:

```csharp
class Parent
{
    public virtual void Call()
    {
        Console.WriteLine("Parent Called");
    }
}

class ChildA : Parent
{
    public override void Call()
    {
        Console.WriteLine("ChildA Called");
    }
}

class ChildB : Parent
{
    public override void Call()
    {
        Console.WriteLine("ChildB Called");
    }
}
/////////////////////////////////////////////////////
void Call(Parent other)  // 参数化多态
{
    other.Call();
}

ChildA a = new ChildA();
ChildB b = new ChildB();

Call(a);  // ChildA Called
Call(b);  // ChildB Called
```

### 5. 接口

接口定义了属性、方法和事件，这些都是接口的成员。接口只包含了成员的声明。成员的定义是派生类的责任。

> 接口命名通常是以 I 开头

如果两个没有继承关系的类都需要用到一些相同的方法，这时候就可以继承一个接口。

### 6. 扩展方法

> 无法扩展静态类，因为需要扩展类的实例

```csharp
static class Extension
{
    public static T ExMethod(this Target t)
    {
        // 使用需要被扩展的类的函数或变量      
    }
}

Target t = new Target()
t.ExMethod()  // 这里不需要填被扩展类的变量
```

### 7. 委托（delegate）

委托类似于 C++ 的函数指针。

- 单委托

```csharp
public delegate void Dlgt();
Dlgt dlgt;

public void DoSomething()
{
    // Do Something
}

dlgt = DoSomething;
dlgt();  // 调用 DoSomething
```

- 多播委托

```csharp
public delegate void Dlgt();
Dlgt dlgt;

pubic void DoSomething1() {
    // Do Something
}
public void DoSomething2() {
    // Do Something
}

// 订阅
dlgt += DoSomething1;  
dlgt += DoSomething2;

dlgt();  // 调用 DoSomething1, DoSomething2

// 退订
dlgt -= DoSomething1
dlgt -= DoSomething2 
```

- `delegate?.Invoke()`

```csharp
Action<T> dlgt;

dlgt?.Invoke();
// 相当于
if (dlgt!= null)
    dlgt();
```

### 8. 匿名方法

### 9. 特性（attribute）

- ExcuteInEditMode

- Range()

### 10. 事件（event）

事件是一种特殊的委托。比起委托，事件有内在安全性。通过事件，其他类只能订阅和退订。而委托可能会被其他类调用或者覆盖委托变量

- `Action<T>`

```csharp
public event Action<T> dlgt;
// 相当于
public delegate void Dlgt(T obj)
public event Dlgt dlgt;
```

### 10. 强制转换

```csharp
// 使用 as 转换失败不会抛出异常二是返回null
// 只支持引用类型转换
string s = someObject as string;
// 转换失败会抛出异常
// 支持引用和值类型转换
string s = (string)someObject;
```

## Unity 脚本生命周期

* `void Awake()` ：即使还没有启用脚本组件还是会被调用，用于初始化；

* `void Start()` ： 必须启用脚本组件，在第一次 Update 前调用；

* `void Update()` ：每帧被调用一次，时间间隔不固定，被上一帧的渲染时间影响

* `void FixedUpdate()` ：固定时间（0.02s）调用一次，用于物理计算

> 继承了 MonoBehavior 的类不要定义构造函数，在 Awake 和 Start 中去实现功能

## 设计模式

### 1. 单例模式

```

```

### 2. 观察者模式