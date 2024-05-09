# :pushpin: 귀행록
>게임 플레이 데모   
>https://drive.google.com/file/d/15a_SWD6fFbhL8xN9SLPNUQ7QEfSvUfnc/view?usp=drive_link

</br>

## 1. 프로젝트 정보
### **1) 제작 기간**
>2022.12.29 ~ 2024.2.1

### **2) 참여 인원**
>프로그래머 : 윤근용, 정태수   
>그래픽 디자이너 : 이수진

</br>

## 2. 역할 분담
**윤근용**
>아이템 저장, 사용 기능 구현
>게임 데이터 Save, Load 기능 구현
>캐릭터 애니메이션 설정
>레벨 디자인

**정태수**
>플레이어 캐릭터 물리 기반 움직임 구현   
>박스 밀기, 로프 타기, 카트 이동 등 오브젝트 상호작용 기능 구현   
>몬스터 움직임 및 추격 구현   
>사다리 타고 움직이는 기능 구현   

</br>

## 3. 사용 기술
#### `프로그래머`
- Unity
- C#

#### `그래픽 디자이너`
- Adobe Photoshop
- Clip Studio

</br>

## 4. 핵심 기능
- 아이템 매니저를 통해 획득 가능한 아이템 정보를 저장하고 관리합니다.
- JSON 기반의 세이브 시스템을 통해 플레이어 위치, 오브젝트 위치, 퍼즐 진행를 저장하고 불러올 수 있습니다.

</br>

## 5. 핵심 트러블 슈팅
### 5.1. 오브젝트 겹침으로 인한 충돌 중복 문제
- 유니티는 콜라이더를 가진 두 오브젝트 간의 충돌을 닿았을 때, 닿는 동안, 떼어졌을 때 3가지로 구분합니다.
- 플레이어가 로프를 붙잡았을 때 플레이어와 로프가 완전히 겹쳐버리면, 떼어지는 동시에 다시 닿게되어 충돌 감지에 문제가 발생합니다.


- 로프를 붙잡은 상태에서 점프했을 때, 로프 생성에 사용한 FixedJoint2D의 연결 몸체를 null로 바꾸고 FixedJoint2D 컴포넌트를 비활성화함으로써 로프와의 물리적인 연결을 해제하고,
bool값을 이용하여 로프를 붙잡은 상태와 그렇지 않은 상태를 구분지어 충돌 감지 문제를 해결하였습니다.
