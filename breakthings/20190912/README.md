### 변경
1. **플레이어 UI 변경**
    - 분리되어 있었던 초상화, 체력게이지, 마나게이지 틀을 새로 제작한 가드게이지 틀과 함께 하나로 합체 ![portarit_and_gauage](https://junhaeng007.github.io/unity-practice/breakthings/20190912/portrait_and_gauage.png)
    - 가드게이지와 오공의 텔레포트 쿨타임을 동시에 공유하던 avoidanceGauage를 guardGauage와 avoidanceGauage로 분리
    - avoidanceGauage를 스킬 버튼 지점으로 이동

### 추가
1. **가드게이지(기력) 시스템 추가**
    - 더 이상 긴급회피 쿨타임(오공의 텔레포트 등)과 공유하지 않음
    - *최대 기력*, (평상 시)*리젠 기력*, (가드 시)*소모 기력*, (리젠)*딜레이 기력*, (가드하기 위한)*최소 기력* 이 수치적으로 존재
    - 더 이상 에네르기파 계열 스킬에 맞는 도중에 가드를 칠 수 없음 → 맞기 직전에 가드를 하고 있어야 가드 가능
