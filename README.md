# Rust programming Notes

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
