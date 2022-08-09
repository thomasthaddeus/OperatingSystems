# Hands-On Practice

```sh
nano ./CODE/ShowArgument.sh
```

```sh
bash ./CODE/ShowArguments.sh first second 'third argument'
```

```sh
bash ./CODE/ShowArguments.sh argument1 argument2 'I am argument 3'
bash ./CODE/ShowArguments.sh 'This is how to include "double quotes"'
bash ./CODE/ShowArguments.sh "This is how to include 'single quotes'"
```

```sh
bash ./CODE/ShowArguments.sh {first,second,third}
bash ./CODE/ShowArguments.sh {{1..5},{a..d}}
bash ./CODE/ShowArguments.sh {1..3}{a..b}
bash ./CODE/ShowArguments.sh {01..10..2}
bash ./CODE/ShowArguments.sh {A..G..2}
```

```sh
bash ./CODE/ShowArguments.sh ~
bash ./CODE/ShowArguments.sh ~root
```

```sh
name=Thaddeus
bash ./CODE/ShowArguments.sh "${name}"
```

```sh
bash ./CODE/ShowArguments.sh "$(( 1 + 2 ))" "$(( (1 + 2) * 2 ))"
```

```sh
echo "Today is $( date +%Y-%m-%d )" > file.md
cat file.md
```

```sh
names="Kevin Arthur Evan"
bash ./CODE/ShowArguments.sh $names
bash ./CODE/ShowArguments.sh "$names"
```

```sh
bash ./CODE/ShowArguments.sh Show*
bash ./CODE/ShowArguments.sh ?ile.md
bash ./CODE/ShowArguments.sh [a-f]ile*
```

```sh
bash ./CODE/ShowArguments.sh <(ls -l) >(pr -Tn)
```

```sh
nano ./CODE/OptionTest.sh
```

```sh
bash ./CODE/OptionTest.sh -a
bash ./CODE/OptionTest.sh -v
bash ./CODE/OptionTest.sh -c
bash ./CODE/OptionTest.sh -b
```
