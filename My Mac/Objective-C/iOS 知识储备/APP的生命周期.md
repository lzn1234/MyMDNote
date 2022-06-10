AppDelegate 类的职责

- app 的启动代码

- 负责 App 的生命周期和 SceneDelegate 的创建

  

SceneDelegate 类的职责

- `sceneDidDisconnect(_:)` 当scene与app断开连接是调用（注意，以后它可能被重新连接）

- `sceneDidBecomeActive(_:)`  当用户开始与scene进行交互（例如从应用切换器中选择场景）时，会调用

- `sceneWillResignActive(_:)`  当用户停止与scene交互（例如通过切换器切换到另一个场景）时调用

- `sceneWillEnterForeground(_:)` 当scene变成活动窗口时调用，即从后台状态变成开始或恢复状态

- `sceneDidEnterBackground(_:)` 当scene进入后台时调用，即该应用已最小化但仍存活在后台中



APP 在进入后台后，绝大部分情况会暂停实执行代码，进入刮起状态，你可以使用 UIBackgroundTaskIdentifier 让任务可以在后台执行之后在挂起。