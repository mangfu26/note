### defer关键字

说明：用于在 函数/方法 **结束时，返回前** 执行某些操作

```go
package main

import (
	"fmt"
)

func main()  {
	defer fmt.Println("main() 函数运行结束了");
	fmt.Println("我是 main() 函数")
	fmt.Println("测试 defer 关键字")
}
```

```powershell
PS D:\code\test\Go\web1> go run .\main.go
我是 main() 函数
测试 defer 关键字
main() 函数运行结束了
PS D:\code\test\Go\web1>
```



>    defer关键字通常用于做一些收尾工作，例如在一个读取文件内容的函数可以使用defer关键字在函数返回前关闭文件

