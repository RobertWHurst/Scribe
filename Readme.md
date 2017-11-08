Quil is a easy to use library that supports message levels, multiple
targets, and message contexts. Quil is thread safe and so it is possible
to send loggers accross threads.

[Documentation](http://docs.rs/quil)

# Examples

Basic example:

```rust
# #[macro_use] extern crate quil;
# fn main() {
# use quil::prelude::*;
let logger = Logger::new(Console::new(), context!{ src: "root" });

logger.info("hello world");
# }
```

```shell
Tue,  7 Nov 2017 23:55:42 +0000 - info:    hello world src=root
```

Sub-context example:

```rust
# #[macro_use] extern crate quil;
# fn main() {
# use quil::prelude::*;
let logger = Logger::new(Console::new(), context!{ src: "root", tag: "1" });
logger.info("hello");

let sub_logger = logger.ctx(context!{ tag: "", marker: "49" });
logger.info("world");
# }
```

```shell
Tue,  7 Nov 2017 23:55:42 +0000 - info:    hello src=root tag=1
Tue,  7 Nov 2017 23:55:42 +0000 - info:    world src=root marker=49
```