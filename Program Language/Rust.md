# Rust 编程语言



## 入门指南

更为现代化，底层依赖 C & C++，似乎所有的高级语言底层皆依赖于此，具有比较完备的开发工具和工具链 `rustup`

macOS安装 Rust：`curl https://sh.rustup.rs -sSf | sh`

Rust 更新：`rustup update`

Rust 卸载：`rustup self uninstall`

查看当前 Rust 版本号：`rustc --version`

查看 Rust 帮助文档：`rustup doc`

格式化代码：`rustfmt main.rs`



常规的 Hello World 环节：

```rust
fn main() {
    println!("Hello, world!");
} 
```

**带 `!` 的是完成对宏的调用而非普通函数的调用**

使用 `ructc {file}`来完成 `.rs` 文件的编译，编译完成后即可将编译文件交付给别人，无需依赖使用环境，和解释型语言不同

单个文件使用 rust` 足以应付，但大型项目需要构建工具，Rust官方提供了：Cargo，是一个构建系统及包管理器

使用 Cargo 来创建项目：`cargo new {project}`

当前工作目录：

```
project
---- .git
---- Cargo.toml
---- src
	---- main.sr
```

Cargo.html 无限接近于 Java 世界当中的 pom.xml

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

使用 Cargo 编译项目：`cargo build`，构建成功的输出在：`target/debug/` 下，可以直接运行，也可以使用 `cargo run` 的方式来依次**完成编译和运行任务**

使用 `cargo check` 来检查是否可以通过编译，而不需要花费额外的时间来生成可执行文件，往往 Rust 开发者会周期性使用这个命令来检查是否能通过编译

> 基于前文所述，Rust 在编译过程当中可以发现绝大多数 Bug，应该是花了大力气在这上面的，所以 check 这条命令很有价值

当修改完成后使用：`cargo build --release` 来完成 release 文件的打包，这种模式会花费更长的编译时间来优化代码，后续的性能基准测试也要基于此



## 猜字游戏

Demo1：Finish input and output

```rust
use std::io;                                                                                           

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

  	// variable in rust default is immutable, use mut keyword let variable mutable
    let mut guess = String::new();
  	// let guess = 2

  	// reference is same sa variable default is immutable, use keyword mut let reference mutable
    io::stdin().read_line(&mut guess)
  			// 对 read_line 函数返回的 Result 进行处理，默认都需要处理 Result
  			.expect("Failed to read line");

    println!("You guessed: {}", guess);
}
```



