## Flask 프레임 워크를 사용한다.


- session  
세션은 로그인하여 로그아웃하는 시간 간격이다.  
각 세션은 고유의 session id를 가지고 있다.  
또한 세션에 로그인 한 사용자의 정보가 들어있다.  

세션  
  - 정보 1  
  - 정보 2  
  - 정보 3  
 와 같이 dictionary object 로 되어있다.  
즉, 내가 필요한 정보들을 넣을 수 있다.  
`session[username] = 'hwan'`  

만약 내가 세션에 넣었던 정보들을 다 지우려면 어떻게 해야 할까???  
`session.pop('key',None)`  






- app.secret_key  

- request

- html 내 코드 삽입. (endif, endfor, ...) 

