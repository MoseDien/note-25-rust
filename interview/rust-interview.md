# rust
## traits上的范型和关联类型associate types
关联类型 - 每个类只能指定一个具体类型
范型类型 - 每个类可以有多个具体实现-带参数T
```rust
// 泛型：可以为同一个类型实现多个不同的泛型版本
trait Convert<T> {
    fn convert(&self) -> T;
}

struct Number(i32);

impl Convert<String> for Number {
    fn convert(&self) -> String {
        self.0.to_string()
    }
}

impl Convert<f64> for Number {
    fn convert(&self) -> f64 {
        self.0 as f64
    }
}
```

