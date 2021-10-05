# if문 사용
```
if [ <some test1> ]; then
	<commands 1>
elif [ <some test2> ]; then
	<commands2>
else
	<commands 3>
fi


* if문에 사용되는 조건문 종류
[ -z ] : 문자열의 길이가 0 이면 참
[ -n ] : 문자열의 길이가 0이 아니면 참

[ -eq ] : 값이 같으면 참
[ -ne ] : 값이 다르면 참
[ -gt ] : 값1 > 값2면 참
[ -ge ] : 값1 >= 값2 참
[ -lt ] : 값1 < 값2
[ -le ] : 값1 <= 값2

[ -a ] : &&연산과 동일, and 연산
[ -o ] : || 연산과 동일, xor 연산

[ -d file ] : 파일이 디렉토리면 참
[ -e file ] : 파일이 있으면 참
[ -L file ] : 파일이 심볼릭 링크면 참
[ -r file ] : 파일이 읽기 가능하면 참
[ -s file ] : 파일의 크기가 0보다 크면 참
[ -w file ] : 파일이 쓰기 가능하면 참
[ -x file ] : 파일이 실행 가능하면 참

[ ! 값 ] : not
[ 값1 && 값2 ] : and
[ 값1 || 값2 ] : or

```

* 예시
```
#!/bin/bash

val="foo"

if [ $val == "dog" ]; then
	echo "I love dog"
elif [ $val == "cat" ]; then
	echo "My cute cat"
else
	echo "I have no pet"
fi
```

* 예시 - 입력문자열 비교하기
```
#!/bin/bash

n=10

if [ $n -lt 10 ]; then
	echo "one digit number"
else
	echo "two digit number"
fi
```

* 예제 1
```
#!/bin/bash

val=$1

if [ -z $val ]; then
	echo "null string"
elif [ $val == "dog" || $val == "cat" ]; then
	echo "I have a pet"
else 
	echo "I have no pet"
fi
```


* 실습 - 3개의 수 입력받고 가장 큰 값 출력하기
3개의 수를 입력 받은 후 가장 큰 수 출력하기
if 구문의 -ge조건식과 &&연산 등을 활요할 것
```
#!/bin/bash

read -p "Enter the first number: " val1
read -p "Enter the second number: " val2
read -p "Enter the third number: " val3

if [[ $val1 -ge $val2 && $val1 -ge $val3 ]]; then
	echo "max: $val1"
elif [[ $val2 -ge $val1 && $val2 -ge $val3 ]]; then
	echo "max: $val2"
else 
	echo "max: $val3"
fi
```

