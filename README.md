# Smart Rust Notes 
### (Courtesy: Smart Contract Programmer YT Channel)

## Main function
```
fn main() {
    // Write all code here
}
```

## Variables

```
    // Variables are immutable by default in Rust

    // Integer
    let x: i32 = -123;

    // Mutable variable
    let mut y: i32 = 123;

    // Assign variables directly
    let z = -123;

    // constant
    const NUM: u32 = 1;

    // Boolean
    let x: bool = true;

    // Vector
    let v: Vec<_> = vec![1, 2, 3];
}
```

## Scalar types

```
// Scalar types represent single, atomic values. They are the most basic building blocks for data in Rust.

    // Range:       -(2**(n-1)) ~ 2**(n-1) - 1
    let i0: i8 = 0; // -2**(8 - 1) ~ 2**(8 - 1) - 1
                    // -128 ~ 127
    let i1: i16 = 1;
    let i2: i32 = 1;
    let i3: i64 = 1;
    let i4: i128 = 1;
    let i5: isize = 1;

    // Unsigned integers
    // 0 ~ 2**n - 1
    let u0: u8 = 1; // 0 ~ 2**8 - 1 = 255
    let u1: u16 = 1;
    let u2: u32 = 1;
    let u3: u64 = 1;
    let u4: u128 = 1;
    let u5: usize = 1;

    // Floats
    let f0: f32 = 0.01;
    let f1: f64 = 0.01;

    // Boolean
    let b: bool = true;

    // Characters
    let c: char = 'c';

    // Type conversion
    let i: i32 = 1;
    let u: u32 = i as u32;
    let x: u32 = u + (i as u32);

    // Min and max
    let min_i: i32 = i32::MIN;
    let max_i: i32 = i32::MAX;

    let min_char: char = char::MIN;
    let max_char: char = char::MAX;

    // Overflow
    let mut u: u32 = u32::MAX;
    u += 1;
    println!("overflow u32: {}", u); // Added 'u' inside the println! macro for correct output

    // checked_add checks for overflows while adding
    let u = u32::checked_add(u32::MAX, 1);

    // wrapping_add allows overflow via wrapping while adding
    let u = u32::wrapping_add(u32::MAX, 1);

}
}
```

## Printing

```
//  Printing variables
    let x = 2;
    println!("{} * {} = {}", x, x, x * x);

//  Printing string
    let lang = "rust";

    println!("hello {}", lang);

    println!("hello {lang}");

//  Printing struct
    #[derive(Debug)]
    struct Lang {
        language: String,
        version: String,
    }

    Method: 1 (Without #)
    let lang_struct = Lang {
        language: String::from("Rust"),
        version: String::from("1.8.3"),
    };

    println!("{:?}", lang_struct);

    Method: 2 (With # which prints struct elements on separate line)
    println!("{:#?}", lang_struct);

}
```

## Tuples

```
    // Tuple
    let t: (bool, u32, char) = (true, 1, 'c');

    // Destructure
    let (a, b, c) = t;

    // ignore with _
    let (_, b, _) = t;

    // Empty tuple - unit type
    let t = ();

    // Nested tuple
    let nested = ((1.23, 'a'), (true, 1u32, 'b'), ());
    let t: (bool, u32, char) = (true, 1, 'c');

    // Printing tuple
    println!("t = {}, {}, {}", t.0, t.1, t.2);
    println!("nested {} {}", nested.0 .0, nested.1 .1);

```

## Array

```
    // Array - fixed length, known at compile time
    let arr: [u32; 3] = [1, 2, 3];
    println!("arr[2] = {}", arr[2]);

    // Mutable array
    let mut arr: [u32; 3] = [1, 2, 3];
    arr[1] = 9;

    // Print array of same elements
    let arr: [u32; 10] = [0; 10];
    println!("{:?}", arr);
    
    // Slice - length not known at compile time
    let nums: [i32; 10] = [-1, 1, -2, 2, -3, 3, -4, 4, -5, 5];
    
    // First 3 elements
    let s = &nums[..3]; // 0, 1, 2
    println!("first 3 elements: {:?}", s);

```
## String and &str

