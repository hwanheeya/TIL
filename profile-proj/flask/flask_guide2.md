## url_for():  
- url_for()는 첫번째 인자로 함수의 이름과 그 이후의 인자로는 변수 부분에 대한 다수의 키워드를 받는다.   
- 인자로 함수명과 키워드를 올바르게 입력한다면, 해당 url 주소를 얻을 수 있을 것이다.  

## http methods  
- @app.route('/login', methods=['GET', 'POST'])  
- 와 같이 방법을 정의할 수 있다.  

## template  
- 파이썬 소스코드에서 html 만들고 싶지 않을 것이다.  
- 동적으로 변환되는 값의 경우 보안 상 html 이스케이핑을 해야 하는데 귀찮다.  
- 따라서 템플릿을 활용하도록 하자.  
- Flask는 templates 디렉토리에서 템플릿 파일을 찾는다.  

``` python  
from flask import render_template

@app.route('/hello/')
@app.route('/hello/<name>')
def hello(name=None):
    return render_template('hello.html', name=name)  
```  
와 같이 작성하고, templates 디렉토리에 hello.html을 추가한 후 실행해보도록 하자.  
위 예제와 같은 경우는 render_template의 두번째 인자로 name이 전달된다.  
hello.html 에서 해당 name을 사용하려면 어떻게 해야 하는가?  
{% %} 구문 안에서 변수처럼 사용하면 된다.  
구문 밖에서는 {{name}} 처럼 사용하면 된다.  



