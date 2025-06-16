# Rust programming Notes

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

```


