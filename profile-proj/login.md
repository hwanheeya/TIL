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

- login_form  
사용자가 입력한 계정 및 비밀번호가 정확한지 확인해야 한다. (유효성 검사)  
계정 및 비밀번호를 입력하는 칸이 필요하다.  

그런데?  
- login_form에서 전달하는 username과 password는 어떻게 받지?
- flask.request.form에 해당 정보가 들어있다.  
- 그런데 어느 순간부터 동작이 잘 되지 않는다. 콘솔에 로그를 찍어 볼 필요가 있는 것 같다.  

### How to debug?  
- app.logger를 참고해라.
> app.logger.debug()  

### Method Not Allowed  
이 문제는 왜 생기는 지 몰랐다.  
http 요청의 method를 의미하는 것 같다.  
@app.route('/login_form',methods=['POST']) 하니까 문제가 해결됨.
> form 태그에서 post 방식으로 요청을 한다.  
> 그러나 @app.route('/login') 과 같이 methods를 지정하지 않을 경우는, 기본 값은 'GET' 이다.  
> 때문에 위와 같은 문제가 생겼던 것이고, @app.route에서 methods를 지정해둔 경우에는 문제가 생기지 않을 것이다.  

  


요약하자면, 사용자 정보가 유효한 경우 username, isLogin 정도의 정보는 세션 정보에 추가한다.  
만약 로그아웃 하면 해당 세션 정보를 지운다. (session.pop)  
이를 활용해서 로그인 및 로그아웃 기본 구조를 만든다.  

로그인 유무에 따라 (세션에 저장된 정보를 참고하여) index.html을 다르게 표현할 것이다.  
로그인 된 사용자는 welcome 'username' 및 로그아웃 할 수 있는 화면을, 로그인을 하지 않은 사용자는 login_form.html로 이동할 수 있는 경로를 제공할 것이다.  

이 때, templates 디렉토리 내에 있는 html 파일에 파이썬 코드를 추가 할 수 있다.  
{{ variable}} or {% statement %}  
``` python
{% if session['logFlag'] == True: %}
<form method="POST" action="/logout">
    <input type="submit" value="log out"
</form>

{% else: %}

<form method="POST" action="/login_form">
    <input type="submit" value="login">
</form>
```  
파이썬 문법대로 했지만 낭패를 봤다.  
어디가 문제일까?  
[template-tag](https://docs.djangoproject.com/en/1.11/ref/templates/builtins/#ref-templates-builtins-tags) 를 참고하도록 하자.  
  
여기까지 잘 따라왔다면 한번 더 시행착오가 필요함을 직감할 수 있다.  
app.secret_key ...   
본인이 session을 사용한다면 secret_key를 무조건 설정해줘야 한다.  
관련해서는 이후에 다시 공부하는 것으로 남겨둔다. (물론 까먹겠지만...)  

{% if val is True%} => no test named True 와 같은 에러가 생긴다.  
https://github.com/pallets/jinja/issues/520

---  









 
