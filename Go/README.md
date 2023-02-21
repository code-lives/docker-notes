# 命令

### go.mod 依赖下载

```
go mod tidy
```

### .ini 文件读取

## [案例]https://github.com/code-lives/socket

- Env
  - env.ini
- src
  - redis
    - redis.go

### chan 使用 range 时候需要关闭 chan,否则循环会发生阻塞

```
	c := make(chan int, 100)
	for i := 0; i < 100; i++ {
		c <- i
	}
	close(c) //
	for val := range c {
		fmt.Println(val)
	}
```
