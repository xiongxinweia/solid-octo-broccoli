😶‍🌫️go语言官方编程指南：[https://golang.org/](https://golang.org/)  

>   go语言的官方文档学习笔记很全，推荐去官网学习

😶‍🌫️我的学习笔记：github: [https://github.com/3293172751/golang-rearn](https://github.com/3293172751/golang-rearn)

---

**区块链技术（也称之为分布式账本技术）**，是一种互联网数据库技术，其特点是去中心化，公开透明，让每一个人均可参与的数据库记录

>   ❤️💕💕关于区块链技术，可以关注我，共同学习更多的区块链技术。博客[http://nsddd.top](http://nsddd.top)

---



 数据结构

[toc]

# 稀疏数组sparsearray

实际需求
---------------

先来看一个实际需求，比较好思考

编写五子棋程序中的 **存盘退出** 和 **续上盘** 功能

![](https://zq99299.github.io/dsalg-tutorial/assets/img/image-20200703215903031.8ffc1996.png)

我们首先能想到的就是使用一个 **二维数组**，如上图所示：

*   0：表示没有棋子
*   1：表示黑棋
*   2：表示白棋

分析问题
---------------

可以看到二维数组中很多值都是 0，因此记录了很多没有意义的数据。

基本介绍
---------------

定义：当一个数组中 **大部分元素为 0（或是同一个值）** 时，可以使用 **稀疏数组** 来保存该数组

处理方法：

1.  记录数组一共有 **几行几列**，**有多少个不同的值**
2.  把具有 **不同值的元素** 的 **行列及值** 记录在一个 **小规模的数组** 中，从而缩小程序的规模

这个小规模的数组就称为 **稀疏数组**，举个例子，如下图

![](https://s2.loli.net/2022/04/03/dA7jP9UY3fzCVO4.png)

左侧是原始的二维数组 `6x7 = 42 个格子`，右侧是稀疏数组 `9 x 3 = 27 个格子`

*   `[0]`：记录了棋盘的大小，6 行 7 列，棋盘上有 8 个不为 0 的值
  
*   其他行：分别记录每一个非 0 值的所在行、所在列、值
  
    比如 `[1]`：在第 0 行第 3 列上有一个 22（这里的行列都是下标）
    

可以看到原始 42 个数据，压缩成 27 个数据。一定程度上压缩了数据。

应用实例
---------------

使用 **稀疏数组** 保留类似前面的 **二维数组**（如棋盘、地图等等的场景），把 **稀疏数组存盘**，并且可以从新 **恢复原来的二维数组**

### 稀疏数组与二维数组互转思路

以前面的棋盘数据来讲解

![](https://s2.loli.net/2022/04/03/Vr4uRL36IGbfw7T.png)

如上图，总结出来稀疏数组为右侧那样。那么他们互转思路如下：

**二维数组转稀疏数组思路：**

1.  遍历原始的二维数组，得到有效个数 sum
2.  根据 sum 创建 **稀疏数组** `sparseArr = int[sum + 1][3]`
3.  将二维数据的有效数据存入到稀疏数组中（从第 2 行开始存储）
4.  最后将棋盘大小和有效个数写入第一行

**稀疏数组转原始二维数组思路：**

1.  读取第一行数据，根据棋盘大小，创建原始的二维数组 `chessArr = int [11][11]`
2.  从第二行开始，将有效数据还原到原始数组中

---

### 代码实现（Go)

```go
/*************************************************************************
    > File Name: chassMap.go
    > Author: smile
    > Mail: 3293172751nss@gmail.com 
    > Created Time: Sun 03 Apr 2022 02:39:52 PM CST
 ************************************************************************/
package main
import (
	"fmt"
)

type valNode struct{
    row int //行
    col int //列
    val int //数值
    //val is struct over
}

func main(){
	//1. 创建一个原始数组
    var chassMap [11][11]int
    chassMap[1][2] = 1   //黑子
    chassMap[2][3] = 2   //篮子
    
    //输出数组是否正确
    for _,v := range chassMap{
        for _,v2 := range v{
            fmt.Printf("%d\t",v2)
        }
        fmt.Printf("\n")

        //转化为稀疏数组。此时必须要使用切片，使用结构体来保存
        //遍历chassmap，如果我们发现有一个元素的值不等于0，此时我们就创建一个node节点，将其放在一个node结构体中
        var sparseArr []valNode 
        
        //标准的稀疏数组应该还有一个 记录元素的二维数组的规模（行和列）
                valNode := valNode{
                    row : 11,
                    col : 11,
                    val : 0,       //行和列  默认是0
                }
        

        //遍历
    for i,v := range chassMap{
        for j,v2 := range v{
            if v2 != 0{
                //创建一个节点 -- valnode 值节点
                valNode := valNode{
                    row : i,
                    col : j,
                    val : v2,
                }
                sparseArr = append(sparseArr,valNode)
    
            }
        }
        fmt.Printf("\n")
    fmt.Println("当前的稀疏数组是:")
    //输出稀疏数组
    for i,valNode := range sparseArr{
        fmt.Printf("%d : %d %d %d",i,valNode.row,valNode.col,valNode.val)
    }
}
}
```



---

### 代码实现（java)

```java
package cn.mrcode.study.dsalgtutorialdemo.datastructure.sparsearray;

/**
 * <pre>
 *  稀疏数组：
 *      1. 二维数组转稀疏数组
 *      2. 稀疏数组转二维数组
 * </pre>
 */
public class SparseArray {
    public static void main(String[] args) {
        // 创建原始二维数组
        // 0：没有棋子，1：黑棋，2：白棋
        // 棋盘大小 11 x 11
        int chessArr[][] = new int[11][11];
        chessArr[1][2] = 1;
        chessArr[2][3] = 2;
      
        // 预览棋盘上的棋子位置
        System.out.println("预览原始数组");
        printChessArray(chessArr);
      
        // 二维数组转稀疏数组
        int[][] sparseArr = chessToSparse(chessArr);
				// int[][] sparseArr = chessToSparse2(chessArr); // 紧凑版本可以参考笔记配套项目
        System.out.println("二维数组转稀疏数组");
        printChessArray(sparseArr);
      
        // 稀疏数组转二维数组
        int[][] chessArr2 = sparseToChess(sparseArr);
        System.out.println("稀疏数组转二维数组");
        printChessArray(chessArr2);
    }

    /**
     * 二维数组转稀疏数组
     *
     * @param chessArr
     */
    private static int[][] chessToSparse(int[][] chessArr) {
        // 1. 遍历数组得到有效棋子个数
        int sum = 0;
        for (int[] row : chessArr) {
            for (int chess : row) {
                if (chess != 0) {
                    sum++;
                }
            }
        }
        // 2. 创建稀疏数组
        int[][] sparseArr = new int[sum + 1][3];
        // 3. 将二维数据的有效数据存入到稀疏数组中（从第 2 行开始存储）
        int chessRow = chessArr.length;  // 行： 棋盘大小
        int chessCol = 0;  // 列： 棋盘大小
        int count = 0; // 记录当前是第几个非 0 的数据
        for (int i = 0; i < chessArr.length; i++) {
            int[] rows = chessArr[i];
            if (chessCol == 0) {
                chessCol = rows.length;
            }
            for (int j = 0; j < rows.length; j++) {
                int chess = rows[j];
                if (chess == 0) {
                    continue;
                }
                count++;  // 第一行是棋盘信息，所以先自增
                sparseArr[count][0] = i;
                sparseArr[count][1] = j;
                sparseArr[count][2] = chess;
            }
        }
        // 4. 补全第一行的棋盘大小和有效数据
        sparseArr[0][0] = chessRow;
        sparseArr[0][1] = chessCol;
        sparseArr[0][2] = sum;
        return sparseArr;
    }

    /**
     * 稀疏数组转二维数组
     *
     * @param sparseArr
     * @return
     */
    private static int[][] sparseToChess(int[][] sparseArr) {
        // 1. 创建二维数组
        int[][] chessArr = new int[sparseArr[0][0]][sparseArr[0][1]];
        // 2. 恢复有效数据到二维数组
        for (int i = 1; i < sparseArr.length; i++) {
            int[] rows = sparseArr[i];
            chessArr[rows[0]][rows[1]] = rows[2];
        }
        return chessArr;
    }
  
    /**
     * 打印棋盘上的棋子布局
     *
     * @param chessArr
     */
    public static void printChessArray(int[][] chessArr) {
        for (int[] row : chessArr) {
            for (int data : row) {
                // 左对齐，使用两个空格补齐 2 位数
                System.out.printf("%-2d\t", data);
            }
            System.out.println("");
        }
    }
}
```



输出信息如下

```
预览原始数组
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	1 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	2 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
二维数组转稀疏数组
11	11	2 	
1 	2 	1 	
2 	3 	2 	
稀疏数组转二维数组
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	1 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	2 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	
0 	0 	0 	0 	0 	0 	0 	0 	0 	0 	0
```





