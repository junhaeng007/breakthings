### 변경

1. **코드 최적화**
    - Obstacle.cs
    - Special_Obstalce.cs
    - Item.cs
    - Stage_BasicMgr.cs
    - Wall.cs

### 추가

1. **플레이어의 모든 스킬에 보스 타격 시스템 추가**
    - 에네르기파, 기합폭발
    - 계왕권은 별다른 타격은 없음. 그리고 계왕권쉴드가 장애물은 막아줘도(지속시간을 희생하고) 보스의 공격까지 막아주지는 않음

2. **손오공의 궁극기, 원기옥 추가**
    - 스크립트, 스프라이트, UI등등 손오공의 궁극기인 원기옥이 추가됨
    - 에네르기파처럼 보스에게 데미지를 프레임단위로 빠르게 주면서 **스턴과 넉백을 동시에**
    - 원작처럼 ***선딜레이는 매우 길지만 (적중 시) 가장 강력함***
    - <font color="grey">~~기본 스킬들(Q, W, E)과 다르게 쿨타임 대신 <b>스택</b>을 쌓아야 사용 가능~~</font> 미구현

### 문제점

1. **원기옥 캔슬당한 그 이후**
    - 던지기 전에 보스에게 데미지를 받아 캔슬당하고 다시 시도해서 원기옥이 폭발하면 평소와 달리 원기옥 구체가 그대로 남아있다.
    - 폭발이 사라지고 오브젝트가 비활성화가 되어서야 사라진다.

### 업데이트가 늦은 <font color="grey">~~변명~~</font>이유

1. <b>원기옥의 폭발 이펙트</b>는 지금까지 쓰던 스프라이트(2D픽셀아트)가 아닌 <b>파티클 시스템</b>을 사용했는데 처음 써보는 거라 유튜브보면서 공부하느라 시간이 좀 걸림

2. **와우했다(...)** 20일동안 하다가 뒤늦게 정신차림

---------------------------------------------------------------------

### Change

1. **Script Optimization**
    - Obstacle.cs
    - Special_Obstalce.cs
    - Item.cs
    - Stage_BasicMgr.cs
    - Wall.cs

### Addition

1. **Add a Hitting(Doing Damage) System for Boss by All Player's Skills**
    - Kamehameha, Spirit Explosion
    - Kaioken doesn't have hitting system. And Kaioken Shield keeps out Obstacle(consume Mode time) but not Boss's attack

2. **Add the Ultimate Skill of Goku, Genkidama**
    - Script, Sprite, User Interface, etc
    - Genkidama hits rapidly the Boss like Kamehameha, it has also **Stun and KnockBack**
    - ***It is the most Powerful but very long Cast Time*** as an Original Story(Dragonball Z)
    - <font color="grey">~~Player needs to have many stacks for using Genkidama not Cooldown~~</font> not yet

### Issue

1. **Be Canceled Genkidama by Boss' Attack**
    - If Genkidama explodes after be canceled, Genkidama sphere is still alive until inactivate Genkidama Object

### A Belate Reasons(excuses)

1. I learned **Particle System** for exploding Genkidama because it is first time

2. I played **World of Warcraft** for 20 days(...) But I swear no more