```
    // String = vector of u8 (Vec<u8>) valid UTF-8
    // &str = slice of u8 (&[u8]) valid UTF-8

    // When to use String vs &str
    // String -> mutate or data needs to be owned
    // &str -> read only

    // String
    let msg: String = String::from("Hello Rust 🦀");
    let len: usize = msg.len();

    // str - string slice
    // &str
    // - usually used str with reference (borrowed)
    // - immutable

    let msg: String = String::from("Hello Rust 🦀");
    let s: &str = &msg[0..5];
    let len: usize = s.len();

    // Multi-line string referral
    let s: &str = r#"
    {
        "a": 1,
        "b": { "c": 2 },
        "d": 3
    }
    "#;

    let msg: String = String::from("Hello Rust 🦀");
    let s: &str = &msg;

    // Add &str to String
    let mut msg: String = "Hello Rust".to_string();
    msg += "!";       // Note that only slices can get added to a string
    println!("{msg}");

    // String interpolation - format!
    let lang = "Rust";
    let emoji = "🦀";
    let msg: String = format!("Hello {} {}", lang, emoji);
    println!("{msg}");

    // To convert from slice to string type
    let a: &str;
    let mut astr = String::from(a); 

```
## Enum

```
#![allow(unused)]

#[derive(Debug, PartialEq)]
enum Color {
    Red,
    Green,
    Blue,
    Rgba(u8, u8, u8, f32),
    Hex(String),
    Hsl { h: u8, s: u8, l: u8 },
}

fn main() {
    let color = Color::Blue;
    let color = Color::Rgba(100, 200, 0, 0.4);
    let color = Color::Hex(String::from("ffffff"));
    let color = Color::Hsl { h: 1, s: 2, l: 0 };

    // Debug
    println!("{:?}", color);

    // PartialEq
    println!("blue == red ? {}", Color::Blue == Color::Red);
    println!("green == green ? {}", Color::Green == Color::Green);

    // Option is predefined as this
    enum Option<T> {
        Some(T),    // Has a value of type T
        None,       // No value
    }

    // Option<T> = Some(T) | None
    let x: Option<i32> = None;
    let x: Option<i32> = Some(-1);

    // Result<T, E> = Ok(T) | Error(E)    // Think of it as a type/variation of Option
    let res: Result<i32, &str> = Ok(100);
    let res: Result<i32, &str> = Err("error 💀");
    
}

```

## Struct

```
#[derive(Debug)]
struct Point {
    x: f32,
    y: f32,
}

// Tuple
struct Point3d(i32, i32, i32);

// Empty
struct Empty;

// Nested
#[derive(Debug)]
struct Circle {
    center: Point,
    radius: u32,
}

fn main() {
    // Create
    let p = Point { x: 1.0, y: 1.0 };
    println!("p.x = {}", p.x);
    println!("p.y = {}", p.y);
    // Debug
    println!("{:?}", p);

    let p = Point3d(1, 2, 3);
    println!("{} {} {}", p.0, p.1, p.2);

    let empty = Empty;

    let circle = Circle {
        center: Point { x: 0.0, y: 0.0 },
        radius: 3,
    };
    println!("{:?}", circle);

    // Shortcut
    let x = 1.0;
    let y = 1.0;
    let p = Point { x, y };

    // Copy fields
    let p0 = Point { x: 1.0, y: 2.0 };
    let p1 = Point { x: 2.0, ..p0 };

    println!("{:?}", p1);

    // Update
    let mut p = Point { x: 0.0, y: 0.0 };
    p.x += 1.0;
    p.y += 1.0;
}
```

## Struct methods

