

## SDWebImage

##### 一个为UIImageView提供一个分类来支持远程服务器图片加载的库。

##### SDweSDWebImage提供一个UIImageView的类别以支持加载来自互联网的远程图片。具有缓存管理、异步下载，同一个URL下载次数控制和优化等特征。

##### 基本使用：

```objective-c
1 //导入头文件  
  #import "UIImageView+WebCache.h"
```



```objective-c
2   //调用 sd_setImageWithXXX方法来设置imageView
		/*
		参数
		url：图片网址
		placeholderImage：占位图
		progress：receivedSize、expectedSize、targetURL，查看图片下载进度的block参数
		option：
		*/
    [imageView sd_setImageWithURL:url completed:^(UIImage * _Nullable image, NSError * _Nullable error, SDImageCacheType cacheType, NSURL * _Nullable imageURL) {
        NSLog(@"");
    }];
```



##### SDImageCache的使用：

使用SDImageCache类进行图片的缓存、读取。

```objective-c
		//创建一个chche对象
		SDImageCache *imageCache = [SDImageCache sharedImageCache];
		//根据key从磁盘/内存中读取图片
    UIImage *image = [imageCache imageFromCacheForKey:@"www"];
		//根据存储类型将图片缓存到内存/磁盘中
    [imageCache storeImage:image forKey:@"www" completion:nil];
```



##### 原理：

三级缓存机制：

内存图片缓存

磁盘沙盒缓存

内存操作缓存



内存缓存和磁盘缓存



流程：

首先SDWebImage会先展示placeholderImage，然后SDWebImageManager根据url处理图片，查询内存缓存中是否有图片缓存，若有则回调到前端展示图片。

若没有，则进入到磁盘中查询是否有图片缓存，若有，则把图片添加到内存缓存中，并且回调到前端展示图片。

若没有，则创建一个下载器下载图片，若下载成功，就把它存到内存和磁盘缓存中，并回调到前端进行展示，

```css
   入口 setImageWithURL:placeholderImage:options: 会先把 placeholderImage 显示，然后 SDWebImageManager 根据 URL 开始处理图片。
    进入 SDWebImageManager-downloadWithURL:delegate:options:userInfo:，交给 SDImageCache 从缓存查找图片是否已经下载 queryDiskCacheForKey:delegate:userInfo:.

    先从内存图片缓存查找是否有图片，如果内存中已经有图片缓存，SDImageCacheDelegate 回调 imageCache:didFindImage:forKey:userInfo: 到 SDWebImageManager。

   SDWebImageManagerDelegate 回调 webImageManager:didFinishWithImage: 到 UIImageView+WebCache 等前端展示图片。

  如果内存缓存中没有，生成 NSInvocationOperation 添加到队列开始从硬盘查找图片是否已经缓存。根据 URLKey 在硬盘缓存目录下尝
```

试读取图片文件。这一步是在 NSOperation 进行的操作，所以回主线程进行结果回调 notifyDelegate:。

```css
    如果上一操作从硬盘读取到了图片，将图片添加到内存缓存中（如果空闲内存过小，会先清空内存缓存）。SDImageCacheDelegate 回调 imageCache:didFindImage:forKey:userInfo:。进而回调展示图片。

     如果从硬盘缓存目录读取不到图片，说明所有缓存都不存在该图片，需要下载图片，回调 imageCache:didNotFindImageForKey:userInfo:。共享或重新生成一个下载器 SDWebImageDownloader 开始下载图片。
```

图片下载由 NSURLConnection 来做，实现相关 delegate 来判断图片下载中、下载完成和下载失败。

connection:didReceiveData: 中利用 ImageIO 做了按图片下载进度加载效果。

connectionDidFinishLoading: 数据下载完成后交给 SDWebImageDecoder 做图片解码处理。

图片解码处理在一个 NSOperationQueue 完成，不会拖慢主线程 UI。如果有需要对下载的图片进行二次处理，最好也在这里完成，效率会好很多。

```css
    在主线程 notifyDelegateOnMainThreadWithInfo: 宣告解码完成，imageDecoder:didFinishDecodingImage:userInfo: 回调给 SDWebImageDownloader。
   imageDownloader:didFinishWithImage: 回调给 SDWebImageManager 告知图片下载完成。

    通知所有的 downloadDelegates 下载完成，回调给需要的地方展示图片。

   将图片保存到 SDImageCache 中，内存缓存和硬盘缓存同时保存。写文件到硬盘也在以单独 NSInvocationOperation 完成，避免拖慢主线程。

   SDImageCache 在初始化的时候会注册一些消息通知，在内存警告或退到后台的时候清理内存图片缓存，应用结束的时候清理过期图片。

   SDWI 也提供了 UIButton+WebCache 和 MKAnnotationView+WebCache，方便使用。

  SDWebImagePrefetcher 可以预先下载图片，方便后续使用。

   从上面流程可以看出，当你调用setImageWithURL:方法的时候，他会自动去给你干这么多事，当你需要在某一具体时刻做事情的时候，你可以覆盖这些方法。比如在下载某个图片的过程中要响应一个事件，就覆盖这个方法：
```

```objectivec
    //覆盖方法，指哪打哪，这个方法是下载imagePath2的时候响应
        SDWebImageManager *manager = [SDWebImageManager sharedManager];
         
        [manager downloadImageWithURL:imagePath2 options:SDWebImageRetryFailed progress:^(NSInteger receivedSize, NSInteger expectedSize) {
             
            NSLog(@"显示当前进度");
             
        } completed:^(UIImage *image, NSError *error, SDImageCacheType cacheType, BOOL finished, NSURL *imageURL) {
             
            NSLog(@"下载完成");
    }];
```

![img](https://upload-images.jianshu.io/upload_images/1388998-9bf0a1d05db2de85.png?imageMogr2/auto-orient/strip|imageView2/2/w/806/format/webp)