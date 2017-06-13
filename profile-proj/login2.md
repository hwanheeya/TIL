## 진행 상황

- 구성 요소
    * login_form.html
    * index.html 
    * main.py  

### Drop-down menu  

index.html은 페이지의 기본 화면 정도로만 사용하고, 운영 업무를 하기 위한 페이지를 별도로 만든다. (admin_index.html) 
admin_index.html에는  
- logout 버튼이 있어야 한다. (logout시 index.html로 redirect) . 
- dropdown menu를 볼 수 있어야 한다. (메뉴 목록은 기존 화면을 참고한다.)  
- 만일 로그인 되지 않은 사용자가 강제로 admin_index.html로 들어가려고 시도할 수 있으므로 해결 방안을 마련해야 할 것이다.  

### What to do?  

1. javascript을 html 내에서 선언해야 할 것이다. (select - option tag)
> https://stackoverflow.com/questions/13739568/how-do-i-link-a-javascript-file-to-a-html-file . 

2. 메뉴를 선택하고 이동하기를 누르면 해당 페이지로 이동한다. form tag 활용하기.  
3. 이전 코드에서 javascript function 내에 id로 접근하는 경우와 name으로 접근하는 경우가 있다.  
> https://stackoverflow.com/questions/3936249/javascript-name-vs-id  

 
---  
위 내용대로만 잘 따라왔다면, 기본적인 틀은 만들 수 있다.  
대망의 앱엔진... 프로젝트 생성 시 앱엔진으로 만들지 않은 경우에는 어떻게 해야 할까??? 


### 앱엔진 시작하기  
- 만약 프로젝트를 생성할 때 앱엔진으로 시작하지 않은 경우는 어떻게 해야 할까?  
    1. Preference -> Languages & Frameworks -> Schemas and DTDs -> Google App Engine 로 이동. 
    2. Enable support 
    3. Set SDK directory (~~~ /google-cloud-sdk/platform/google_appengine) . 
    4. Tools -> App Engine 확인. (시험 삼아 upload appengine 시도)  
    5. 안됨...

### 앱엔진 시작하기 2.  
- 위 과정은 왜 안됬을까???  
- 앱엔진 프로젝트는 기본적으로 앱엔진 설정 파일이 있다. 그런데 현재는 기존 프로젝트에 앱엔진 기능을 추가한 터라 
있어야 하는 데이터가 없다. 직접 만들어 줄 필요가 있다. 그것은 [app.yaml](https://cloud.google.com/appengine/docs/standard/python/config/appref)이다.  

또한 앱엔진 프로젝트를 만들때 기본적으로 생기는 main.py도 있다. 아래 코드를 참고하자.  

<app.yaml>  
```
application: ~~~~
version: 1
runtime: python27
api_version: 1
threadsafe: yes

handlers:
- url: /favicon\.ico
  static_files: favicon.ico
  upload: favicon\.ico

- url: .*
  script: main.app

libraries:
- name: webapp2
  version: "2.5.2"

```  

<main.py>  
```
import webapp2

class MainHandler(webapp2.RequestHandler):
    def get(self):
        self.response.write('Hello world!')

app = webapp2.WSGIApplication([
    ('/', MainHandler)
], debug=True)
```  
해당 내용을 추가하더라도, deploy가 되지 않는다.  물론 프로젝트를 만들 때 앱엔진 with flask로 만들면 된다.  
하지만 이 넘치는 궁금증을 해결하지 못하면 난 아무리 먹어도 배고플지도 모른다.  
잠깐 살펴봤는데 일단 배고프기로 하고 프로젝트를 다시 만들자.












