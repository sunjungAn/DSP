# 8. Virtual Memory

## Valid-Invalid BIt

---

- page table entry의 valid-invalid bit은
    - v ⇒ 메모리에 적재됨
    - i ⇒ 메모리에 없음
- 초기화 상태는 i로 초기화 된다.
- 프로세스가 메모리에 올라와 있지 않는 페이지를 접근하려고 하면?
    - 페이지 테이블 항목이 무효로 설정 되어 있으므로 **페이지 폴트 트랩 (page fault)이 발생**

![8%20Virtual%20Memory%20c5e2c301da6d46cf9ce085f44aaab3d8/Untitled.png](8%20Virtual%20Memory%20c5e2c301da6d46cf9ce085f44aaab3d8/Untitled.png)

## 페이지가 메인 메모리에 없을 때

---

![8%20Virtual%20Memory%20c5e2c301da6d46cf9ce085f44aaab3d8/Untitled%201.png](8%20Virtual%20Memory%20c5e2c301da6d46cf9ce085f44aaab3d8/Untitled%201.png)

## Page Fault

---

1. 페이지 참조가 있는지 확인
2. [page fault] operation system에 트랩을 발생시킴
3. 디스크에 페이지를 위치시킨다. 
4. 빈 프레임을 찾고, 디스크에 새로 할당된 프레임으로 해당 페이지를 읽어들이도록 요청한다. 
5. 디스크 읽기가 끝나면, 페이지가 메모리에 있다는 것을 알리기 위해 페이지 테이블을 갱신한다. 또한 validation vit를 v로 바꾼다. 
6. 트랩에 의해 중단되었던 명령어를 다시 수행한다. 

## Aspects of Demand Paging

---

- 극단적인 경우에는 메모리에 페이지가 하나도 안 올라와 있는 상태에서도 프로세스를 실행시킬 수 있다.
-