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
A|Combo Punch|   
↑+A|Somersalut Kick
↓+A|  
␣+A|SledgeHammer
␣ +↑+A|Somersalut Kick
␣ +↓+A|

||Goku|Vegeta
:--:|:--:|:--:
S|Straight|  
↑+S|[D]Somersalut Kick|   |
↓+S|[P]RoundHouse Kick|   |   |
␣+S|RoundHouse Kick|   |   |
␣+↑+S|[D]Somersalut Kick|   |   |
␣+↓+S||   |   |

||Goku|Vegeta
:--:|:--:|:--:
D|   |  
↑+D|   |  
↓+D|SpiritShot|
␣+D|   |
␣+↑+D|   |
␣+↓+D|   |   |
### Development Log

#### 2019
- 11/13 [프로젝트](https://drive.google.com/open?id=1mNYOsG-oiTiDN1jlWLgxqvSDHREb4fCW)
  - 기본적인 플레이어 컨트롤은 거의 완성되었다
  - 이동, 점프, 매달리기, 매달리기-점프, 매달리기-내려오기, 웅크리기
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
    - **AnyState의 남용은 금물이라는 것을 깨달았다.**
    - Attack -> Fall로 자연스럽게 가지 못하고 아주 살짝 Posture_Ready가 끼어드니 자연스럽지 못한다

- 11/25 [프로젝트](https://drive.google.com/open?id=1C88GkHucs_BuSMGOntn5v5X69-273GNP)
  - **애니메이터 대공사 완료.** 이제 스테이트 간의 이동이 확실히 깔끔해졌고 공사하면서 덕분에 불필요한
  스크립트 코드도 많이 삭제할 수 있었다
  - 매달리기 관련 이슈가 많이 안정화되었다. 의미없는 Ground트리거 오브젝트를 제거했다
  - 바닥은 Tag를 Ground, Ground_Egde, Wall 3가지로 분류해서 느닷없이 Move로 가는 일 없이 바닥을 세분화했지만 이 때문에 원인 모를 끼임 현상이 생겼다.
  일단 크기를 조절해서 ~~야매로~~대강 해결은 했지만 잠재이슈가 남아있다.

- 12/11 [프로젝트](https://drive.google.com/open?id=1EqdlcFeoy5EsV8Fg0o1q-6nu2mM5hpO2)
  - **유니티 Photon** 멀티플레이 환경을 구축함
  - 쾌적한 동기화 환경을 구축하기 위해 모든 캐릭터(미래의 오브젝트까지)의 이동방식을 **Transform Translate → Rigidbody2D velocity와 Addforce로 변경**
  - 따라서 좌표 동기화는 렉없이 잘 되는데 문제는...
  - **<font color="red">ISSUE</font>**
    - **애니메이터 동기화가 잘 되지 않는다.**
    - 애니메이터 대공사를 한 번 거치면서 AnyState의 사용을 대폭 줄이고 파라미터 개수도 많이 줄였지만
    아직 AnyState를 의존하는 곳이 있다. 바로 **모든 공격 애니메이션**
    - 하도 많아서 이것도 AnyState없이 스테이트를 연결시키려면 화살표가 난잡하게 엉킬 것 같아서 그냥 AnyState를 사용했는데 그에 의해 아직 많이 남은 <b>트리거 파라미터</b>때문에 애니메이터 동기화가 잘 되지 않는 것 같다.
    - 따라서 다음 목표는 트리거 파라미터와 AnyState를 한번 더 정리(**제 2차 애니메이터 대공사**)
