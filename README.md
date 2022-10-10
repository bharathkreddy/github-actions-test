# Github actions
***
## Structure of YAML ✨
- yml or yaml : **Both mean the same thing**
- Similar to json, yaml is **key value pairs**
- Examples
    ```yaml
    name: bharath            //no quotations for Strings//
    age: 23                  //space after the colon//
    address: "47:uplands"    //quotations if string has colons//
    current: true            //boolean values//
    key:                     //can have arbiatry levels//
        key1: value1
        key2: value2
        key3:
            sub_key: sub_value
    array:                  //arrays each object starts with hypen and indented//
        - item1
        - item2
        - {key: value}
    object_array:            //each object in array has 2 keys//
        - key1: value1
          key2: value2
        - keya: valuea
          keyb: valueb
    long_text: >             // same as  "long_text": "fdas fda fd adf  fdasfa  fdabc\n" //
        fdas fda fd adf 
        fdasfa 
        fdabc
    preserve_space: |        //same as "long_text": "fdas fda fd adf \nfdasfa \nfdabc\n" //
        fdas fda fd adf 
        fdasfa 
        fdabc
    ```
## First Workflow✨
***
1. All workflows should be in **.gihub/workflows/** folder
2. Here is the first simple file called [**simple.yml**](.github/workflows/simple.yml)
3. Here is the first actions file called [**actions.yml**](.github/workflows/actions.yml)
4. 