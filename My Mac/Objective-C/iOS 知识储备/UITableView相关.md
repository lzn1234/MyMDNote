##### UITableView 和 UICollectionView 的复用机制

- UITableView 在初始化时会创建一个复用池，同时创建出当前页面需要展示所有 cell。

- 但滑动屏幕使得 cell **已经**滑出屏幕时，该 cell 就会进入复用池。

- 但滑动屏幕使得 cell **将要**滑入屏幕时，tableView 就跟根据你提供的服用 ID 去复用池中拿取相应的 cell，如果没找到 cell，就创建一个 cell 展示到屏幕。

  



##### UITableView 的滑动优化技术

　

