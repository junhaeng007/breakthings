## Breakthings

### 보류된 문제점

1. **노말 베지터의 와일드 헌터 3단계, 슬렛지해머**
    - 베지터의 돌격기 중 하나인 와일드 헌트의 3번째 단계인 <b>슬렛지해머</b>에서 플레이어 뒤로 고속이동할 때 빨간 벽(가칭)밖으로 이동해서 맵 밖으로 아웃되는 경우가 있다

2. **손오공의 계왕권 + 순간이동**
    - 플레이어 손오공의 계왕권 모드가 끝나기 직전에 순간이동(회피기)를 사용하면 빠르게 이동할 타이밍에 속도가 노말상태의 노말이속과 같아짐(∵순간이동 이동속도에 결함 발생)

3. **원기옥 캔슬당한 그 이후**
    - 던지기 전에 보스에게 데미지를 받아 캔슬당하고 다시 시도해서 원기옥이 폭발하면 평소와 달리 원기옥 구체가 그대로 남아있다
    - 폭발이 사라지고 오브젝트가 비활성화가 되어서야 사라진다

### 수정

1.

2.

3. **원기옥 캔슬 문제점 보완**
    - 애니메이션에 의해 스프라이트가 바뀌더라도 애니메이션이 종료되면
    바뀌기 전의 원래 스프라이트로 되돌아간다
    - 보스의 공격에 의해 캔슬당했을 때 직전의 스프라이트가 남아있게 된다
    - 따라서 캔슬 혹은 폭발 등으로 오브젝트가 종료됐을 때 `spriteRenderer.sprite = null`를 넣었음

---------------------------------------------------------------------------

### Issue

1. **Wild Hunt 3rd of Normal Vegeta, SlegeHammer**
    - He sometimes goes out the map after SlegeHammer's Blink

2. **Kaioken and Teleport of Goku**
    - Issue comes for use Teleport shortly before over Kaioken Mode

3. **Be Canceled Genkidama by Boss' Attack**
    - If Genkidama explodes after be canceled, Genkidama sphere is still alive until inactivate Genkidama Object


### Fix

1.

2.   

3. **Fix issue that be canceled Genkidama**
    - Even if sprite is changed because of animation, it is returned first sprite before changed when animation is finished
    - Sprite when be canceled by Boss' Attack stays just before
