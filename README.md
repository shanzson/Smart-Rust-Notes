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
    msg += "!";
    println!("{msg}");


```




