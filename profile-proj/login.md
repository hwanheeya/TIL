## Flask 프레임 워크를 사용한다...

- session  
세션은 로그인하여 로그아웃하는 시간 간격이다.  
각 세션은 고유의 session id를 가지고 있다.  
또한 세션에 로그인 한 사용자의 정보가 들어있다.  

세션은 dictionary object 로 되어있다.  
즉, 내가 필요한 정보들을 넣을 수 있다.  
`session[username] = 'hwan'`  
  
만약 내가 세션에 넣었던 정보들을 다 지우려면 어떻게 해야 할까???  
`session.pop('key',None)`  



- app.secret_key  
`If app.secret_key is not set, the Flask framework will not allow you to set or access the session dictionary.`  
(출처: https://stackoverflow.com/questions/22463939/demystify-flask-app-secret-key)  

---  


위 내용을 기반으로 해서, 로그인 페이지를 만들어 보도록 하자.  

index.html : 시작 화면  
 - login : 로그인 요청  
 - login_form : 로그인 양식 입력  
 - logout : 로그아웃 요청 -> 완료 시 index.html로 redirect
 
- login  
로그인 시 해야 하는 일은 무엇이 있을까?  
우선 세션을 추가해야 한다.  
세션을 추가한 후에 로그인한 사용자에 대한 기본 정보를 세션에 추가한다.  
예를 들면 username?  
``` python
session[username] = 'hwan'  
```  

 
