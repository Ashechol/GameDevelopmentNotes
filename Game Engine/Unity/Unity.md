# Unity 笔记

## 移动旋转的实现

移动的实现相关的组件主要分为四种：

* Transform 组件

* RigidBody 组件

* Character Controller 组件

* NavMesh + NavMeshAgent 组件

### 移动

#### 1. Transform 组件

在 Unity 中，移动其实就是改变物体的 位置（position）旋转（rotation），即物体的transform 。所以可以很容易想到第一种方法，即直接通过物体的 Transform 组件来改变物体的 transform 。

* 线性插值 Vector3.Lerp()

* 平滑阻尼 Vector3.SmoothDamp()
  
  * 运镜

* 球形插值 Vector3.SLerp()
  
  ```csharp
  Void Update()
  {
    // 基于世界坐标移动的方向
    Vector3 worldDirection = transform.forward * moveInput.y + 
                        transform.right * moveInput.x;
    Vector3 selfDirection = new Vector3(moveInput.x, 0, moveInput.y);
  
    Vector3 move = direction * speed * Time.deltaTime;
  
    // transform.position += move
    transform.Translate(move, Space.World);
    transform.Translate(selfDirection * speed * Time.deltaTime);
  }
  ```

### Input System
