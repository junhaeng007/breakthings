#### 변경
1. **20190904_2에 있었던 문제점 수정**
    - OnTriggerStay2D()함수 자체에 문제가 있다.
        - Update()처럼 매 프레임마다 호출되는 함수다 → **성능 저하에 큰 요인이 된다.**
        - 완벽하게 매번 호출되지는 않는다.
    - 따라서 OnTriggerStay2D()를 제거하고 StiffenByKiBlast()코루틴 함수를 부활
    - OnTriggerStay2D()에 있던 일부 내부 코드를 새로운 코루틴 함수인 GuardFromKiBlast()내부로 이동

2. **플레이어 UI 변경**
    - 가드게이지 위치 변경 : 스킬버튼 아래 → 마나게이지 아래
