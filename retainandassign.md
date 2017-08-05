# retain,assign和copy
## retain
retain release旧对象,retain新对象(对其他NSObject和其子类 )
* 使用retain修饰对象,自动生成set和dealloc方法的内存管理

```objectivec
//set
if(_dog != dog){
    [_dog release];
    _dog = [dog retain];
}
//dealloc
[_dog release];
[super dealloc];//一定调用
```
### 循环retian
* 对象相互引用,一方用retain 一方用assign即可

## assign
assign 直接赋值，不做任何内存管理(默认,对基础数据类型(NSInteger)和C数据类型(int,char)等)

## copy
copy copy一个索引计数为1的新对象，然后释放旧对象
(一般用于NSString *,但是对于明确不可变的,还是应该用strong,因为用copy拷贝一个不可变的是浅拷贝,不会生成新的对象,如果用copy,会有一个判断,耗费多余的性能,如果用strong就不会有判断,性能稍微好一点.)

