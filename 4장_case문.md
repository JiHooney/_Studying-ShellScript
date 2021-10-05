# case문 사용

* 문법
```
case <variable> in
<pattern 1>)
<commands>
;;
<pattern 2>)
<other commands>
;;
esac

* 예시
#!/bin/bash

case $1 in
hello) echo "hello world";;
good) echo "good day";;
*) echo "invalid command";;
esac



 * 예시2
#!/bin/bash

echo "What is your preferred fruit?"
echo "1) apple"
echo "2) avocado"
echo "3) banana"
echo "4) melon"
echo "5) I do not know!"
read case;

case $case in
1) echo "apple";;
2) echo "avocado";;
3) echo "banana";;
4) echo "melon";;
5) exit;;
esac
```


## Function 만들기
```
#!/bin/bash

test_func() {
	echo "hello, world"
}

test_func


* 예제1
#!/bin/bash

val=5

function_foo() {
	local val=3
	echo "hello $1 $val"
}

foo 3
```

* 쉘스크립트 안에서 ()
```
()을 사용하면 터미널에서 명령어를 실행하는 것과 같다.

* 예제
#!/bin/bash

for i in $( ls );
do
	echo "item: $i"
done

```


* 예제2
```
exit 1은 실패했을 때

#!/bin/bash

if [ -z "$1" ]; then
	echo "usage: $0 directory"
	exit 1
fi
src_dir=$1
target_dir="./backup/"
of=home-$(data +%Y%m%d).tgz

tar -cvf $target_dir$of $src_dir
```


* 예제 3
```
#!/bin/bash

cd /dada &> /dev/null   #오류가 생기면 /dev/null로 보내라.
echo rv: $? 	#바로 윗 줄의 코드의 결과를 리턴, 성공이면 0 실패이면 1
cd $(pwd) &> /dev/null
echo rv: $?
```


* 예제 4 - counter값 증가시키기
```
counter=0
while [ $counter -lt 10 ]; 
do
	echo "The counter is $counter"
	let counter=counter+1
done
```


* 예제 5 -여러개의 문자열 입력받기
```
#!/bin/bash

backup_dirs=("/etc" "/home" "/boot")
dest_dir="/backup"
dest_server="server1"
backup_date=$(date +%b-%d-%y)

echo "Starting backup of: ${backup_dirs[@]}"

for i in "${backup_dirs[@]}";
do
	sudo tar -Pczf /tmp/$i-$backup_date.tar.gz $i
	if [ $? -eq 0 ]; then
		echo "$i backup succeeded"
	else
		echo "$i backup failed"
	fi
	#scp는 원격 서버에 이 파일을 보내고 copy한다는 명령어
	scp /tmp/$i-$backup_date.tar.gz $dest_server:$dest_dir
	if [ $? -eq 0 ]; then
		echo "$i transfer succeeded."
	else
		echo "$i transfer failed"
	fi
done

sudo rm /tmp/*.gz | echo "Beackup is done."
```

	