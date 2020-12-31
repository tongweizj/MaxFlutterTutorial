# 7.2 存取（getter/setter）方法


---

getter-setter方法格式和写法都是固定的
是程序员之间的一种规范,降低程序员之间的沟通成本


### 1.setter方法
- 作用：用来设置成员变量，可以在方法里面过滤掉一些不合理的值
- 好处
    + 数据不暴露在外,保证了数据的安全性
    + 对设置的数据进行过滤


- 命名规范：
    + 必须是对象方法
    + 返回值类型为void
    + 方法名必须以set开头，而且后面跟上成员变量名去掉”_” 首字母必须大写
    + 必须提供一个参数，参数类型必须与所对应的成员变量的类型一致
    + 形参名称和成员变量去掉下划线相同

- 举例：
```objc
如：如果成员变量为int _age 那么与之对应seter方法为
-(void) setAge: (int) age;
```


### 2.getter方法
- 作用：为调用者返回对象内部的成员变量的值
- 优点：
    + 可以让我们在使用getter方法获取数据之前,对数据进行加工；
    + 比如双十一活动，我们希望对全线商品的价格在原来的价格基础上打五折，那么我们只要去改成品类的价格的getter方法就可以了，让他返回的值为价格 * 0.5


- 命名规范：
    + 必须是对象方法
    + 必须有返回值,返回值的类型和成员变量的类型一致
    + 方法名必须是成员变量去掉下划线
    + 一定是没有参数的

- 举例

```objc
如：如果成员变量为int _age 那么与之对应geter方法为
- (int) age;
```



### 3.getter/setter方法注意
- 在实际的开发中,不一定set和get方法都会提􏰀供,如果内部的成员变量,比如学生的学号或计算出来的数据。这样的数据只允许外界读取，但是不允许修改的情况,则通常只提􏰀供get方法而不􏰀提供set方法
。

- 成员变量名的命名以下划线开头,get方法名不需要带下划线

- 成员变量名使用下划线开头有两个好处
    + 与get方法的方法名区分开来
    + 可以和一些其他的局部变量区分开来,下划线开头的变量,通常都是类的成员变量。当我看到以下划线开头变量，那么他一定是成员变量

### 4. 合成存取方法



```
#Fraction.h
#import <Foundation/Foundation.h>


@interface Fraction: NSObject
{
    int numerator;
    int denominator;
}

@property int numerator;
@property int denominator ;
-(void) print;
//-(void) setNumerator: (int) n;
//-(void) setDenominator: (int) d;
//
//-(int) numerator;
//-(int) denominator;
-(double) convertToNum;

@end

```




```
#Fraction.m
#import "Fraction.h"


@implementation Fraction
@synthesize numerator ;
@synthesize denominator  ;

-(void) print
{
    NSLog( @" %i/%i ", numerator, denominator);
}
//
//-(void) setNumerator: (int) n
//{
//    numerator = n;
//}
//-(void) setDenominator: (int) d
//{
//    denominator = d;
//}
//-(int) numerator{
//    return numerator;
//}
//-(int) denominator
//{
//    return denominator;
//}

-(double) convertToNum
{
    if (denominator !=0)
        return (double) numerator / denominator;
    else
        return NAN;
}
@end

```
