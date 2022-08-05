# HOP05 – BASH – Looping and branching

## CS 340 – Operating Systems

#### School of Technology & Computing (STC) @ City University of Seattle (CityU)

   ```plaintext
   7/13/2019 Developed by Kevin Wang
   06/17/2020 Reviewed by Kim Nguyen
   03/29/2021 Updated by Matt Raio
   02/14/2022 Reviewed by Ken Ling
   ```

![AWS](./img/CS340_Header.png)

1. **Before You Start**
   - This exercise assumes that the user is working with the Linux distribution in Virtualbox
   - All commands and code discussed in this exercise will run in the Ubuntu console.
   - The directory path shown in the screenshots may be different from yours.
   - Some steps are not explained in the tutorial. If you are not sure what to do:
      - Consult the resources listed below, experiment in the Ubuntu console, and try to solve the problem yourself.
      - If you cannot solve the problem after a few tries, ask a TA for help.

1. Learning Outcomes
   - Students will be able to:
       - Use test command
       - Understand the conditional execution
       - Use input/Output, pipeline, and command substitution

1. Resources
   - [Linux command line: bash + utilities](https://ss64.com/bash/)
   - [Nano/Basics Guide](https://wiki.gentoo.org/wiki/Nano/Basics_Guide)

### Preparation

1. Connect to your Ubuntu instance

---

### Basic usage of the test command

1. Type the following command to test integers:

   ```sh
   test 1 -eq 1
   ```

    |code|Meaning|
    |---|---|
    |`-eq`|equal|
    |`-ne`|not equal|
    |`-gt`|greater than|
    |`-lt`|less than|
    |`-ge`|greater or equal|
    |`-le`|less or equal|

2. Check the result by typing:
   - `$?` is a special parameter that contains the exit code for the last command.
   - `0` means successful when `1` means error.
   - When we use a test command, `0` means `true` and `1` means `false`.

   ```sh
   echo $?
   ```

3. `[]` is the equivalent of test. We can test an integer like this:

   ```sh
   [ 1 -lt -2 ]
   And then, retrieve the result:
   echo $?
   ```

   - Note: Linux Bash script is case sensitive as well as space sensitive.
   - For using the `[]`, we have to keep a space after `[` and before `]`.

4. Use `[[]]` to test a regular expression

    ```sh
    [[abc =~ ^a.*c$]]
    And retrieve the result
    echo $?
    ```

   - Note: We will practice more regular expression in other modules.

5. Use (()) to evaluate an arithmetic expression. (This is a nonstandard feature)

    ```sh
    (( 2 - 1 ))
    echo $?
    (( 1 - 1 ))
    echo $?
    ```

    In Linux, when arithmetic expression value is `0`, it will return `False`. Otherwise, a `True` will be returned.

### If conditional execution

1. The basic syntax of if command shows below:

   ```sh
   if <condition list>
   then
   <list>
   elif <condition list>
   then
   <list>
   else
   <list>
   fi
   ```

2. Create a `ConditionTest.sh` file by typing following command:

   ```sh
   nano ConditionTest.sh
   ```

3. Type the following script in the file:
    ![pic5](./img/HOP05_pic5.png)
   - Hit the `CTRL + x` key to quit and save the file.

4. Type the following command to execute the script:

   ```sh
   bash ConditionTest.sh
   ```

   > Then type in a number to test it.
   > Please run the program several times to try different numbers.

### Case condition execution

1. The basic syntax for `case`:

   ```sh
   case WORD in
   PATTERN) COMMANDS ;;
   PATTERN) COMMANDS ;; ## optional
   esac
   ```

2. Create a `CaseTest.sh` file by typing the following command:

   ```sh
   nano CaseTest.sh
   ```

3. Type the following script in the file:
   ![pic6](./img/HOP05_pic6.png)
   - Hit the `control + x` key to quit and save the file.

4. Type the following command to see the result

   ```sh
   bash CaseTest.sh 10
   bash CaseTest.sh string
   ```

### Looping

1. Type the following command to create a WhileTest.sh file:

   ```sh
   nano WhileTest.sh
   ```

2. Type the following script in the file:
    ![pic7](./img/HOP05_pic7.png)

   - Click the `control + x` key to quit and save

3. Type the following command to test the file.
   __*You can give a different number to the parameter*__.

   ```sh
   bash WhileTest.sh 10
   ```

4. An `Until` loop is the opposite of `while` loop, which will run the code as long as the condition fails.
   - Type the following command to create a `UntilTest.sh` file:

    ```sh
    nano UntilTest.sh
    ```

   - Click the `control + x` key to quit and save.

5. Type the following command to `test` the file:

   ```sh
   bash UntilTest.sh 5
   ```

6. Another common loop is `for` loop. Type the following command to create a `ForTest.sh` file:

   ```sh
   nano ForTest.sh
   ```

7. Type the following script in the file:
    ![pic8](./img/HOP05_pic8.png)
   - Click the `control + x` key to quit and save.

8. Type the following command to `test` the file:

   ```sh
    bash ForTest.sh
   ```

---

## Challenge

1. Take substitute variables for a random number and run the ConditionTest.sh again. Take a screenshot.

1. Change the condition in ForTest loop to output a different print statement that shows how many times the loop ran. Take a screenshot.

1. Submit your Work to Brightspace
   - Please upload all your files for this hands-on practice to the HOP assignment on Brightspace.
