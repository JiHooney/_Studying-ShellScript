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

[ -d ] : 파일이 디렉토리면 참
[ -e ] : 파일이 있으면 참
[ -L ] : 파일이 심볼릭 링크면 참
[ -r ] : 파일이 읽기 가능하면 참
[ -s ] : 파일의 크기가 0보다 크면 참
[ -w ] : 파일이 쓰기 가능하면 참
[ -x ] : 파일이 실행 가능하면 참
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
