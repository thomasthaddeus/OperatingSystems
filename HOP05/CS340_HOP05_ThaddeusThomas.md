# HOP05 BASH - Looping and Branching

## Test command

1. Result

    ```sh
    test 1 -eq 1
    echo $?
    ```

2. Result

    ```sh
    [ 1 -lt -2 ]
    echo $?
    ```

3. Result

    ```sh
    [[ abc =~ ^a.*c$ ]]
    echo $?
    ```

4. Result

    ```sh
    (( 2 - 1 ))
    echo $?
    ```

5. Result

    ```sh
    (( 1 - 1 ))
    echo $?
    ```




## Conditional Expression

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

## Condition Test.sh

```sh
#! /bin/bash
printf "How many pizzas do you want to buy?\n"
read amount.to

if (( amount <=  0 ))
then
    printf "Please enter a number that is greater than 0.\n"
elif (( amount > 10 ))
then 
    printf "Sorry, we do not have that many pizzas.\n"
    exit 1
else
    printf "There you go. Here are %d pizzas for you.\n" "$amount"
fi
```

## CaseTest.sh

```sh
#! /bin/bash
case $1 in
    *[!0-9]*) message="non-numeric character(s).";;
    *) message="a number.";;
esac

printf "You entered %s\n" "$message"
```

## WhileTest.sh

```sh
#! /bin/bash
n=1;
while [ $n -le $1 ]
do
  printf "The loop has already run %d times. \n" "$n"
  n=$(( $n + 1 ))
done
```

## UntilTest.sh

```sh
#! /bin/bash
n=1;
until [ $n -gt $1 ]
do
  printf "The loop has already run %d times.\n" "$n"
  n=$(( $n + 1 ))
done
```

## ForTest.sh

```sh
#! /bin/bash
# loop in different strings
for name in Kevin Arthur Evan
do
  printf "%s\n" "$name"
done

# loop in numbers (C likes syntax)
for (( i=0; i<= 10; i++ ))
do
  printf "The loop runs %d times.\n" "$i"
done
```


