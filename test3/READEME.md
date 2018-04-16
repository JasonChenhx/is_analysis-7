# 实验3：图书管理系统领域对象建模
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201510414101|软件(本)15-1|安春生|![flow1](../test1/20607259.png)|

## 1. 图书管理系统的类图

### 1.1 类图PlantUML源码如下：

``` class
@startuml
class Borrow_借阅信息类{
    +String  ISBN
    +String  readerId
    +boolean  isOvertime
    +Date  lendDate
    +Date  returnDate
    +add()
    +delete()
    +update()
    +find()
    +save()
}

class Reader_借阅者{
    +String  ID
    +String  name
    +int  maxBorrowNum
    +int  maxBorrowDays
    +int  borrowNum
    +find()
    +borrow()
    +returnDate()
}
class Book_图书信息类{
    +String  ISBN
    +String BookNumber
    +int Inventory
    +add()
    +find()
    +delete()
    +update()
}
class BookDescribeInfo_图书描述{
    +String ISBN
    +String bookName
    +String bookType
    +String describe
    +double price
    +String author
    +String bookVersion
}
class admin_图书管理员{
    String adminID
    String adminName
    +add()
    +find()
    +update()
    +delete
    +payFine()
}
BookDescribeInfo_图书描述"1" ---* "1"Book_图书信息类:Composition
Reader_借阅者"1" ---"m"Book_图书信息类:find
Reader_借阅者"1" --- "m"Borrow_借阅信息类
Book_图书信息类 <... admin_图书管理员:可进行所有操作
Borrow_借阅信息类  <... admin_图书管理员:可进行所有操作
@enduml
```

### 1.2. 类图如下：

![class](class1.png)

### 1.3. 类图说明：
``` 
BookDescribeInfo_图书描述是Book_图书信息的一部分，是对图书信息的详细描述
Reader_借阅者类可以对图书信息类和借阅信息类进行查询操作
admin_图书管理员类可以对图书信息类和借阅信息类进行所有的操作
``` 

## 2. 图书管理系统的对象图
### 2.1 图书信息类的对象图
#### 源码如下：
``` class
@startuml
class Book_图书信息类{
        +String  ISBN
        +String BookNumber
        +int Inventory
        +add()
        +find()
        +delete()
        +update()
}
@enduml
``` 
#### 对象图如下：
![class](class2.png)

#### 说明：
``` 
图书信息类：
    属性：
        ISBN：书号
        BookNumber：图书编号
        Inventory：库存
    方法：
        add()：添加图书
        find()：查找图书
        delete()：删除图书
        update()：更新图书
``` 

### 2.2 借阅者类的对象图
#### 源码如下：
``` class
class Reader_借阅者{
    +String  ID
    +String  name
    +int  maxBorrowNum
    +int  maxBorrowDays 
    +int  borrowNum
    +find()
    +borrow()
    +returnDate()
}
``` 
#### 对象图如下：
![class](class3.png)

#### 说明：
``` 
借阅者类：
    属性：
        ID：借阅者号
        name：借阅者姓名
        maxBorrowNum：最大借书量
        maxBorrowDays：最大借书时限
        borrowNum：借书数量
    方法：
        find()：查找图书
        returnDate()：还书日期
        borrow()：借书
``` 

### 2.3 借阅信息类的对象图
#### 源码如下：
``` class
@startuml
class Borrow_借阅信息类{
    +String  ISBN
    +String  readerId
    +boolean  isOvertime
    +Date  lendDate
    +Date  returnDate
    +add()
    +delete()
    +update()
    +find()
    +save()
}
@enduml
``` 
#### 对象图如下：
![class](class4.png)

#### 说明：
``` 
借阅信息类：
    属性：
        ISBN：书号
        readerId：借阅者号
        isOvertime：是否超出时限
        lendDate：借书日期
        returnDate：还书日期
    方法：
        add()：添加图书
        find()：查找图书
        delete()：删除图书
        update()：更新图书
        save()：保存操作
``` 

### 2.4 图书管理员类的对象图
#### 源码如下：
``` class
@startuml
class admin_图书管理员{
    String adminID
    String adminName
    +add()
    +find()
    +update()
    +delete
    +payFine()
}
@enduml
``` 
#### 对象图如下：
![class](class5.png)

#### 说明：
``` 
图书管理员类：
    属性：
        adminID：图书管理员编号
        adminName：图书管理员姓名
    方法：
        add()：添加图书
        find()：查找图书
        delete()：删除图书
        update()：更新图书
        payFine()：罚金缴纳
``` 

### 2.5 图书描述类的对象图
#### 源码如下：
``` class
@startuml
class BookDescribeInfo_图书描述{
    +String ISBN
    +String bookName
    +String bookType
    +String describe
    +double price
    +String author
    +String bookVersion
}
@enduml
``` 
#### 对象图如下：
![class](class6.png)

#### 说明：
``` 
图书描述类：
    属性：
        ISBN：书号
        bookName：图书名称
        bookType：图书类型
        bookVersion：图书版本
        describe：图书描述
        price：价格
        author：作者
``` 