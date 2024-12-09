# for 循环和iter
- for循环vec的时候使用引用或者是iter

ref:
- https://rustwiki.org/zh-CN/std/iter/index.html


有三种常见的方法可以从集合中创建迭代器：
- iter()，它在 &T 上迭代。
- iter_mut()，它在 &mut T 上迭代。
- into_iter()，它在 T 上迭代。

## example
```rs
let v = vec![1, 2, 3];

for i in v { // 此时 v 的所有权被转移
    println!("{}", i); // i 是 i32 类型，直接取出 v 中的元素
}
// println!("{:?}", v); // 报错，因为 v 的所有权已被消费

// 如下是正确的方式
for i in &v {
    println!("{}", i); // i 是 &i32 类型，引用了 v 中的元素
}
println!("{:?}", v); // v 依然有效

// 如下也是正确的方式 - 使用iter
let v = vec![1, 2, 3];
for i in v.iter() {
    println!("{}", i);
}
println!("{:?}", v); // v 仍然有效
```
##
```rs
    pub fn plus_one(digits: Vec<i32>) -> Vec<i32> {
        let mut digits = digits;
        for i in (0..digits.len()).rev() {
            if digits[i] < 9 {
                digits[i] += 1;
                return digits;
            } else {
                digits[i] = 0;
            }
        }
        digits.insert(0, 1);
        digits
    }
```