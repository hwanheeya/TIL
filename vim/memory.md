# 타이틀
## 흐흠
### 170528
- 외우면 좋은 것들
  + it        : Inside the tag
  + gU        : Make uppercase
  + gu        : Make lowercase
  + \<C-v\>   : Visual-block mode
  + V         : 비주얼-행 모드
  + aw        : A Word
  + gv        : 이전에 선택한 비주얼 모드의 영역을 다시 선택한다.
  + r         : Replace
  + c         : Change
  + y         : Yank into register
  + I         : 행의 처음으로 이동한 후 끼워넣기 모드
  + A         : 행의 끝으로 이동한 후 끼워넣기 모드
  + 끼워넣기 모드에서 \<C-w\> (이전 단어까지 역방향으로 지우기) \<C-u\> (행의 시작까지 역방향으로 지우기)를 사용할 수 있다.
  + G         : 파일 끝으로 이동
---

- 명령행 모드
    + 점 명령은 가장 마지막에 실행한 일반 모드 명령을 반복한다. 따라서 점 명령으로 명령행 모드의 명령을 반복할 수 없다.
   명령행 모드를 반복하기 위해서는 @:을 사용해라.
    + 대부분 범위를 지정할 수 있다.
        * :2          범위 : 2번째 행 
        * :2,5        범위 : 2~5번째 행
        * :.,5        범위 : 현재 커서가 있는 행 ~ 5번째 행
        * :.,$        범위 : 현재 커서가 있는 행 ~ 마지막 행
        * :%          범위 : 모든 행
        * :'<,'>      범위 : 비주얼 선택의 범위를 의미한다.
        * : /<html>/,/<\/html>/ 범위 : <html> 패턴과 일치하는 행 ~ </html> 패턴과 일치하는 행
        * : .,.+3     범위 : 현재 행 ~ 현재 행 + 3
    + p(rint)    행에서 지정한 범위를 간단하게 출력한다.
    + copy || co || t(copy To) 
        * :6t. 는 6번째 행을 t (복사) 하여 . 아래로 붙여넣기
        * 그렇다면 :t$는 현재 행을 복사하여 $(마지막 행) 아래로 붙여넣기가 된다.
        * (복사 대상)t(목적지) 가 된다.
    + m(move)
        * 동작 방식은 t와 유사하다.
    + normal = (범위)normal (일반 모드 명령) 
### 170529
