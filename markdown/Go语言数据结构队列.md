😶‍🌫️go语言官方编程指南：[https://golang.org/](https://golang.org/)  

>   go语言的官方文档学习笔记很全，推荐去官网学习

😶‍🌫️我的学习笔记：github: [https://github.com/3293172751/golang-rearn](https://github.com/3293172751/golang-rearn)

---

**区块链技术（也称之为分布式账本技术）**，是一种互联网数据库技术，其特点是去中心化，公开透明，让每一个人均可参与的数据库记录

>   ❤️💕💕关于区块链技术，可以关注我，共同学习更多的区块链技术。博客[http://nsddd.top](http://nsddd.top)

---



 数据结构

[toc]

# 队列

## 队列的使用

```go
/*************************************************************************
    > File Name: queue.go
    > Author: smile
    > Mail: 3293172751nss@gmail.com 
    > Created Time: Sun 03 Apr 2022 04:40:39 PM CST
 ************************************************************************/

 package main
import(
	"fmt"
    "os"
    "errors"
)

//使用一个结构体管理数据
type Queue struct{
    maxSize int 
    array [10]int //数组
	front int //表示指向队列最前面
    rear int //表示指向队列最后面
}

//方法一： 添加数据到队列
func (this *Queue) AddQueue(val int) (err error) {  //可能有错误

    //先判断队满
    if this.rear == this.maxSize -1{
        //提醒！！！rear是队列的尾部（含队列尾部元素--最后一个元素）
        return errors.New("queue full")
    }

    this.rear++      //rear后移
    this.array[this.rear] = val
    return
    
}

//显示队列
func (this *Queue) ShowQueue() {
    //找到队首，遍历到队尾
    fmt.Println("队列当前的的情况是：")
    for i := this.front + 1;i<= this.rear;i++{
        //frout是不包含队首的元素的
        fmt.Printf("arrary[%d]=d\t",i,this.array[1])
    }
}

//取出元素
func (this *Queue) GetQueue() (val int,err error){
    //先判断队列是否为空
    if this.rear == this.front{
        //对空
        return -1,errors.New("Queue empty")
    }
    this.front++      //头后移一位
    val = this.array[this.front]
    return               //或者return val,err
}



func main(){
    
    //先创建一个队列
    queue := &Queue{
        maxSize : 5,
        front : -1,
        rear : -1,
    }

    var key string 
    var val int
    for{
        fmt.Println("1/ 输入add表示添加数据到队列")
        fmt.Println("2/ 输入get表示出队列")
        fmt.Println("3/ 输入show表示显示队列")
        fmt.Println("4/ 输入exit表示退出队列")
        
    
        fmt.Scanln(&key)
        switch key{
        case "add":
            fmt.Println("请输入你要入队列的数")
            fmt.Scanln(&val)
            err := queue.AddQueue(val)
            if err != nil{
                  fmt.Println("err = ",err.Error())
            }else{
             fmt.Println("加入队列成功")
            }
       case "get":         //取出元素
            fmt.Println("get")
            val,err := queue.GetQueue()
            if err != nil{
                fmt.Println("err = ",err.Error())
            }else{
             fmt.Println("取出队列成功val = ",val)
            }
       case "show":
              queue.ShowQueue()
       case "exit":
            os.Exit(0)   //也可以直接使用return
        }
    }
}

```

**编译：**

![image-20220403170952129](https://s2.loli.net/2022/04/03/qYoNJkM75jub1DU.png)

```
PS C:\Users\smile\Desktop\区块链\code\chapter18\tcpdemo\server> go run .\a.go
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
add
请输入你要入队列的数
2
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
add
请输入你要入队列的数
4
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
add
请输入你要入队列的数
q
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
请输入你要入队列的数
1
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
add
请输入你要入队列的数
234
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
show
队列当前的的情况是：
arrary[0]=d     %!(EXTRA int=4)arrary[1]=d      %!(EXTRA int=4)arrary[2]=d      %!(EXTRA int=4)arrary[3]=d      %!(EXTRA int=4)arrary[4]=d      %!(EXTRA int=4)1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
get 1
get
取出队列成功val =  2
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
get
取出队列成功val =  4
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
show
队列当前的的情况是：
arrary[2]=d     %!(EXTRA int=4)arrary[3]=d      %!(EXTRA int=4)arrary[4]=d      %!(EXTRA int=4)1/ 输入add表示添加数据到 队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
exit
```



**上面的队列并没有对空间进行有效的利用，如果实现环形队列！！**



## 环形队列

> 队尾索引的下一个头索引时表示队满。**即队列容量空出一个作为约定，这个在做判断的时候要注意（tail+1)%maxSize == head 表示满**

```go
package main
import (
	"fmt"
	"errors"
	"os"
)

type CircleQueue struct {
	maxSize int //4
	array [4]int 
	head int //指向队列首部
	tail int //指向队列尾部
}

//入队列 AddQueue       出队列 GetQueue(popQueue)
func (this *CircleQueue) Push(val int) (err error){
	 fmt.Println("bool = ",this.IsFull())
	//入队列
	if this.IsFull(){
		return errors.New("queue full")
		//队列满了
	}

	this.array[this.tail] = val  //把值给尾部
	//此时this.tall往后移位
	this.tail = (this.tail+1)%this.maxSize
	return 

}


func (this *CircleQueue) Pop() (val int, err error){
	//出队列，队列空没办法出
	 fmt.Println("bool = ",this.IsEmpty())
	if this.IsEmpty(){
		return 0,errors.New("queue empty")
	}
	//取出
	val = this.array[this.head]
	this.head = (this.head + 1)%this.maxSize
	return
}

//判断环形队列为满了的方法
func (this *CircleQueue) IsFull() bool {
	return (this.tail +1) %this.maxSize == this.head
}

//判断环形队列是否空的
func (this *CircleQueue) IsEmpty() bool {
	return this.tail == this.head
}

//取出环形队列有多少个元素
func (this *CircleQueue) Size() int {
	return (this.tail + this.maxSize - this.head) % this.maxSize
	//由于是环形队列，所以我们在使用的时候要先加上队列的容量，减去头部，最后要%%%%%
}

//显示队列
func (this *CircleQueue) ListQueue() {
	//判断为空，空的话就直接跳出
	//取出当前有多少元素
	fmt.Println("环形队列情况如下：")
	size := this.Size()
	if size == 0{
		fmt.Println("队列为空")
	}

	temp := this.head
	for i := this.head;i<size; i++{
		fmt.Println("aee[%d = %d\t",temp,this.array[this.head])
		temp = (temp +1)%this.maxSize
	}
	fmt.Println()
}

//获取队头元素
func  (this *CircleQueue) GetFront() (val1 int ,val2 int , err error) {
	//判断队空
	if(this.head == this.tail){
		//表示队空
		fmt.Println("取出队列失败，队列为空的 err  ")
		return 0,0,errors.New("queue empty")
	}
		//队列非空
		val1 = this.array[this.head] 
		val2 = this.array[this.tail]
		//获取元素不移位
		return
}
func main(){
	  
    //先创建一个队列
    queue := &CircleQueue{
        maxSize : 5,
		head : 0,
        tail : 0,
    }

    var key string 
    var val int
	var input byte
    for{
        fmt.Println("1/ 输入add表示添加数据到队列")
        fmt.Println("2/ 输入get表示出队列")
        fmt.Println("3/ 输入show表示显示队列")
        fmt.Println("4/ 输入exit表示退出队列")
		fmt.Println("5/ 输入select显示头尾元素")
        
    
        fmt.Scanln(&key)
        switch key{
        case "add","1":
            fmt.Println("请输入你要入队列的数")
            fmt.Scanln(&val)
            err := queue.Push(val)
            if err != nil{
                  fmt.Println("err = ",err.Error())
            }else{
             fmt.Println("加入队列成功")
            }
       case "get","2":         //取出元素
           fmt.Println("get")
            val,err := queue.Pop()
            if err != nil{
                fmt.Println("err = ",err.Error())
            }else{
             fmt.Println("取出队列成功val = ",val)
            }
       case "show","3":
              queue.ListQueue()
       case "exit","4":
            os.Exit(0)   //也可以直接使用return
	   case "select","5":
			//显示首位元素
			a,b,err := queue.GetFront()
			if err != nil{
				fmt.Println("显示失败，err = ",err.Error())
			}else{
				re:    //标记
				fmt.Println("请选择取出的元素 A/a:队首 --- B/b:队尾")
				fmt.Scanln(&input)
				if input == 1 {
					fmt.Println("队首元素为：",a)
				}else if input == 2{
					fmt.Println("队尾元素为：",b)
				}else{
					fmt.Println("你的输入有误，请重新输入")
					goto re
				}
			}
        }
    }
}
```

**编译**

```shell
PS C:\Users\smile\Desktop\区块链\code\chapter18\tcpdemo\server> go run .\a.go
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1
请输入你要入队列的数
3
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
add
请输入你要入队列的数
3
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
show
环形队列情况如下：
aee[%d = %d      0 3
aee[%d = %d      1 3

1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
5
请选择取出的元素 A/a:队首 --- B/b:队尾
a
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
A
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
'a'
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
"a"
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
^S你的输入有误，请重新输入
请选择取出的元素 A/a:队首 --- B/b:队尾
exit status 0xc000013a
PS C:\Users\smile\Desktop\区块链\code\chapter18\tcpdemo\server> go run .\a.go
# command-line-arguments
.\a.go:144:17: invalid operation: input == a (mismatched types byte and int)
PS C:\Users\smile\Desktop\区块链\code\chapter18\tcpdemo\server> go run .\a.go
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
5
取出队列失败，队列为空的 err
显示失败，err =  queue empty
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1
请输入你要入队列的数
add
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
exit status 0xc000013a
PS C:\Users\smile\Desktop\区块链\code\chapter18\tcpdemo\server> go run .\a.go
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1
请输入你要入队列的数
3
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
5
请选择取出的元素 A/a:队首 --- B/b:队尾
1
队首元素为： 3
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
1
请输入你要入队列的数
4
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
add
请输入你要入队列的数
5
bool =  false
加入队列成功
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
show
环形队列情况如下：
aee[%d = %d      0 3
aee[%d = %d      1 3
aee[%d = %d      2 3

1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
2
get
bool =  false
取出队列成功val =  3
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
5
请选择取出的元素 A/a:队首 --- B/b:队尾
2
队尾元素为： 0
1/ 输入add表示添加数据到队列
2/ 输入get表示出队列
3/ 输入show表示显示队列
4/ 输入exit表示退出队列
5/ 输入select显示头尾元素
```

