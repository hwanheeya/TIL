## Flask Framework

### Sample code  

``` python
(a) from flask import Flask 
(b) app = Flask(__name__)

(c) @app.route('/')
(d) def hello_world():
    return 'Hello World!'

(e) if __name__ == '__main__':
       app.run()
```  
- (a)  
모듈을 불러오는 방법은 크게 2가지가 있다.  
  1. import Module  
  2. From Module import '변수나 함수'  

#### 둘의 차이는 무엇일까?  
1의 경우는 모듈 내의 함수나 변수를 사용하기 위해서는 접근자로 모듈 이름을 써줘야 한다.  
반면 2의 경우는 함수 및 변수 이름만 사용해도 된다.  
1의 경우는 귀찮지만, 변수 및 함수 사용에 있어서 보다 안전한 사용 방법이 된다.  
예를 들어, import한 모듈이 사용하는 변수와 내가 임의로 만든 변수가 겹치는 경우 의도하지 않은 동작이 발생할 수 있기 때문이다.  


- (b), (e)  
`app = Flask(__name__)`  
app이라는 변수에 Flask 객체를 넣은 것 같이 보인다.  
그런데 저기 저 괴상하게 생긴 __name__은 무엇인가?  
또한, (e)에서 볼 수 있는 __main__은 또 무엇인가?  

__name__은 현재 모듈의 이름을 담고있는 내장 변수이다.  
abc.py 내에서 app = Flask(__name__)을 선언하면, __name__ 자리에 abc가 들어간다.  

__main__을 이해하기 위해서는 c의 main 함수를 생각해보면 좋다.  
c의 경우는 main 함수가 자동으로 실행된다.  
하지만 python의 경우 자동으로 실행되는 main 함수가 없고, 대신 들여쓰지 않은 코드들이 모두 수행된다.  

예를 들어, script.py 파일이 있다고 가장하자.  
다른 파일에서 script.py를 임포트하여 사용하는 경우가 있을 수 있고  
python script.py와 같이 모듈이 직접 수행되는 경우가 있다.  

전자의 경우 __name__ -> script가 되고  
후자의 경우 __name__ -> main이 된다.  

---  






