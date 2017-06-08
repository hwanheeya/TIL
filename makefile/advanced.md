이 글을 보기전에 intro.md를 숙지해야 해.  
## Advanced  

intro.md에서 크게 다루지 않은 것이라고 한다면 Macro가 있겠지.  
Macro를 쓰는 이유는  
1. 변경 용이  
2. 단순함  

makefile의 가장 큰 목적은 효율적으로 실행파일(target)을 만들기 위함이니까  
target에 대해서 Macro를 적용해보자. 또한, target을 만들기 위해 사용한 컴파일러도 필요하다.  

TARGET = exe  
CC = gcc  
그리고 매크로를 사용할 때는 $(TARGET)과 같이 사용하면 된다.  

example)   
```
$(TARGET) : $(OBJS)  
  $(CC) -o $(TARGET) $(OBJS)  
$(OBJS) : a1.c  
  $(CC) -c a1.c
```  

## BONUS SKILL

1. $@ : 현재 타겟의 이름
2. $^ : 현재 종속 리스트
