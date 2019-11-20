# Battle Stadium

### Concept

- 모티브 : Battle Stadium D.O.N(2006) - PS2, 게임큐브
- 2 ~ 4인용 난투형 액션 게임
- 만화 캐릭터들 간의 난투
- 스프라이트 출처 - 점프 얼티밋 스타즈(2006) - NDS

### Player Command
※[D]: Derive, [P]: Push

||Goku|Vegeta
:--:|:--:|:--:
A|Hook|  
A+A|   |  
↑+A|Somersalut Kick
↓+A|  
␣+A|Somersalut Kick  
␣ +↑+A|  
␣ +↓+A|SledgeHammer

||Goku|Vegeta
:--:|:--:|:--:
S|Straight|  
S+S|Combo Punch|
↑+S|[D]Somersalut Kick|   |
↓+S|[P]RoundHouse Kick|   |   |
␣+S|[D]Somersalut Kick|   |   |
␣+↑+S|   |   |   |
␣+↓+S|RoundHouse Kick|   |   |
### Development Log

#### 2019
- 11/13 [프로젝트](https://drive.google.com/open?id=1mNYOsG-oiTiDN1jlWLgxqvSDHREb4fCW)
  - 기본적인 플레이어 컨트롤은 거의 완성되었다
  - 이동, 점프, 매달리기, 매달리기-점프, 매달리기-내려오기, 웅크리기
  - ! 유니티 툴에서 적은 String 데이터가 변수에 들어가기 전(String characterName)에 Awake가 먼저 실행된다.
  - **<font color="red">ISSUE</font>**
      - **제자리** 점프 → 매달기 → 점프(놓기) → 주어진 힘만큼 스핀(내려가기)
      - **앞으로** 점프 → 매달기 → 점프(놓기) → **비정상적으로 큰 힘만큼** 스핀(내려가기)
      - ▶ 단순 스크립트 상의 문제가 아닌 엔진의 문제라서 쉽게 해결할 수가 없다...
      - ▶ 따라서 일단 보류
- 11/16 [프로젝트](https://drive.google.com/open?id=121AD0WfpChXsnJZQ3zwE8UYEeibmEJJ1)
  - 손오공의 입력 A와 관련된 공격버튼이 완성되었다
  - A, A + A, Space + A, Space + ↓ + A
  - 베지터 역시 같이 추가할려고 했지만 둘이 동시에 하기에는 힘드므로 손오공 최종완성 이후 재개할 예정
  - **<font color="blue">ISSUE Complete</font>**
    지속적인 이슈 확인 결과, Move()내부에서 매달려있을 때는 transform.Translate()를 호출하지는 않지만 moveDir조차 업데이트가 되지 않아 힘이 그대로 남아있었기에 매달리기가 종료될 때 moveDir이 초기화되지 않고 다시 transform.Translate()가 호출되므로 moveDir = <font color="#33ccff">Vector2</font>.zero를 추가함.
    ~~스크립트 상의 문제였던걸로....~~
  - 아직 매달리기 관련 스크립트가 많이 불안정하다. 중간에 충돌체 트리거가 안꺼진다든가, 잘 매달리지 못한다든가, SpaceBar를 꾹 누르고 있어야 (점프 공격 중에 매달릴지 그냥 떨어질지에 대한 선택권) 매달리는 기능도 미구현 등등

- 11/20 [프로젝트](https://drive.google.com/open?id=1mL0Dl_4AVkhR_aVmOBeBrS5_IcrNF1Wo)
  - 손오공의 <b>A공격을 개편</b>하고 <b>S공격</b>까지 완성했다
  - <b>공중 공격</b>과 점프 이후의 낙하가 아닌 <b>그냥 낙하시</b> 낙하모션을 따로 제작했다
  - 애니메이터의 대공사가 필요할 것 같다
    - **AnyState의 남용은 금물이라는 것을 깨달았다.** Attack -> Fall로 자연스럽게 가지 못하고 아주 살짝 Posture_Ready가 끼어드니 자연스럽지 못한다
