### 수정

1. **원기옥 캔슬 문제점 보완**
    - 애니메이션에 의해 스프라이트가 바뀌더라도 애니메이션이 종료되면
    바뀌기 전의 원래 스프라이트로 되돌아간다
    - 보스의 공격에 의해 캔슬당했을 때 직전의 스프라이트가 남아있게 된다
    - 따라서 캔슬 혹은 폭발 등으로 오브젝트가 종료됐을 때 `spriteRenderer.sprite = null`를 넣었음

### 변경

1. **원기옥 폭발 원인 변경**
    - **원기옥 폭발 대상 추가**
        - 빨간 벽, 보스 → 바깥 투명벽, 보스(+빨간 벽)
        - 원기옥을 사용범위가 너무 좁아 확장시킴
    - **원기옥 보스 적중 이후 폭발까지의 시간 변경**
        - 2s → 4s ~ 5s (4.5s ± 0.5s)
        - (+빨간 벽일 때) 즉발 → 1s ~ 2s (1.5s ± 0.5s)
        - ※ 이 수치들은 이후 계속 변경될 수 있음

2. **앞으로 넉백 속도는 스킬마다 달리 정할 수 있음**


-------------------------------------------------------------------------------------

### Fix

1. **Fix issue that be canceled Genkidama**
    - Even if sprite is changed because of animation, it is returned first sprite before changed when animation is finished
    - Sprite when be canceled by Boss' Attack stays just before

### Change

1. **Change the Genkidama explosion target**
    - Red wall & Boss → Invisible outside wall & Boss
    - Expand usable range because it was too narrow
