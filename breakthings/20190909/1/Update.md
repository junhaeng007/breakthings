<style>
  #Rcolor{ color:red;}
  #Gcolor{ color:green;} #YGcolor { color:yellowgreen; }
  #Bcolor{ color:blue;}
</style>

#### 변경
1. **20190904_2에 있었던 문제점 수정**
    - <class id="Bcolor">OnTriggerStay2D()</class> 함수 자체에 문제가 있다.
        - <class id="Bcolor">Update()</class>처럼 매 프레임마다 호출되는 함수다 → **성능 저하에 큰 요인이 된다.**
        - 완벽하게 매번 호출되지는 않는다.
    - 따라서 <class id="Bcolor">OnTriggerStay2D()</class>를 제거하고    <class id="YGcolor">StiffenByKiBlast()</class> 코루틴 함수를 부활
    - <class id="Bcolor">OnTriggerStay2D()</class>에 있던 일부 내부 코드를 새로운 코루틴 함수인 <class id="YGcolor">GuardFromKiBlast()</class>내부로 이동

2. **플레이어 UI 변경**
    - 가드게이지 위치 변경 : 스킬버튼 아래 → 마나게이지 아래
