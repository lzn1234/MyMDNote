RSKImageCropper 图片裁剪框架框架

------

#### 框架导入

pod 导入框架

```swift
pod 'RSKImageCropper'
```

引入头文件

```swift
#import <RSKImageCropper/RSKImageCropper.h>
```

#### 框架使用

使用一个 `imageView` 初始化一个 `RSKImageCropViewController`

```swift
let croper = RSKImageCropViewController(image: (photos?.first)!, cropMode: .custom)
croper.modalPresentationStyle = .fullScreen
croper.delegate = self
croper.dataSource = self
self.present(croper, animated: true)
```

代理方法

```swift
		// 继承代理方法 RSKImageCropViewControllerDelegate,RSKImageCropViewControllerDataSource

		// RSKImageCropViewControllerDelegate
    // 图片已经取消剪切，移除模态框
    func imageCropViewControllerDidCancelCrop(_ controller: RSKImageCropViewController) {
        self.dismiss(animated: true)
    }
    
    // 图片已经被剪切，操作已经剪切好的图片
    func imageCropViewController(_ controller: RSKImageCropViewController, didCropImage croppedImage: UIImage, usingCropRect cropRect: CGRect, rotationAngle: CGFloat) {
        self.imageView1.image = croppedImage
        self.dismiss(animated: true)
    }
    
    // 图片将要被裁减，调用活动指示器，可能要耗费一点时间
    func imageCropViewController(_ controller: RSKImageCropViewController, willCropImage originalImage: UIImage) {
        
    }

		// RSKImageCropViewControllerDataSource
    // 返回矩阵来设置裁剪框
    func imageCropViewControllerCustomMaskRect(_ controller: RSKImageCropViewController) -> CGRect {
        return CGRect.init(x: (screenWidth-100)/2, y: (screenHeight-100)/2, width: 200, height: 200)
    }
    
		// 返回自定义的贝塞尔曲线来设置裁剪框
    func imageCropViewControllerCustomMaskPath(_ controller: RSKImageCropViewController) -> UIBezierPath {
        let imageRect  = CGRect.init(x: 20, y: (screenHeight-screenWidth)/2, width: screenWidth-40, height: screenWidth-40)
        return UIBezierPath.init(roundedRect: imageRect, cornerRadius: 0)
    }
    
    @optional
		/**
		返回一个图片可以移动的矩形区域
		仅在RSKImageCropModeCustom下有效
		如果你想支持图片旋转，则必须实现该方法
		 */
    func imageCropViewControllerCustomMovementRect(_ controller: RSKImageCropViewController) -> CGRect {
        return controller.maskRect
    }
```

注意：虽然可以通过返回UIBezierPath展示不同形状的效果，但裁剪还是以返回的CGRect为准。建议返回相同的区域。