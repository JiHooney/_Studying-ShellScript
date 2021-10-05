# for문 사용

* 문법1
```
for (( exp1; exp2; exp3 ))
do
	command1
	command2
	command3
done


* 예시 
for (( c=1; c<=5; c++ )) 
do
	echo "value $c"
done

```

* 문법2
범위에는 배열이나 리스트 등이 온다.
```
for 변수 in [범위];
do
	command1
done

* 예시1
for val in {1, 2, 3, 4, 5}
do
	echo ${val}
done

* 예시2
for val in $(sep 1 5);
do
	echo ${val}
done


for val in 1 2 3
do 
	echo ${val}
done


> ./my3.sh aa bb cc
for var in $@;
do
	echo $val
done


```


* 실습 - 현재 디렉터리에 있는 모든 파일 라인수 구하고 파일로 저장하기
```
> vi ex2.sh

#!/bin/bash
exec 2> /dev/null

count=0
for file in $@
do
	if [ -f $file ]; then
		wc -l $file >> result.txt
		let count=count+1
	elif [ -d $file ]; then
		for subfile in $file/*
		do
			wc -l $subfile >> result2.txt
			let count=count+1
			
		done
	fi
done

echo "Total count: $count" >> result.txt


혹은 아래와 같이 바꿀 수 있다.
for file in $@
do
	if [ -f $file ]; then
		wc -l $file >> result.txt
		let count=count+1
	elif [ -d $file ]; then
		for subfile in $file/*
		do
			wc -l $subfile >> result2.txt
			let count=count+1
			
		done
	fi
done >> result.txt


혹은 아래와 같이 작성하면 사용자에게 입력받는것이 아니라
input.txt에서 입력값을 가져오라는 뜻이다.
for file in $@
do
	if [ -f $file ]; then
		wc -l $file >> result.txt
		let count=count+1
	elif [ -d $file ]; then
		for subfile in $file/*
		do
			wc -l $subfile >> result2.txt
			let count=count+1
			
		done
	fi
done < input.txt >> result.txt

> bash ex2.sh *

* 참고
-exec 명령어
이때 exec를 이용해서 오류출력을 화면에 보이지 않도록 하고 다른데로 보내준다.
즉, exec 명령어 밑에서 생기는 오류들은 이제 화면에 출력되지 않는다. 
오류는 /dev/null로 보내진다.
0 : 표준입력
1 : 표준출력
2 : 표준에러출력

->> 명령어
>>는 기존 파일에 덮어씌어준다.
```