# CS340 Operating Systems

## HOP10 -- BASH -- String Manipulation

### Preparation

1. Connect to your Ubuntu instance
   + Open a command prompt
   + Syntax: ssh -i LOCATION_OF_YOUR_KEY ubuntu@PULIC_DNS
   + Example:

    ```go
    ssh -i key.pem ubuntu@ec2-33-222-101-222.us-west-2.compute.amazonaws.com
    ```

1. Navigate to your name directory under the IS340-Summer-2020

    ```sh
    cd ~/ IS340-Summer-2020/ThaddeusThomas
    ```

1. Create a Module9 directory under [ThaddeusThomas] directory.
__Note__: If this directory exists, skip this step.

    ```sh
    mkdir Module9
    ```

1. Navigate to the Module9 directory.

    ```sh
    cd Module9
    ```

### Concatenate strings

1. Concatenating strings is very easy in the Bash. Try it by typing follow commands:

    ```sh
    str1=Kevin
    str2=Wang
    str3="$str1 $str2 says hi"
    echo $str3
    ```

1. After Bash 3.1, we can use += operator to concatenate strings. Test it by typing the following command:

    ```sh
    str3+=" there."
    echo $str3
    ```

### Process character by character and reverse a string

1. Test the following commands to see how bash script can get whole string without the first or last character:

    ```sh
    testString=TestString
    echo ${testString#?}
    echo ${testString%?}
    ```

1. __Note:__
   + `#?` means marking one character from beginning
   + `%?` means marking one character from the end
   + You can use `#??` to mark two characters.

1. So, we can use the follow combined commands to get the first or last character:

    ```sh
    echo ${testString%${testString#?}}
    echo ${testString#${testString%?}}
    ```

1. Try to use the technic we learned above to make a function that helps to reverse a string. Type the following command to create a script file:

    ```sh
    nano Reverse.sh
    ```

1. Type the script into the file as below:

    ```sh
    #! /bin/bash

    reverse() {
        str=$1
        reversedStr=
        while [ -n "$str" ]
        do
            temp=${str%?}
            reversedStr=$reversedStr${str#$temp}
            str=$temp
        done
        printf "The reversed string is: %s\n" "$reversedStr"
    }
    ```

1. Hit [CTRL+X] to quit and save the file
1. Type the following command to source the file:

    ```sh
    . Reverse.sh
    ```

1. Type the following command to test the reverse function:

    ```sh
    reverse abcde
    ```

### Case conversion

1. The tr command can help to make a character map. Test it by typing the following commands:

    ```sh
    echo abc | tr abc ABC
    echo abc | tr c C
    echo abc | tr abc efg
    ```

    __Note__: as you can see the tr command is offering a map that can map a character to any other character.

1. Try this command to map a group of characters:

```sh
echo "This is a full sentence." | tr 'a-z' 'A-Z'
```

1. Sometimes, we want to compare two strings that have the same characters with different cases. We can convert both strings to uppercase and compare them. Try it by typing the following commands:

```sh
str1=abc
str2=aBc
[[ $str1 == $str2 ]] && echo equal || echo "Not equal"
```

The result shows they are not equal since we have different cases for the letter b.
Use the following commands to overcome this:

```sh
[[ ${str1^^} == ${str2^^} ]] && echo equal || echo "Not equal"
```

### Insert characters in a string

1. In order to perform the insertion, we have to separate the original string to the left and right part. Try this by typing the following commands:

```sh
str1=abcd
echo ${str1:0:2}
echo ${str1:2}
```

1. Now we can use this approach to make an insert function. Create a script file by typing the following command:

```sh
nano Insert.sh
```

1. Type the following script in the file:

    ```sh
    #! /bin/bash
    insert() {
        str=$1
        left=${str:0:$(( $3 - 1 ))}
        right=${str:$(( $3 - 1 ))}
        printf "The final string is: %s\n" "$left$2$right"
    }
    ```

1. Hit [CTRL+X] key to quit and save the file:
1. Test the following commands to test the new function:

    ```sh
    . Insert.sh
    insert Hllo e 2
    ```

### Trim unwanted characters

1. Type the following command to create a trim script:

    ```sh
    nano Trim.sh
    ```

1. Type the following script in the file:

    ```sh
    #! /bin/bash
    trim() {
        str=$1
        left=${str%%[!$2]*}
        str=${str#"$left"}
        right=${str##*[!$2]}
        str=${str%"$right"}
        printf "The final string is: %s\n" "$str"
    }
    ```

1. Hit [CTRL+X] key to quit and save the file.
1. Test the script by typing follow commands:

    ```sh
    . Trim.sh
    trim 0000213.43000 0
    ```


### Push your work to GitHub

Run the following commands to push your work to the GitHub repository:

```sh
git add .
git commit -m “Submission for Module 10”
git push origin ThaddeusThomas_Module_10
```

Note: you should change the YOUR_BRANCH_NAME to your own branch name. It should be firstname-lastname (e.g. maria-gracia).
If you cannot remember, run the command “git status” to check.
