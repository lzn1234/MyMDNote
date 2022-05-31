##### 最低版本支持

- macOS 12.0+
- Mac Catalyst 15.0+
- Xcode 13.0+



##### 使用 Object Capture 来构建 3D 模型



1. 拍摄不同角度的照片。
2. 上传到支持 object Capture API 的macOS 电脑
3. 利用 计算机视觉技术 Photogrammetry 将 一组 2D 照片变成 3D 模型。
4. 该模型包含坐标信息和材质纹理



##### 照片要求

- 照片需要**足够清晰**且能够**覆盖目标物的所有角度**
- 使用 iphone 和 iPad 拍照，可以得到物体的**立体深度数据**和**重力方向**
  - 立体深度数据：用于复原物体的真实尺寸
  - 重力方向：使物体按照重力方向数值排放





##### PhotogrammetrySession





https://developer.apple.com/cn/augmented-reality/object-capture/

