>   1、go中只有for循环语句
>
>   2、for循环语句分为4种



#### 1、for init; condition; post { }

```go
package main

import (
	"fmt"
)

func main()  {
	for i := 0; i < 5; i++ {
		fmt.Println(i)
	}
}
```

```powershell
PS D:\code\test\Go\web1> go run .\main.go
0
1
2
3
4
PS D:\code\test\Go\web1> 
```



#### 2、for condition { }

```go
package main

import (
	"fmt"
)

func main()  {
	i := 0
	for ; i < 5; {
		fmt.Println(i)
		i++
	}
}
```

```powershell
PS D:\code\test\Go\web1> go run .\main.go
0
1
2
3
4
PS D:\code\test\Go\web1> 
```



#### 3、for {}

无限循环

```go
package main

import (
	"fmt"
	"time"
)

func main()  {
	i := 0
	for  {
		fmt.Println(i)
		i++
		// 循环一次睡眠2秒
		time.Sleep(time.Duration(2)*time.Second)
	}
}
```

```powershell
PS D:\code\test\Go\web1> go run .\main.go
0
1
2
3
4
exit status 3221225786
PS D:\code\test\Go\web1>
```



#### 4、for range

```go
package main

import (
	"fmt"
)

func main()  {
	// 创建一个编程语言集合(map)
	programmingLanguages := make(map[int]string)
	programmingLanguages[0] = "C"
	programmingLanguages[1] = "C++"
	programmingLanguages[2] = "Python"
	programmingLanguages[3] = "Java"
	programmingLanguages[4] = "Golang"

	// 遍历集合
	for key, value := range programmingLanguages {
		fmt.Println(key, value)
	}
}
```

```powershell
PS D:\code\test\Go\web1> go run .\main.go
0 C
1 C++
2 Python
3 Java
4 Golang
PS D:\code\test\Go\web1> 
```

