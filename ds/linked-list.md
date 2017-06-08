# Linked List

1. 사이즈가 자유자재로 늘어나는 자료 저장소
2. 노드들의 집합
    * 노드는 데이터와 다른 노드로 가는 link를 가지고 있다.

노드를 정의하자면 아래와 같다.  
```
typedef struct node {
  int val;
  struct node *next;
} node_t;
```
링크드 리스트는 노드들의 집합인데, 이 노드들 중에서 대장 한명을 뽑을 것이다.
대장을 보통 head라고 일컫는다.
```
node_t *head = NULL;
head = malloc(sizeof(node_t));
if (head == NULL) {
  return 1;
}
head->val = 1;
head->next = NULL;
```
todo 1.  
노드 생성 코드를 함수로 만들어 보자. (create)  

todo 2.  
잘 만들었는 지 확인하기 위해 노드를 출력하는 함수를 만들어보자. (print)

todo 3.
노드들의 집합이기 때문에 기준 노드(head)에 다른 노드를 추가하고 싶다.  
노드 집합의 가장 끝에 노드를 추가하자(insert)

todo 4.





