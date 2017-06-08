
## what is make?  
make 는 파일 관리 유틸리티다.  
파일 관리를 위한 명세서 같은 녀석이 makefile이다.  

## why make?  
make를 안써도 컴파일은 가능하다.  
다만, make를 쓰면 삶이 보다 풍요로워진다.  
1. 시간 절약  
2. 관리 용이  
비교를 위해, 쓰기 전과 후를 확인해보자.  

그 전에 알아두어야 할 gcc compile option이 있다.  
`gcc -c -o test.o test.c`  
-c는 object file을 만들어준다. (어셈블까지만 수행하고, 링크는 수행하지 않는다.)    
-o는 생성될 실행 파일의 이름을 지정해준다. (-o 다음에는 실행 파일 이름이 와야 한다.)  

예를 들어, 컴파일해야 할 c 파일이 1000개가 있다고 가정하자.  
gcc -c a1.c, gcc -c a2.c, ..., gcc -c a1000.c  
gcc -o exe a1.o a2.o ... a1000.o  
./exe  
exe 실행파일을 만들기 위해 엄청나게 험난한 여정을 떠나야만 한다.  

머리를 쓰자.  
makefile은 실행파일을 만드는 데 드는 시간을 줄여주는 대신 인터넷 쇼핑할 시간을 벌어준다.  
위 예제에 makefile을 당장 적용해보자.  

## makefile structure  
1. Target  
2. Dependency  
3. Command  
4. Macro  

CC = gcc  
target1 : dependency1  
(tab)command1  
(tab)command2  

위 코드는 makefile의 일부를 가져온 것이다.  
[해석]  
CC = gcc  
> CC는 gcc로 치환된다.    
> target1 : dependency1  
> (tab)command1  
> target1을 만들기 위해 우선적으로 dependency1이 필요하다.  
> target1을 만들기 위해 command1를 실행한다.
> (위 내용에 따르면 dependency1이 있을 때 command1을 수행할 수 있겠지?)  
  
즉, target1을 만들기 위해 `dependency1`을 만들어야 하니까  
dependency1이 `target`인 문장을 하나 더 만들어야겠지?  

dependency1 : ~~
  gcc -c ~~  
요런 식으로 말이야.  


위 내용을 잘 기억해두면, make clean 등 멋진 녀석들을 만들어 낼 수 있을거야.  
그럼 이만.  


---
[참고 링크]  
http://bowbowbow.tistory.com/12