```
struct Point {
    x: f32,
    y: f32,
}

impl Point {
    // Associated functions - static methods
    fn new(x: f32, y: f32) -> Self {
        Self { x, y }
    }

    fn zero() -> Self {
        Self { x: 0.0, y: 0.0 }
    }

    // Methods
    fn move_to(&mut self, x: f32, y: f32) {
        self.x = x; 
        self.y = y; 
    }
    fn dist(&self) -> f32 {
        (self.x * self.x + self.y * self.y).sqrt()
    }

    fn move_to(&mut self, x: f32, y: f32) {
        self.x = x;
        self.y = y;
    }
}

fn main() {
    let mut p = Point::new(1.0, 1.0);
    p.move_to(2.0, 0.0);

    let d = p.dist();
    println!("{}", d);
}
```

## Operators
```
-1 / 2 = 0
-1 % 2 = -1

    // Bit shift
    // Left shift
    // When you left shift by n positions, it's equivalent to multiplying by 2^n:
    6u32 << 3
    Original (6):  00000000 00000000 00000000 00000110
                                                 ↑↑
                                               bits 1,2
    
    After << 3:    00000000 00000000 00000000 00110000
                                          ↑↑
                                    bits 4,5

    // Right shift
    // When you right shift by n positions, it's equivalent to dividing by 2^n (integer division)
    10u32 >> 2
    Original (10): 00000000 00000000 00000000 00001010
                                                  ↑ ↑↑
                                                  │ └┴── bits 0,1 (will be lost)
                                                  └───── bit 3 (will move to bit 1)
    
    After >> 2:    00000000 00000000 00000000 00000010
                                                    ↑
                                                    └──── bit 3 moved to bit 1

    let fast_square = x * x;        // Fast
    let slow_square = x.pow(2);     // Slower

    // Type casting
    let a: u32 = 1;
    let b = a as f32;
    println!("b = {b}");

    // Comparisons
    let a = 1;
    let b = 2;
    let c = a == b;
    let c = a != b;
    let c = a <= b;
    let c = a < b;
    let c = a >= b;
    let c = a > b;

    // Boolean
    let c = true && false;
    let c = true || false;
    let c = !true;

    // Bitwise operators
    // 101
    let a: u8 = 5;
    // 011
    let b: u8 = 3;
    println!("a & b = {:03b}", a & b);
    println!("a | b = {:03b}", a | b);
    println!("a ^ b = {:03b}", a ^ b);
    println!("!a = {:03b}", !a);
    println!("1 << 3 = {}", 1u32 << 3);
    // 10 >> 2 = 1010 >> 2 = 10
    println!("10 >> 2 = {}", 10u32 >> 2);

    
```
## If-else statement

```
    if x % 2 == 0 {
        println!("{x} is even");
    } else {
        println!("{x} is odd");
    }

    // Return from conditional statement
    let z: i32 = if x > 0 {
        1
    } else if x < 0 {
        -1
    } else {
        0
    };
```

## Loop
```
    // Loop
    let mut i: u32 = 0;
    loop {
        println!("loop {}", i);
        i += 1;

        if i > 5 {
            break;
        }
    }

    // While loop
    let mut i: u32 = 0;
    while i <= 5 {
        println!("while loop {}", i);
        i += 1;
    }

    // For loop
    for i in 0..5 {
        println!("for loop {}", i);
    }

    // Loop array
    let xs = [1, 2, 3];

    // usize
    let n: usize = xs.len();
    for i in 0..n {
        // This will not compile
        // i is usize
        // let k = i + 1u32;
        println!("{}", xs[i]);
    }

    // Loop using iterator
    for x in xs.iter() {
        println!("for loop iter {}", x);
    }

    // Return value from loop
    let mut i: u32 = 0;
    let v = loop {
        i += 1;
        if i > 3 {
            break "i > 3";
        }
    };
    println!("return value from loop {}", v);

    // Labels
    let mut i = 0;
    'outer: for i in 0..3 {
        'inner: for j in 0..3 {
            println!("{i}, {j}");
            if i == 1 && j == 1 {
                break 'outer;
            }
        }
    }
```

