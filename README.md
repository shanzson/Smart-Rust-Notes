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


