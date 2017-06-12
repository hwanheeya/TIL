``` shell
SyntaxError: Non-ASCII character '\xec' in file D:\app\views.py on line 41, but no encoding declared; see http://python.org/dev/peps/pep-0263/ for details
```  

[해결 방법]  
파이썬 코드 맨 위에 한글 인코딩을 하도록 문장 하나를 추가하면 됩니다.  
`# -*- coding: utf-8 -*- `  

끝.
