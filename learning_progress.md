# MATLAB/Simulink 드론 시뮬레이션 개인 학습 진행 기록

기준일: 2026-10-16 (한국 시간)  
진도표 버전: 1.0  
학습 언어: 한국어  
상태: 1·2·3·4단원 완료(12/12, 8/8, 5/5, 9/9), 5단원 완료(6/6), 6단원 Quadcopter Control 진행 중(1/13: A06-01 완료)

## 1. 교재와 확인 범위

- 주 교재: Introduction to Quadcopter Modeling & Simulation
- 공식 저장소: https://github.com/MathWorks-Teaching-Resources/Quadcopter-Modeling-Simulation
- 확인한 브랜치: release
- 확인한 커밋: 61167f7280347f85e82134ef0f21da0cfe40d646
- README는 R2025a 제작, R2025a 이후 버전 호환을 명시한다. R2026a는 이 범위에 포함된다. 사용자 환경에서의 실행 성공을 뜻하지는 않는다.
- README, MainMenu.mlx, Scripts의 11개 본 단원과 NextSteps.mlx, Models의 9개 .slx 내부 블록·주석·라이브러리 참조, Data의 두 .mat 존재를 확인했다. Live Script는 파일 내부 문서·코드를 읽었고 Simulink 모델은 내부 구조를 검사했다. MATLAB에서 직접 실행하거나 화면을 렌더링한 것은 아니다.
- 외부 openExample 예제와 별도 배송·칼만 필터 저장소는 본 교재가 연결하는 대상임을 확인했다. 해당 외부 프로젝트의 모든 내부 과제를 조사한 것으로 간주하지 않는다.
- 현재 추가 .mlx/.slx 업로드는 필요 없다. 사용자 수정본, 로컬 버전 차이 또는 실행 오류의 확인에 필요하면 해당 파일을 요청한다.

## 2. 사용자 환경과 현재 위치

| 항목 | 상태 |
|---|---|
| MATLAB | R2026a Update 5, 26.1.0.3346908: 첨부 ver 화면 확인 |
| Simulink | 26.1 (R2026a): 첨부 ver 화면 확인 |
| 라이선스 | 대학교 라이선스: 사용자 제공 정보 |
| 그 외 제품 | 아래 설치 목록 확인. 실제 예제의 라이선스 사용 가능 여부·실행은 미확인 |
| 운영체제 | macOS 26.5.2 Build 25F84: 첨부 화면 확인 |
| MATLAB 숙련도 | 기초 수준 |
| 수학·제어 | 배운 경험 있음, 필요 개념은 기초부터 보충 |
| 학습 시간 | 고정 일정 없음 |
| 현재 위치 | 6단원 Quadcopter Control, 진행 중 4/13(A06-05 시작 전) |
| 마지막 실행 | A06-05: P=200, I=50, D=150 실행 → t=0.3764 s에서 Simulink 오류로 시뮬레이션 중지(발산) |
| 다음 행동 | 같은 이득에 A06-06 설정(출력 0~10000 제한, back-calculation 1, 적분기 제한 0~10000, 필터 계수 10) 적용해 실행하고 A06-05·06을 함께 확인 |

## 3. 진행률 계산 규칙

**A. 공식 교재 기반 학습**

- 본 단원은 11개다. 아래 79개는 실제 Live Script의 실행·Try·Exercise·Reflect 및 연결 예제를 바탕으로 튜터가 묶거나 나눈 체크포인트다. 교재가 공식적으로 발표한 과제 총개수가 아니다.
- 계산: 완료 체크포인트 수 / 79 × 100. 표시는 소수 첫째 자리로 반올림하되 0은 0%로 표시한다.
- 단원 완료: 그 단원의 체크포인트를 모두 완료했을 때만 인정한다.
- 핵심 1~6단원은 53개다. 핵심 진행률=핵심 완료 수 / 53 × 100을 보조 지표로 표시한다. 전체 79개 분모를 대신하지 않는다.
- 실행·변경 과제는 실제 사용자 실행 결과와 설명이 확인되어야 완료다. 수식/판단 과제는 직접 작성한 계산·답과 검산이 있어야 완료다. 설명 청취만으로 완료 처리하지 않는다.
- 상태: 미시작 / 진행 중 / 완료 / 보류 / 건너뜀. 체크박스 [x]는 완료에만 쓴다. 보류·건너뜀은 분모에 남으며 완료로 계산하지 않는다.
- 이미 아는 내용은 바로 결과/설명을 확인하거나 건너뛸 수 있다. 건너뛰기는 완료와 구분한다.
- 환경 준비 E00, NextSteps 자료 안내, Onramp 보충 수업은 79개에 포함하지 않는다.
- 외부 배송 프로젝트의 Exercise Select 안의 선택 과제, 칼만 필터 실험실의 추가 세부 과제, Further Resources의 모든 링크는 별도 확장 목록이다. 내부 미확인 과제 수를 꾸며내지 않는다. 분모 변경이 필요하면 버전을 올리고 변경 사유·구분 전후 수를 명시한다.

**B. 개인 시뮬레이터 제작**

- 필수 작업 20개. 계산: 완료 작업 수 / 20 × 100.
- 아래 완료 조건은 튜터가 제안한 개인 학습 프로젝트 기준이다. 공식 교재 기준이나 실제 기체 안전성 기준이 아니다.
- 관련 단원을 공부해도 개인 모델 구현·검증이 없으면 제작 완료로 계산하지 않는다.
- 교재 실습과 개인 제작이 같은 결과로 두 기준을 모두 충족하면 각각 기록할 수 있다.
- 3차원 시각화는 선택 확장 V01로 따로 기록하며 필수 20개 분모에 포함하지 않는다.

| 지표 | 완료/전체 | 진행률 |
|---|---:|---:|
| 공식 교재 본 단원 | 5/11 | 45.5% |
| 공식 교재 기반 체크포인트 | 44/79 | 55.7% |
| 핵심 체크포인트 | 44/53 | 83.0% |
| 개인 시뮬레이터 작업 | 0/20 | 0% |
| 선택 3차원 시각화 | 0/1 | 미시작 |

## 4. 전체 단원과 학습 체크포인트

각 항목 형식: ID — 원문 실습 위치 — 할 일 — 완료 조건. 1단원 전체 완료, 1~3단원 전체 완료, 나머지는 미시작이다.

### 1. Projectile Motion — 핵심

파일: `Scripts/ProjectileMotion.mlx`  
세부 목차: Free Fall → Numerical Approximation → Set Up Variables → How Many Timesteps? → Simulate and Plot in 1D → 2D Projectile Motion → Modeling Projectiles in Simulink → Implementing a 1D Projectile → Adding Drag to a 1D Projectile  
진도: 12/12

- [x] A01-01 — **Set Up Variables**: 변수를 설정하고 한 시간 간격 계산을 실행한다. 완료 조건: 변수의 단위, vNext·pNext 값, 속도·위치 그래프를 제출한다.
- [x] A01-02 — **Numerical Approximation / Try**: 반복 갱신 코드를 여러 번 실행한다. 완료 조건: 시간·속도·위치 표가 갱신된 결과와 변화 방향을 설명한다.
- [x] A01-03 — **How Many Timesteps? / Try·Reflect**: 필요 시간 간격 수를 계산한다. 완료 조건: n_timesteps 계산과 정수 여부 판단을 기록한다.
- [x] A01-04 — **Simulate and Plot in 1D / derivation**: 초기 위치가 0이 아닌 비행시간 식을 유도한다. 원문: ‘Details are left as an exercise to the reader.’ 공식 Try·Exercise 번호가 없는 독자 연습이며 교재가 최종식 t_end=(v0+√(v0²+2g·p0))/g를 제시한다. 완료 조건(튜터 기준): 사용자가 이 식이 나오는 유도 과정을 직접 쓴다. 특정 수치 계산은 추가(선택).
- [x] A01-05 — **Simulate and Plot in 1D**: 전체 1차원 시뮬레이션을 실행한다. 완료 조건: 속도·위치 그래프와 초기조건을 기록한다.
- [x] A01-06 — **Simulate and Plot in 1D / Try m**: 질량 m을 변경해 다시 실행한다. 완료 조건: 변경 전후 그래프와 자유낙하에서 질량의 역할을 설명한다.
- [x] A01-07 — **Simulate and Plot in 1D / Try v0**: 초기 속도를 변경해 다시 실행한다. 완료 조건: 최고 높이와 비행시간의 변화 방향을 기록한다.
- [x] A01-08 — **Simulate and Plot in 1D / Try dt·error**: 시간 간격을 바꾸고 코드의 오류 발생 조건을 조사한다. 완료 조건: 두 간격의 결과와 오류가 발생하거나 발생하지 않는 이유를 기록한다.
- [x] A01-09 — **2D Projectile Motion / Exercise 1**: sind·cosd로 초기 속도의 두 성분을 계산한다. 완료 조건: vx0·vy0 계산 코드와 값, 각도의 단위를 기록한다.
- [x] A01-10 — **2D Projectile Motion / Exercise 2**: 1차원 코드를 2차원 운동 코드로 확장한다. 완료 조건: 수평·수직 위치를 추적하는 코드와 궤적 그래프를 제출한다.
- [x] A01-11 — **Implementing a 1D Projectile / model annotation**: Projectile_1D.slx에 운동 모델과 종료 조건을 직접 구성한다. 완료 조건: 초기 위치 10 m, 초기 속도 50 m/s에서 실행한 모델·Scope·종료 결과를 제출한다.
- [x] A01-12 — **Adding Drag to a 1D Projectile / Reflect**: Projectile_1D_WithDrag.slx에 항력 모델을 구성한다. 완료 조건: 항력 포함·미포함 및 항력 계수 변경 결과와 지면 도달 시점을 비교한다.

### 2. Rigid Transforms — 핵심

파일: `Scripts/RigidTransforms.mlx`  
세부 목차: 점군 불러오기 → 회전·병진 객체 → 순차 변환 → 전체 변환 → Try → 애니메이션 Exercise → 6자유도 플랫폼 예제 → Rotations, Orientation, and Quaternions → Further Explorations  
진도: 8/8

- [x] A02-01 — **initial point cloud**: 찻주전자 점군을 불러와 표시한다. 완료 조건: 원본 점군과 좌표축을 확인한다.
- [x] A02-02 — **incremental transforms**: tform1·tform2·tform3을 순차 적용한다. 완료 조건: 각 단계의 위치·방향 결과를 기록한다.
- [x] A02-03 — **full transform**: 전체 변환 tform을 적용한다. 완료 조건: 순차 변환 결과와 비교하고 일치 여부를 설명한다.
- [x] A02-04 — **Try / switch tform1 and tform3**: 변환 순서를 바꿔 다시 실행한다. 완료 조건: 변경 전후 결과를 비교하고 순서의 영향을 설명한다.
- [x] A02-05 — **Try / sliders**: 각도·병진 값을 변경한다. 완료 조건: 변경 값을 기록하고 예상 위치와 실제 그림을 비교한다.
- [x] A02-06 — **Exercise / animation**: for 반복문으로 부드러운 변환 애니메이션을 작성한다. 완료 조건: 완성 코드·시작/끝 상태·실행 결과와 운동 결합에 대한 답변을 제출한다.
- [x] A02-07 — **6DOF platform / openExample**: 공식 6자유도 플랫폼 예제를 열고 실행한다. 완료 조건: 힘·모멘트 입력과 운동 출력 블록을 찾아 기록한다.
- [x] A02-08 — **Rotations, Orientation, and Quaternions**: 연결된 QuaternionExample을 실행한다. 완료 조건: 예제의 회전 표현 결과와 사용 단위를 기록한다.

### 3. Propeller Model — 핵심

파일: `Scripts/PropellerModel.mlx`  
세부 목차: Motivation → Momentum theory → Blade element reasoning → Dimensional analysis → Modeling assumptions → Thrust model → Reaction torque model → Drag on a blade element → Torque → Impact on Quadcopter Design → Further Design Considerations  
진도: 5/5

- [x] A03-01 — **Thrust model / Exercise 1**: 호버링에 필요한 프로펠러 각속도를 계산한다. 완료 조건: omega_hover를 작성하고 CheckEx1의 확인 결과와 단위를 제출한다.
- [x] A03-02 — **Reaction torque / Exercise 2a**: 허브 부근의 유입각 변화에 답한다. 완료 조건: CheckEx2 a 결과와 물리적 이유를 기록한다.
- [x] A03-03 — **Reaction torque / Exercise 2b**: 블레이드 끝 부근의 유입각 변화에 답한다. 완료 조건: CheckEx2 b 결과와 물리적 이유를 기록한다.
- [x] A03-04 — **Impact on Quadcopter Design / Try·Reflect**: SimplePropellerModel 함수로 추력·토크 곡선을 그린다. 완료 조건: 두 곡선의 단위와 제곱 의존성을 설명한다. 교재의 증가율 질문은 계수·단위 차이와 상대 증가율을 구분한다.
- [x] A03-05 — **Exercise 3**: SimplePropellerModel.slx에 추력·토크 블록을 직접 구성한다. 완료 조건: 입력값·출력값을 MATLAB 함수 결과와 비교한다.

### 4. Quadcopter Basics — 핵심

파일: `Scripts/QuadcopterBasics.mlx`  
세부 목차: Quadcopter Coordinate System → Propeller Configuration → Motivating example → Simple Geometric Model → Simple Inertia Model → Inertia of Propellers → Inertia of Body → Thrust and yaw-drag model → Derive the Mixer → Estimate Constants → Performance Curves → Forces and Torques → Save the Parameter Values → Next Steps  
진도: 9/9

- [x] A04-01 — **Simple Geometric Model**: 기체·프로펠러 질량과 위치를 계산한다. 완료 조건: 총질량과 프로펠러 번호·좌표·회전 방향을 기록한다.
- [x] A04-02 — **Simple Inertia Model / plus**: +형의 관성행렬 계산을 실행한다. 완료 조건: Ixx·Iyy·Izz와 단위를 기록한다.
- [x] A04-03 — **Simple Inertia Model / x·Reflect**: x형으로 바꾸어 관성 계산을 비교한다. 완료 조건: 형상·좌표 변경과 관성 결과의 관계를 설명한다.
- [x] A04-04 — **Derive the Mixer**: 힘·모멘트 변환 행렬 A를 계산한다. 완료 조건: 입력이 회전속도의 제곱이라는 점과 각 행의 단위를 설명한다.
- [x] A04-05 — **Derive the Mixer / configuration·Reflect**: 두 배치의 mixer를 비교한다. 완료 조건: 계산에 사용한 pB와 선택한 배치가 일치하는지 확인하고 부호 패턴을 기록한다.
- [x] A04-06 — **Estimate Constants**: 4000 회/분 호버 설계점으로 kT·km을 계산한다. 완료 조건: W·T_prop·kT·km과 속도 기준 단위를 기록한다.
- [x] A04-07 — **Performance Curves**: 추력·모멘트 성능 곡선을 실행한다. 완료 조건: 그래프와 4000 회/분에서의 값을 기록한다.
- [x] A04-08 — **Forces and Torques**: 같은 속도의 네 프로펠러를 mixer에 입력한다. 완료 조건: 총추력−무게와 세 모멘트를 확인하고 회전 방향 관련 Reflect에 답한다.
- [x] A04-09 — **Save the Parameter Values**: 파라미터를 Data 폴더에 저장한다. 완료 조건: 실제 생성된 .mat 이름·배치·질량·관성·mixer를 확인한다.

### 5. Quadcopter Movement — 핵심

파일: `Scripts/QuadcopterMovement.mlx`  
세부 목차: Quadcopter Simulation → Quadcopter Movement - Elevation → Pitch, Roll, and Yaw → Quadcopter Movement - Pitch → Quadcopter Movement - Roll → Quadcopter Movement - Yaw → Next Steps  
진도: 6/6

- [x] A05-01 — **Quadcopter Simulation / Try**: UAV_Sim.slx에서 네 프로펠러를 4000 회/분으로 실행한다. 완료 조건: 초기 호버 결과와 총힘·모멘트 균형을 확인한다.
- [x] A05-02 — **Elevation / Try**: 네 프로펠러의 공통 속도를 호버보다 높거나 낮게 바꾼다. 완료 조건: 상승·하강 그래프와 원인을 기록한다.
- [x] A05-03 — **Pitch / Exercise**: 선택한 배치에 맞게 전진하는 속도 조합을 만든다. 완료 조건: 프로펠러 입력과 pitch·위치 결과, 장시간 불안정 원인을 기록한다.
- [x] A05-04 — **Roll / Exercise right**: 오른쪽 roll 입력을 구성한다. 완료 조건: 프로펠러 입력·회전 부호·횡이동 결과를 기록한다.
- [x] A05-05 — **Roll / Exercise left·Reflect**: 왼쪽 roll 입력을 구성한다. 완료 조건: 반대 방향 결과와 +형·x형 부호 패턴의 차이를 설명한다.
- [x] A05-06 — **Yaw / Exercise·Reflect**: 위에서 본 반시계·시계 회전을 각각 구성한다. 완료 조건: 두 입력 조합과 yaw 방향을 기록하고 총추력이 보존되는지 계산한다.

### 6. Quadcopter Control — 핵심

파일: `Scripts/QuadcopterControl.mlx`  
세부 목차: Loading up Quadcopter Parameters → Equation of Motion (1D) → Modeling Propeller Forces → Propeller Thrust vs Speed → Closed-Loop Feedback Control → Demonstration: Tuning the PID Controller → Proportional → Derivative → PID → PID - Anti-windup + Saturation → Quadcopter Hover Control → Quadcopter Position Control using multiple PID loops → Further Resources  
진도: 4/13

- [x] A06-01 — **Propeller Thrust vs Speed**: 파라미터를 불러와 추력 곡선을 실행한다. 완료 조건: 속도·추력 단위와 수직 운동식의 질량·부호를 확인한다.
- [x] A06-02 — **Closed-Loop / Exercise·Initialization**: QuadcopterPID_Vertical.slx에 PID를 연결하고 적분기 초기값을 설정한다. 완료 조건: 오차→제어기→prop_speed 경로와 초기값 4000을 기록한다.
- [x] A06-03 — **Proportional / Try**: P=80, I=0, D=0으로 실행한다. 완료 조건: 목표·실제 고도 및 진동 결과를 기록한다.
- [x] A06-04 — **Derivative / Try**: P=120, I=0, D=40으로 실행한다. 완료 조건: 앞선 결과와 응답 차이를 설명한다.
- [ ] A06-05 — **PID / Try**: P=200, I=50, D=150으로 실행한다. 완료 조건: 목표·실제 고도와 세 제어항의 역할을 설명한다.
- [ ] A06-06 — **PID - Anti-windup + Saturation**: 교재의 출력 제한·적분기 제한·역계산·필터 설정을 적용한다. 완료 조건: 설정표와 제한 적용 전후 고도·명령 결과를 제출한다.
- [ ] A06-07 — **Quadcopter Hover Control**: UAV_Hover_Sim.slx에 고도 제어기를 구현한다. 완료 조건: 목표 높이로 이동하고 호버하는 응답을 제출한다.
- [ ] A06-08 — **Quadcopter Hover Control / PID Tuner**: PID Tuner로 호버 제어기의 이득을 조정한다. 완료 조건: 실제 적용한 이득과 조정 전후 결과를 제출한다. 제품 미설치 시 보류하며 완료로 처리하지 않는다.
- [ ] A06-09 — **Position Control / Try baseline**: XY_Control.slx를 실행하고 제어 경로를 추적한다. 완료 조건: 위치 제어·자세 제어·프로펠러 명령의 연결을 기록한다.
- [ ] A06-10 — **Position Control / altitude**: 목표 고도를 변경한다. 완료 조건: 목표·실제 고도와 애니메이션 결과를 비교한다.
- [ ] A06-11 — **Position Control / X and Y**: X·Y 목표를 변경한다. 완료 조건: 목표·실제 위치와 roll·pitch의 관계를 기록한다.
- [ ] A06-12 — **Position Control / yaw**: yaw 목표를 변경한다. 완료 조건: 목표·실제 yaw와 회전 단위를 기록한다.
- [ ] A06-13 — **Position Control / Reflect**: Propeller Speed 하위 시스템을 조사한다. 완료 조건: mixer·부호 있는 제곱근의 의미와 물리적 제한을 실제 블록값을 근거로 설명한다.

### 7. Multidomain Physical Modeling — 선택 심화

파일: `Scripts/MultidomainPhysicalModeling.mlx`  
세부 목차: What is Simscape? → DC Motor Model → Propeller Physical Model → A Current-Controlled Propeller Model  
진도: 0/10

- [ ] A07-01 — **DC Motor Model**: 연결된 PWMControlledDCMotorExample을 실행한다. 완료 조건: 전기 입력·모터·속도 제어 흐름을 기록한다.
- [ ] A07-02 — **Propeller Physical Model / baseline**: Propeller_Model.slx를 조사하고 실행한다. 완료 조건: 추력 곡선과 이상 속도원의 역할을 설명한다.
- [ ] A07-03 — **Propeller Physical Model / ramp**: 램프 시작 시점·기울기를 바꾼다. 완료 조건: 변경 전후 추력 응답을 기록한다.
- [ ] A07-04 — **Propeller Physical Model / units**: 속도 출력을 라디안/초에서 회/분으로 변환한다. 완료 조건: 변환 코드 또는 블록과 수치 검산을 제출한다.
- [ ] A07-05 — **Propeller Physical Model / geometry·mass**: 프로펠러 직경·질량을 변경한다. 완료 조건: 각 변경에 따른 출력과 이상 속도원이 갖는 한계를 설명한다.
- [ ] A07-06 — **Current-Controlled / baseline·comparison**: Propeller_Ref_Speed.slx를 실행한다. 완료 조건: 목표·실제 속도와 전류·추력 결과를 이상 속도 모델과 비교한다.
- [ ] A07-07 — **Current-Controlled / ramp**: 목표 램프 시작 시점·기울기를 바꾼다. 완료 조건: 전류·토크·추력 변화 결과를 기록한다.
- [ ] A07-08 — **Current-Controlled / voltage**: 전압원 값을 바꾼다. 완료 조건: 전류·토크·추력 결과와 전압값을 기록한다.
- [ ] A07-09 — **Current-Controlled / propeller**: 직경·추력계수·동력계수를 변경한다. 완료 조건: 변경한 값과 영향이 나타나는 출력을 기록한다.
- [ ] A07-10 — **Current-Controlled / InitFcn·interfaces**: InitFcn의 모터·제어기 파라미터를 변경하고 변환 블록을 조사한다. 완료 조건: 변경 전후 응답과 전기·기계·신호의 연결 위치를 제출한다.

### 8. Trajectory Generation — 선택 심화

파일: `Scripts/ExampleCollectionOnTrajectories.mlx`  
세부 목차: 웨이포인트와 B-spline 계산 → 속도·가속도·jerk → B-Spline Trajectories → Generate Minimum Jerk Trajectory Example → Package Delivery Quadcopter Example  
진도: 0/6

- [ ] A08-01 — **waypoint Try**: 기본 B-spline 궤적을 실행한다. 완료 조건: 웨이포인트·제어점·궤적 그래프를 기록한다.
- [ ] A08-02 — **waypoint Try / modify**: 웨이포인트를 변경·추가·삭제한다. 완료 조건: 각 변경의 궤적 결과 또는 발생 오류와 해결을 기록한다.
- [ ] A08-03 — **PlotDerivatives**: UseComputedValues 두 설정을 비교한다. 완료 조건: 속도·가속도·jerk 결과와 미분 계산 방법의 차이를 설명한다.
- [ ] A08-04 — **B-Spline Trajectories**: 연결된 2차원 공식 예제를 실행한다. 완료 조건: 예제 입력과 궤적 결과를 기록한다.
- [ ] A08-05 — **Minimum Jerk**: 연결된 최소 jerk 예제를 실행한다. 완료 조건: 여러 Scope에서 위치와 미분량을 함께 확인한다.
- [ ] A08-06 — **Package Delivery Quadcopter Example**: 연결된 sm/QuadcopterExample을 실행한다. 완료 조건: 패키지 전달 과정과 물리 모델의 주요 부분을 기록한다.

### 9. Quadcopter Package Delivery — 선택 심화

파일: `Scripts/QuadcopterFromFEX.mlx`  
세부 목차: 외부 Quadcopter Drone Model in Simscape 프로젝트 열기 → electrical/mechanical/maneuver controller 조사 → 배송·복귀 시각화 → Further Exercises (Optional)  
진도: 0/2

- [ ] A09-01 — **linked project / download·run**: 연결된 Quadcopter_Drone.prj를 열고 배송·복귀 예제를 실행한다. 완료 조건: 프로젝트 버전·실행 결과·3차원 시각화를 기록한다.
- [ ] A09-02 — **Explore the model**: 전기·기계·기동 제어 하위 시스템을 조사한다. 완료 조건: 입출력 연결과 각 하위 시스템의 역할을 실제 모델을 근거로 설명한다.

### 10. Sensor Fusion — 선택 심화

파일: `Scripts/SensorFusion.mlx`  
세부 목차: Sensor Fusion → IMU and GPS Fusion example → Kalman Filtering (Recommended) → Also Explore  
진도: 0/3

- [ ] A10-01 — **IMU and GPS Fusion**: 연결된 공식 센서 융합 예제를 실행한다. 완료 조건: 센서 측정·참값·추정 결과의 차이를 기록한다.
- [ ] A10-02 — **Kalman Filtering / linked virtual lab**: 연결된 Kalman Filter Virtual Lab의 선형 필터 실습을 수행한다. 완료 조건: 실제 파일·실습 위치·측정값과 추정값 결과를 기록한다. 세부 과제는 외부 프로젝트 확인 후 보충 목록으로 관리한다.
- [ ] A10-03 — **Kalman Filtering / linked virtual lab**: 연결된 실험실의 비선형 확장 필터 실습을 수행한다. 완료 조건: 실제 파일·실습 위치·추정 결과를 기록한다. 실행 전 실제 포함 여부와 의존 제품을 확인한다.

### 11. Scenario Generation — 선택 심화

파일: `Scripts/ScenarioGeneration.mlx`  
세부 목차: UAV Scenario Tutorial → Plan Minimum Snap Trajectory → Photorealistic Simulation with Unreal Engine → UAV Package Delivery → Further Exploration  
진도: 0/5

- [ ] A11-01 — **UAV Scenario Tutorial**: 연결된 저해상도 도시 시나리오 예제를 실행한다. 완료 조건: 환경·기체·센서와 출력 데이터를 기록한다.
- [ ] A11-02 — **Minimum Snap**: 연결된 쿼드로터 경로 계획 예제를 실행한다. 완료 조건: 경로·장애물·궤적 결과를 기록한다.
- [ ] A11-03 — **SimpleFlightAndSensorInUE4Example**: 연결된 사실적 비행·센서 예제를 실행한다. 완료 조건: 운영체제·지원 패키지 확인 후 실제 실행 결과를 제출한다. 불가 시 보류한다.
- [ ] A11-04 — **UAVPackageDeliveryExample**: 연결된 배송 예제를 실행한다. 완료 조건: 실제 사용한 모델 충실도와 배송 결과를 기록한다.
- [ ] A11-05 — **Further Exploration / depth·segmentation**: 연결된 깊이·분할 시각화 예제를 실행한다. 완료 조건: 깊이와 분할 결과를 비교한다. 실행 환경이 없으면 보류한다.

### 별도 부록: NextSteps.mlx — 선택 확장, 진행률 분모 제외

목차: Advanced Control / Working with ROS & Gazebo / Projects - MATLAB and Simulink Challenge Project Hub / Further Resources.

내용: 모델 예측·강화학습 제어, 로봇 운영체제 연동·Gazebo, 도전 프로젝트, 하드웨어 지원과 드론 제어 영상. 필요한 경우 실제 연결 자료를 확인한 후 별도 목표로 추가한다.

## 5. 파일 구성과 연결 예제

| 위치 | 확인한 파일/역할 |
|---|---|
| 루트 | UAV.prj: 프로젝트 시작, MainMenu.mlx: 단원 안내, README.md·README.mlx: 소개 |
| Scripts | 위 11개 본 단원과 NextSteps.mlx |
| Models | Projectile_1D.slx, Projectile_1D_WithDrag.slx, SimplePropellerModel.slx, UAV_Sim.slx, QuadcopterPID_Vertical.slx, UAV_Hover_Sim.slx, XY_Control.slx, Propeller_Model.slx, Propeller_Ref_Speed.slx |
| Data | plus_quad_params.mat, x_quad_params.mat |
| FunctionLibrary | 외부 예제 다운로드 등의 보조 함수 |
| InstructorResources/Solutions | 풀이 Live Script와 완성 모델: 필요할 때 결과 비교용 |

Projectile_1D, Projectile_1D_WithDrag, SimplePropellerModel은 내부에 구축 지침을 넣은 빈 과제 모델이다. QuadcopterPID_Vertical과 UAV_Hover_Sim은 PID를 추가하는 과제가 포함된다. 빈 모델을 실행 실패 또는 파일 누락으로 오해하지 않는다.

연결 예제는 기본 저장소 파일과 별개다. 필요 시 MATLAB에서 다운로드되며 현재 사용자의 설치·네트워크·운영체제에 맞는지를 실행 전에 확인한다.

| 단원 | 코드에서 확인한 외부 예제/프로젝트 |
|---|---|
| 2 | aeroblks/ModelingASixDegreeOfFreedomMotionPlatformExample, shared_positioning/QuaternionExample |
| 7 | simscapeelectrical/PWMControlledDCMotorExample |
| 8 | robotics/ComputeBSplineTrajectoryFor2DPlanarMotionExample, shared_uav_robotics/GenerateMinimumJerkTrajectoryExample, sm/QuadcopterExample |
| 9 | https://github.com/mathworks/Quadcopter-Drone-Model-Simscape — Quadcopter_Drone.prj |
| 10 | shared_positioning/IMUandGPSFusionExample, https://github.com/MathWorks-Teaching-Resources/Kalman-filter-virtual-lab |
| 11 | uav/UAVScenarioTutorialExample, uav/PlanMinimumSnapTrajectoryForQuadrotorExample, uav/SimpleFlightAndSensorInUE4Example, uav/UAVPackageDeliveryExample, uav/DepthAndSegmentationVisualizationUsingUE4SimulationExample |

## 6. 필요한 제품과 설치 확인 계획

| 범위 | 제품 | 확인 근거와 상태 |
|---|---|---|
| 1단원 | MATLAB, Simulink | 코드·기본 블록. 첨부 화면에서 설치 확인, 교재 실제 실행 미확인 |
| 2단원 점군 | Image Processing Toolbox, Computer Vision Toolbox | README 명시, pcread·pcshow·pctransform·rigidtform3d 사용. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 2단원 플랫폼, 5~6단원 | Aerospace Blockset | 6자유도 운동 블록. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 3~4단원 | Symbolic Math Toolbox | README 명시, 기호 계산·확인 함수의 displayFormula 사용. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 5~6단원 시각화 | UAV Toolbox | UAV Animation 참조. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 6단원 자동 이득 조정 | Simulink Control Design, 관련 Control System Toolbox 의존 제품 | PID Tuner의 Simulink 모델 조정은 Simulink Control Design 필요. 수동 PID 블록 실행과 구분. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 7단원 | Simscape, Simscape Driveline, Simscape Electrical | fl_lib·nesl_utility·sdl_lib·ee_lib 참조와 전기 모터 예제. 첨부 설치 목록 참조. 실제 실행 미확인 |
| 8단원 | Robotics System Toolbox, 배송 물리 예제용 Simscape·Simscape Multibody 등 | bsplinepolytraj와 연결 예제. 외부 예제의 전체 제품은 실행 전 재확인 |
| 9단원 | 외부 배송 프로젝트 요구 제품 | 상세 의존성은 외부 프로젝트의 해당 버전 확인 후 확정 |
| 10단원 | Sensor Fusion and Tracking Toolbox 또는 해당 공유 예제가 지원하는 제품 조합 | 교재 설명과 공식 융합 예제. 공유 예제의 제품 조합·필터 실험실 의존성은 실행 전 확인 |
| 11단원 | UAV Toolbox, Unreal Engine 연동용 해당 지원 패키지·예제별 추가 제품 | 운영체제 및 R2026a 지원 범위를 별도 확인 |
| README의 공통 제품 목록 | Stateflow, Simulink Real-Time도 기재됨 | 현재 확인한 1단원 기본 실습의 필수 제품으로 단정하지 않음. 관련 예제에서 실제 요구 여부 확인 |

R2026a PID Tuner 공식 문서: https://www.mathworks.com/help/releases/R2026a/control/ref/pidtuner-app.html

사용자 MATLAB의 `ver` 결과는 첨부 화면으로 확인했다. 설치된 제품과 라이선스 사용 가능 여부는 다르므로 필요한 제품은 실제 예제 열기·모델 갱신·실행으로 추가 확인한다. 이후 제품의 추가 설치는 해당 실습 전에만 확인하고 한 단계씩 안내한다.

### 2026-10-13 첨부 화면의 설치 제품 확인

근거: `image(20261013-073437).png`의 MATLAB `ver` 전체 화면. 아래 32개 제품이 표시되며 모두 Version 26.1 (R2026a)이다. 라이선스 번호는 기록하지 않는다.

`MATLAB`, `Simulink`, `Aerospace Blockset`, `Aerospace Toolbox`, `Computer Vision Toolbox`, `Control System Toolbox`, `Embedded Coder`, `Image Processing Toolbox`, `MATLAB Coder`, `MATLAB Compiler`, `MATLAB Report Generator`, `Optimization Toolbox`, `Requirements Toolbox`, `Robotics System Toolbox`, `Simscape`, `Simulink Check`, `Simulink Coder`, `Simulink Compiler`, `Simulink Control Design`, `Simulink Coverage`, `Simulink Design Optimization`, `Simulink Design Verifier`, `Simulink Desktop Real-Time`, `Simulink FMU Builder`, `Simulink Fault Analyzer`, `Simulink PLC Coder`, `Simulink Report Generator`, `Simulink Test`, `Stateflow`, `Symbolic Math Toolbox`, `UAV Toolbox`, `Vehicle Dynamics Blockset`.

현재 1~6단원에서 확인한 핵심 제품과 Simulink PID 자동 조정 제품은 설치 목록에 있다. `Simscape Electrical`, `Simscape Driveline`, `Simscape Multibody`, `Sensor Fusion and Tracking Toolbox`, `Navigation Toolbox`, `Simulink Real-Time`은 이 화면에 표시되지 않는다. `Simscape` 설치만으로 개별 Simscape 확장 제품 설치를 의미하지 않으며, `Simulink Desktop Real-Time`은 `Simulink Real-Time`과 별도 제품이다. 심화 예제 전에 필요한 제품만 확인한다.

## 7. 개인 시뮬레이터 예상 구조 — 교재를 바탕으로 한 추가 제작 계획

1차 버전: 목표 고도 → 오차 → 고도 제어기 → 공통 프로펠러 속도 → 네 추력의 합 → 무게·외력과 합산 → 수직 가속도 → 속도·고도 → 실제 고도 피드백.

확장 버전: 목표 고도·roll·pitch·yaw → 고도/자세 제어기 → 총추력·세 축 모멘트 명령 → mixer와 속도 제한 → 프로펠러 추력·토크 → 강체 운동 → 실제 고도·자세 피드백. 운동 출력과 목표는 그래프·선택 애니메이션에 연결한다. 질량·관성은 운동 모델 파라미터이고 외력·외부 모멘트는 운동 입력에 추가한다.

초기 모델은 이상적인 속도 입력·고정 질량·참 상태 피드백을 사용한다. 실제 전기 모터·센서·추정기·사실적 환경은 심화 확장이다. 처음부터 배송 모델을 복사해 최종 프로젝트로 삼지 않는다.

병진 3축+회전 3축인 6자유도(Six Degrees of Freedom, 6DOF) 블록을 사용할 수 있지만, 내부 운동방정식과 좌표변환을 함께 학습한다. 블록을 사용했다고 원리를 이해한 것으로 기록하지 않는다.

고도 제어에서 사용할 비례·적분·미분 제어(Proportional–Integral–Derivative control, PID)는 6단원에서 항별로 구현하고 응답을 비교한다.

### 필수 제작 작업 20개

아래 수치 기준은 학습용 제안 기준이며 추후 변경 시 이유와 버전을 기록한다. 마지막 3초 조건은 각 시험의 10초 실행에서 평가한다. 세 축 자세 시험은 고도 제어를 켠 상태에서 한 축씩 한다. 외란 시험의 성능 저하는 그 자체가 미완료가 아니며, 실행·정량 비교·원인 분석이 완료 조건이다.

- [ ] B01 — **기본 파라미터**. 완료 조건: 중력·질량·초기조건·좌표계·단위를 하나의 초기화 파일에 정리한다.
- [ ] B02 — **수직 운동 모델**. 완료 조건: 합력/질량→가속도→속도→위치의 블록을 직접 구성하고 출력한다.
- [ ] B03 — **운동 모델 검산**. 완료 조건: 추력 0에서 해석식과 수치 결과를 비교하고 시간 간격에 따른 오차를 기록한다.
- [ ] B04 — **기체 질량·관성**. 완료 조건: 선택한 배치의 질량·관성행렬·프로펠러 위치를 계산하고 저장한다.
- [ ] B05 — **프로펠러 모델**. 완료 조건: 속도 제곱→추력·반작용 토크 모델을 만들고 함수/블록 결과를 비교한다.
- [ ] B06 — **호버 평형**. 완료 조건: 네 프로펠러 추력 합=무게, 세 모멘트=0인 입력을 계산·검증한다.
- [ ] B07 — **수직 개루프 통합**. 완료 조건: 추력 모델과 수직 운동 모델을 연결해 호버·상승·하강을 실행한다.
- [ ] B08 — **피드백 경로**. 완료 조건: 목표 고도−실제 고도 오차와 제어 명령을 연결하고 부호를 검산한다.
- [ ] B09 — **비례 제어**. 완료 조건: 비례 제어를 직접 구현·실행하고 고도 응답을 저장한다.
- [ ] B10 — **비례·미분 제어**. 완료 조건: 미분 항을 추가하고 진동·응답 차이를 비교한다.
- [ ] B11 — **비례·적분·미분 제어**. 완료 조건: 적분 항을 추가하고 목표 추종 응답을 저장한다.
- [ ] B12 — **명령 제한**. 완료 조건: 실현 가능한 프로펠러 속도 범위를 지정하고 포화·적분 누적 방지를 시험한다.
- [ ] B13 — **상승·호버 검증**. 완료 조건: 초기 고도 0 m, 목표 2 m에서 10초 실행한다. 마지막 3초의 고도 오차 절댓값이 0.1 m 이하이고 명령이 제한 안에 드는 결과를 제출한다.
- [ ] B14 — **힘·모멘트 배분**. 완료 조건: 총추력·세 축 모멘트를 네 프로펠러 속도로 바꾸고 다시 계산해 검산한다.
- [ ] B15 — **6자유도 운동 통합**. 완료 조건: 병진·회전 운동을 연결하고 사용 블록의 운동식·관성·입출력·좌표변환을 설명한다.
- [ ] B16 — **Roll 자세 제어**. 완료 조건: 자체 모델에 roll 목표를 연결하고 목표 0°와 5° 응답을 비교한다. 마지막 3초 오차 2° 이하를 확인한다.
- [ ] B17 — **Pitch 자세 제어**. 완료 조건: pitch 목표 0°와 5°에 같은 검증을 수행한다.
- [ ] B18 — **Yaw 자세 제어**. 완료 조건: yaw 목표 0°와 10°에 같은 검증을 수행하고 각도 단위·주기 처리를 기록한다.
- [ ] B19 — **외란·질량 시험**. 완료 조건: 1 N 수직 외력을 1초 가하는 시험과 질량 +20%의 별도 재실행 시험을 수행한다. 기준 응답과 오차·정착·명령을 비교하고 실패도 기록한다.
- [ ] B20 — **통합·재현 검증**. 완료 조건: 초기화부터 고도·세 축 자세·외란 시험을 다시 실행한다. 목표/실제 응답·명령 그래프, 파일 목록과 결과를 저장하고 전체 폐루프를 설명한다.

- [ ] V01 — 선택 3차원 시각화. 위치·자세 결과를 UAV Animation 또는 기본 MATLAB 도형 애니메이션에 연결하고 그래프와 방향이 일치하는지 확인한다. 필수 제작 진행률에 포함하지 않는다.

자체 파일명 후보: `personal_drone_init.m`, `personal_vertical.slx`, `personal_quadcopter.slx`, `run_personal_tests.m`. 아직 생성된 파일이 아니며 실제 생성 후 파일 목록에 등록한다.

## 8. 교재 확인 중 발견한 보충·검산 지점

이 항목은 사용자 실행 오류 기록이 아니다. 교재를 그대로 설명하기 전에 확인해야 할 원문 내부 불일치다.

- 좌표 부호: ProjectileMotion은 위쪽 양의 y, 드론 기체 좌표는 전방 x·오른쪽 y·아래쪽 z다. 고도 제어는 위쪽 양의 높이로 전환한다. 높이와 아래쪽 양의 위치를 같은 신호로 혼용하지 않는다.
- 단위: PropellerModel은 라디안/초, Basics·Movement·Control의 추력 파라미터는 회/분 기반이다. 서로 다른 kT를 그대로 재사용하지 않는다.
- QuadcopterBasics의 mixer 설명 식 중 속도 벡터가 제곱 없이 적힌 곳이 있으나 실제 코드·뒤 단원은 속도 제곱을 사용한다.
- QuadcopterBasics의 초기 배치 선택 뒤 mixer 코드가 `pB = propX.'`를 다시 지정한다. +형을 선택해 실행할 때 배치와 mixer가 일치하는지 실제 결과를 확인해야 한다. 후속 제작에서는 명시적인 배치 선택을 사용한다.
- RigidTransforms의 회전 순서 설명과 실제 `rot = Rx*Ry*Rz`·순차 변환은 적용 관례를 구분해서 검산해야 한다. 수식과 코드가 항상 일치한다고 가정하지 않는다.
- QuadcopterControl의 위쪽 양의 가속도 설명 식에서 질량 나눗셈이 빠진 문장이 있다. 실제 모델은 Gain에서 질량을 반영한다. 올바른 가속도 단위는 길이/시간²다.
- PropellerModel의 추력과 토크 증가율 질문은 서로 다른 단위·계수의 크기와 동일한 제곱 속도 의존성을 구분해야 한다.

- UAV_Sim.slx의 6DOF (Quaternion) 블록은 Initial mass 1.0, Inertia eye(3)이다(사용자 첨부 화면 확인). 4단원 기체는 Mquad 1.3 kg, 관성 약 0.0061 kg·m²이므로 UAV_Sim의 가속도·각가속도는 이 값에 맞는다(상승 8 m, 각가속도 약 0.0074 rad/s²로 검산 일치). 호버 평형(추력=W)은 질량과 무관하게 성립한다. 개인 제작(B 작업)에서는 질량·관성을 4단원 값과 일치시킨다.

교재 수정이 필요하면 원본 설명, 확인 근거, 개인 사본 수정 내용을 구분해 기록한다. 추가 외란 주입·질량 시험·개인 모델 통합·정량 완료 기준은 튜터가 구성한 추가 실습이다. 주 교재에 같은 형태의 독립 과제가 있다고 주장하지 않는다.

## 9. 현재 파일·문제·이해 기록

### 실제 생성한 사용자 학습 파일

| 파일 | 역할 | 상태 |
|---|---|---|
| learning_progress.md | 전체 진도·현재 위치·문제·인계 기록 | 생성 완료 |
| 사용자 작성 .m/.mlx/.slx/.mat | 실습 코드·모델·파라미터 | 아직 없음 |

공식 교재 원본을 확인하기 위해 내려받은 파일은 사용자 제작물로 집계하지 않는다.

### 사용자 실행 문제

- 현재 문제(A06-05): P=200, I=50, D=150(제한 없음) 실행 시 ‘상태 1의 도함수가 유한하지 않다’ 오류와 최소 스텝 경고로 t=0.3764 s에 중지. 사용자 입력 오류 아님. 튜터 확인: 같은 식을 고정 스텝(2e-5 s)으로 직접 풀면 t≈0.376 s 부근에서 발산(미분 킥으로 속도 약 260 m/s, 이후 D·속도 항으로 명령이 음수 −3×10⁴ rpm 이상, 추력이 속도 제곱이라 음수 명령도 위쪽 추력(약 825 N)이 되어 되먹임이 양으로 바뀌며 폭주). 해결 방향: A06-06 출력 하한 0·상한 10000·필터 계수 10. A06-05는 안정 실행 그래프 확인 뒤 완료 처리. 아래 ‘6DOF 블록 질량·관성’ 항목은 교재 모델 특성으로 기록(오류 아님).
- 해결한 문제(A05-01): 첫 sim에서 기체가 600 m 넘게 낙하. w를 4000으로 설정하는 셀을 실행하지 않아 파일에서 불러온 w로 실행된 것으로 추정(w 값은 직접 확인하지 못함). 같은 셀에서 w 설정과 sim을 함께 실행해 호버 확인.
- 해결한 문제: Step 2에서 늘지 않던 문제. Run Section으로 반복 실행하자 Step 1~4가 누적됨을 사용자 첨부 화면(표·그래프)에서 확인했다. 전체 Run은 초기화 구간(변수·빈 표)을 다시 실행해 표가 처음 상태로 돌아갈 수 있다고 설명했다. 사용자가 실제로 눌렀던 버튼은 끝내 미확인이다.
- 참고: 이번 표의 초기 속도는 10 m/s로, 앞서 변경했던 20 m/s가 원문 기본값으로 돌아와 있었다. 초기화 구간 재실행 때문으로 추정하며 확인하지는 않았다. A01-02 완료는 v0=10 m/s 기준으로 검산했다.
- 해결한 오류: A01-03 코드 셀에 한글 문장이 주석 기호(%) 없이 입력되어 발생한 'Invalid text character' 오류. 줄 앞에 %를 붙여 해결(사용자 첨부 화면 확인).
- 해결한 오류: A01-10 코드 상자의 ‘Illegal use of reserved keyword "end"’. 튜터 골격의 `...`(줄 이음 기호)와 대입이 아닌 `==`가 원인이었고 수정 후 해결(튜터 골격 실수).
- 참고: Step 고정 문제는 오류 메시지가 아닌 실행 방법 문제였다.
- 준비 확인 완료: ver 화면의 설치 제품 32개, MATLAB R2026a Update 5, macOS 26.5.2.
- 교재 다운로드 및 UAV.prj 열기 확인 완료: image(20261013-075234).png에서 프로젝트 제목·폴더·StartUp App 확인.
- 사용자 교재 경로: /Users/min/Documents/MATLAB/Quadcopter-Modeling-Simulation-release
- 준비 단계 미확인: 개별 예제의 라이선스 사용 가능 여부·실제 실행 결과.

### 이해 확인

- 확인된 이해: 사용자가 첫 계산에 대해 “잘 나왔고, 이해했어”라고 응답했다. 음의 중력가속도와 양의 속도를 구분하는 설명을 수용한 상태로 기록하며 직접 서술한 답변은 없었다.
- A01-01 완료 근거: image(20261013-084409).png에서 한 행의 표, 속도 감소·위치 증가 그래프를 확인. 사용자가 초기 속도를 20 m/s로 변경했다. 원문 기본값 10 m/s와 차이를 기록했다.
- 검산: g=9.81 m/s², dt=0.01 s, p0=0 m이면 v1=19.9019 m/s, p1≈0.199019 m이며 화면은 반올림해 19.902·0.19902로 표시한다. 해당 값은 화면과 일치한다.
- 설명한 내용: 질점, 중력만 작용하는 모델, 위쪽 양의 좌표, 위치·속도·가속도, 속도 갱신 후 새 속도로 위치 근사. 이번 안내에서는 다음 값을 이전 값으로 넘겨 반복하는 구조를 설명한다.
- A01-02 완료 근거: 첨부 화면에서 Step 1~4 누적 표와 그래프 확인. v0=10 m/s 기준 검산 일치(Step 1: 9.9019, 0.099019 / Step 2: 9.8038, 0.19706 / Step 3: 9.7057, 0.29411 / Step 4: 9.6076, 0.39019). 사용자가 직접 서술: 중력가속도 때문에 속도는 줄고, 속도가 0이 될 때까지 위치는 위로 증가한다. 속도가 0이 되는 시점은 10/9.81≈1.02초로 계산(정답 1.0194초).
- A01-03 완료 근거: 첨부 화면에서 t_end = 2*v0/g → 2.0387, n_timesteps = ceil(t_end/dt) → 204 확인(검산 203.87→204 일치). 사용자 Reflect 답(주석): ‘204번. 203은 땅에 안 닿아서 안 됨. 정수여야 함. 한 번씩 진행하기 때문에 소수점은 나올 수 없음.’ 올림(ceil)이 반올림보다 안전한 이유(203.4처럼 내림되면 땅에 닿기 전에 끝남)는 설명으로 안내했다.
- A01-05 완료 근거: 사용자 보고(스크린샷 없음) — 위치가 0으로 돌아오는 시점 약 2.04초, 최고 높이 5 m 이상. 검산: t_end=2.0387초, 최고 높이 v0²/(2g)=5.097 m로 일치. dt 컨트롤 값 질문에는 답이 없었다.
- A01-06 완료 근거: 사용자 직접 설명 — ‘질량이 계산식에 없어서 변화가 없고, 힘을 질량으로 나누면 상쇄된다.’ F=−mg, a=F/m=−g 설명과 일치.
- A01-07 완료 근거: 사용자 예측(비행시간 2배, 최고 높이 약 20 m)과 첨부 그래프가 일치했다. v0=20에서 4.08초, 약 20.4 m, 속도 20→−20 m/s. 비행시간은 v0에 비례(2배), 최고 높이는 v0²에 비례(4배)함을 설명했다.
- A01-08 Try 3 확인: 사용자가 dt=1 그래프를 첨부하고 ‘dt가 커질수록 높이 측정이 불명확해지고 곡선이 선형으로 변한다. 속도 그래프는 크게 달라 보이지 않는다’고 설명했다. 화면: 점 3개(t=0,1,2), 위치 0→0.19→약 −9.4 m(땅 아래로 내려감), 속도 10→0.19→약 −9.6 m/s. 검산 일치(p=0.19, −9.43). 보충 설명: 속도는 등가속도라 선형이어서 오차가 거의 없고, 위치는 걸음 끝의 속도로 한 걸음씩 더해 오차가 쌓인다(오차 ≈ −g·dt·t/2, dt=1·t=2에서 −9.81 m). x축이 2에서 끝나는 것은 0:1:2.0387이 2까지만 만들기 때문이다.
- A01-08 완료 근거(Try 4): 사용자가 p0=−5 정상, −5.5 이하 오류를 찾고 오류 화면을 첨부했다(v0=9, p0=−5, dt=0.001: ‘Error using : Colon operands must be real scalars.’). 검산: 루트 안 값 81−98.1<0이라 tEnd가 복소수가 되어 colon 오류. 이유(땅 아래에서 출발해 땅 높이에 올라오지 못함)는 튜터가 설명했고 사용자의 재진술은 받지 않았다(사용자 요청으로 추가 질문 생략).
- A01-09 완료 근거: 사용자 보고 vx0=35.355, vy0=35.355(v0=50, angle=45). 검산 50·cos45°=35.3553로 일치. 사용자 코드는 보지 못했다. 사용자가 ‘왜 v0를 곱하는지, vx0·vy0가 무엇인지’ 질문 → 설명: cos·sin은 단위 없는 비율, v0를 곱해 m/s 성분이 되며, 속도는 크기와 방향을 가진 양이고 피타고라스로 50이 복원된다. 사용자 요청으로 추가 질문은 생략했다.
- A01-10 완료 근거: 첨부 화면의 코드(tEnd=(vy0+sqrt(vy0^2+2*g*y0))/g, vx(i)=vx(i-1), vy(i)=vy(i-1)-g*dt, x(i)=x(i-1)+vx(i)*dt, y(i)=y(i-1)+vy(i)*dt)와 x–y 궤적 확인. v0=50, 45도: 사거리 약 255 m(검산 v0²·sin2θ/g=254.8 m), 최고 높이 약 63.7 m(검산 vy0²/(2g)=63.7 m)로 일치.
- A01-11 완료 근거: 첨부 화면 — 모델 구성(Constant −9.81, 적분기 2개, 라벨 a·v·p, Scope 2입력, 위치 p→Hit Crossing(falling)→Stop Simulation)과 Scope 결과: 정지 T=10.3899 s, 최고 높이 약 137 m, 시작 p(0)=10·v(0)=50 확인. 검산 t_end=(50+√(50²+2·9.81·10))/9.81=10.3899 s로 일치. Stop time 15·Max step 1e-2 설정값은 화면에서 직접 확인하지 못했다(축은 0~15).
- A01-12 완료 근거: Gain 0.1(α=0.1)로 수정한 모델 화면과 Scope 확인. 사용자 보고 정지 약 4.75 s, 최고 약 26.5 m, 속도 약 −10 m/s 수렴. 수치 검산(4.751 s, 26.38 m, 종단 −9.9 m/s)과 일치. Reflect 답: 속도는 직선에서 곡선(수렴)으로, 위치는 훨씬 낮게, 항력 계수를 키우면 더 낮게(α=1 실행에서 약 13 m로 확인), 땅 도달 약 4.75 s(항력 없음 10.39 s).
- A01-04 완료 근거: 사용자 설명 — v0=50, p0=10, g=9.81에서 a=−g/2, b=v0, c=p0로 놓고 근의 공식에 대입해 −0.2초와 10.4초를 얻었고, 음수 시간은 불가능해 10.4초를 선택했다. 검산: −0.196, 10.390으로 일치하며 Simulink 정지 시각 10.3899와 같다. 교재의 ‘독자 연습’은 문자 식 유도이며, 문자 전개 t=(v0±√(v0²+2g·p0))/g와 양의 근 선택 근거(√≥v0이므로 −는 0 이하)는 튜터가 보충했다. 사용자의 수치 대입 풀이로 인정했다.
- A02-01 완료 근거: 첨부 화면 — pcread('teapot.ply')와 pcshow로 찻주전자 점군과 X·Y·Z 축(−5~5) 표시를 확인했다.
- A02-02 완료 근거: 첨부 화면 3장 — tform1 후 찻주전자가 x 약 2·y 약 −3·z 4~6 부근으로 이동·기울어짐, tform2 후 x 4~8·z 1~4로 이동·회전, tform3 후 다시 회전. 사용자 설명: x, y, z 순서대로 회전했고 이전 상태가 이어져 회전했다. 보충: tform2·tform3은 원점 기준 회전이라 이동된 물체의 위치도 함께 바뀐다(대략 검산: 중심 (2,−3,4)→(4.2,−3,1.4)→(4.7,2.2,1.4)).
- A02-03 완료 근거: 사용자가 전체 변환 그림을 첨부하고 순차 변환 마지막(tform3 후)과 다르다고 관찰했다. 전체 변환은 찻주전자가 대략 (2,−3,4) 부근, 순차 결과는 x 4~6·y 1~5·z 1~4 부근으로 위치가 다르다. 이유는 튜터가 설명했다: tform1에만 이동이 있고 이후 tform2·tform3의 원점 기준 회전이 이동된 위치를 다시 옮기며, 전체 변환은 회전 후 이동이 한 번 적용된다. 회전 합성 순서·관례(교재의 외재/내재 설명)도 방향 차이에 영향을 준다.
- A02-04 완료 근거: 사용자가 tform1과 tform3의 회전을 교체(tform1=z축 60° + 이동 [x y z], tform3=x축 30°)해 순차 변환을 다시 실행했고 ‘마지막 결과가 전체 변환과 같게 나왔다’고 관찰했다. 첨부 화면에서 모양(방향)은 전체 변환과 같지만 좌표축은 달라(순차 x 4~6·z −1~2, 전체 z 3~6) 위치는 다르다. 이유: 이동 [x y z]가 tform1에 남아 처음 적용된 뒤 y·x축 회전에 함께 돌아갔다(대략 (4.2,−3.3,−0.3)). 이동까지 tform3으로 옮기면 위치도 일치할 것이다. 회전을 z→y→x 순서(고정 축)로 적용한 결과가 교재 rigidtform3d의 x,y,z 합성과 같은 방향을 준다는 것을 확인했다.
- A02-05 완료 근거: 사용자가 x_rot=180°로 찻주전자를 뒤집어 전체 변환 그림에서 위아래가 거꾸로 보임을 확인했다. 순차 변환(tform1·2·3)으로는 프레임 밖으로 나갔으나 전체 변환(ptCloudOut)에서는 나가지 않는다고 보고했다. 설명: 전체 변환은 회전 후 이동이라 최종 중심이 이동값 [x y z] 그대로이므로 값이 ±5 안이면 프레임 안에 있고, 순차 변환은 이동이 이후 원점 기준 회전에 같이 돌아 위치가 달라진다. 프레임 밖은 이동값 절댓값이 약 6 이상이면 가능하다. 참고: 교재 하단 helper rotationMatrix는 Rx*Ry*Rz(z→y→x 순)이며 본문의 R=Rz·Ry·Rx 표기와 다르다(교재 내부 불일치, 코드 기준).
- A02-06 완료 근거: 사용자가 경로(linspace 6개)와 for 안의 idx번째 rigidtform3d·pctransform으로 애니메이션을 완성했다(최종 코드 화면 확인). 마지막 값(회전 180·90·90, 이동 3·−3·3)에서 disp(mean) 결과 c=(0.0372, 0, 1.7251), 마지막 중심 (4.7251, −3.0372, 3.0). 튜터 검산: Rz90→Ry90→Rx180 순 적용 R·c=(1.7251, −0.0372, 0), +t=(4.7251, −3.0372, 3.0)로 일치(점군 중심이 원점에서 z 방향으로 1.7251 떨어져 있음). Reflect 답변: 매 시간 단계마다 투사체 운동 방정식으로 위치(Translation), 회전 운동 방정식으로 회전각을 계산해 rigidtform3d에 함께 전달해 위치와 방향 변환을 동시에 적용한다.
- A02-07 완료 근거: 첨부 화면 — 6DOF (Euler Angles) 블록의 입력은 F_xyz(N)(Fx·Fy·Fz 슬라이더)와 M_xyz(N·m)(롤·피치·요 모멘트와 Mxx·Myy·Mzz 슬라이더), 출력은 V_e(m/s)·X_e(m)·φθψ(rad)·DCM_be·V_b(m/s)·ω_b(rad/s)·dω_b/dt·A_bb(m/s²). Inertial·Body Scope에 속도·위치·오일러각·몸체 회전율이 표시됨. Return Here 실행했다고 보고.
- A02-08 완료 근거: 사용자가 QuaternionExample을 실행해 모두 확인했다고 보고하고 코드 eul3=[0 89 0], eul4=[180 89 180], qdist3 = quaternion(deg2rad(eul3),'euler','ZYX','frame')을 제시했다(출력 화면은 보지 못함). 단위: 각도를 도로 적고 deg2rad로 라디안 변환, 회전 순서 ZYX, frame 회전. 튜터 검산: 두 오일러각은 (180°,0°,180°) 차이로 크게 달라 보이지만 피치 89° 부근이라 실제 회전 차이는 약 2°이다.
- A03-01 완료 근거: 첨부 화면 — omega_hover = sqrt(M*g/(4*k_T)) = 351.4827 rad/s, CheckEx1 ‘Correct! The calculated hover speed matches the expected value. The propeller needs to be rotating at approximately 351 rad/s or 3356 rpm.’ 호버링 조건 4·kT·ω²=M·g에서 도출. 사용자의 total_propeller=M*g*4(21.1896)는 잘못된 계산이며 사용되지 않았다(무게는 M·g 하나이고 프로펠러 한 개는 M·g/4를 낸다). 단위: 3단원은 rad/s, 이후 단원은 회/분 기반 kT가 나오므로 혼용 주의.
- A03-02·A03-03 완료 근거: 첨부 화면 — CheckEx2("increases","a") ‘Correct.’, CheckEx2("decreases","b") ‘Correct.’ 및 ‘This dependence on radial distance is why forward-flight propellers must be twisted.’ 사용자 설명: x가 허브에 가까울수록 분모 ωx가 작아져 tan(φ)가 커지고(φ 증가), 끝 쪽은 반대(φ 감소). 보충: 허브에서는 축 방향 유입이 지배해 φ가 90°에 가깝고 끝에서는 회전 속도가 지배해 φ가 0°에 가까워, 전진 비행 프로펠러는 반지름에 따라 피치각을 비틀어야 한다.
- A03-04 완료 근거: 사용자 Reflect 답 — 추력/토크 비율이 거의 100배이고 그래프 차이는 k_T와 k_m 값의 차이 때문(정확히 1.8e-5/2.0e-7=90배). 보충: T=k_T·ω², Q=ε·k_m·ω²로 ω에 대한 제곱 의존성은 같아 ω가 2배면 둘 다 4배, 비율 T/Q=90은 ω와 무관. 단위가 N과 N·m로 달라 절대 크기보다 비율로 비교한다. 수치(튜터 계산): ω=900에서 T=14.58 N, Q=0.162 N·m. 사용자의 그래프 화면은 보지 못했다.
- A03-05 완료 근거: 첨부 모델 화면 — Constant(omega=900, Km=2e-7, eps=1, kT=1.8e-5), ω에서 분기해 u²(제곱) 블록 2개, 토크용 Product(ω², Km, eps) 3입력, 추력용 Product(ω², kT) 2입력, Display Q=0.162, T=14.58. 튜터 계산 T=1.8e-5×900²=14.58 N, Q=2e-7×900²=0.162 N·m와 일치. 사용자가 MATLAB 함수 SimplePropellerModel 결과와 직접 비교했는지는 확인하지 못했다.
- A04-01 완료 근거: 사용자 답 — Mquad=1.3 kg(=4×0.07+1.02 일치), +형 프로펠러 1(0.13,0,0) 2(0,0.13,0) 3(−0.13,0,0) 4(0,−0.13,0). 좌표의 R=0.13 m는 교재 관성 셀의 Rval 값이며, 이 좌표 계산 과제는 튜터가 덧붙인 것(교재 기하 셀은 질량 코드만 있음). 회전 방향 1·3 반시계, 2·4 시계는 교재 설명.
- A04-02 완료 근거: 첨부 화면 — M=1.3000 kg, I=diag(0.0061, 0.0061, 0.0117) kg·m², Ixx=0.0061, Iyy=0.0061, Izz=0.0117. 튜터 검산(교재 코드 수식): 프로펠러 Ixx=4·(¼·m·r²)+2·m·R²=3.374e-3, 몸체 Ixx=(1/12)·Mbody·(L²+H²)=2.7625e-3, 합 6.14e-3 / Izz=프로펠러 6.748e-3+몸체 4.913e-3=1.166e-2로 일치. 사용자의 해석 설명은 아직 없음(결과 제출만 확인).
- A04-03 완료 근거: x형 실행 결과 화면(Ixx=Iyy=0.0061, Izz=0.0117, + 형과 동일) 및 사용자 Reflect 답 — '바뀌는 것은 pB 좌표와 Ibody 회전'. 튜터 보충: 대칭 때문에 이 모델에서 관성 수치는 두 형상이 같고, 형상은 pB(프로펠러 위치)와 몸체 45° 회전 유무로만 반영됨. 화면에서 configuration="x" 설정 여부는 확인 불가.
- A04-04 완료 근거: 첨부 화면 — pB 드롭다운 'x configuration'으로 A 계산: 행1 [kT kT kT kT], 행2 [σ −σ −σ σ], 행3 [σ σ −σ −σ], 행4 [km −km km −km], σ=√2·R·kT/2, [T;Qx;Qy;Qz]=A·[ω1²..ω4²]. 튜터 예측과 일치. 사용자 Reflect 답: '모든 프로펠러를 같은 방향으로 돌리면 기체가 요 회전을 한다'(맞음; ε가 모두 같으면 Qz=km(ω1²+…+ω4²)로 반작용 토크가 상쇄되지 않음). 입력이 ω²이고 행별 단위(T[N], Qx·Qy·Qz[N·m])는 튜터가 설명했으며 사용자 서술은 아님. 정정: 교재 셀의 pB는 드롭다운으로 배치를 선택(이전에 '항상 x형'이라 한 튜터 설명은 틀림).
- A04-05 완료 근거: 첨부 화면 2장 — 드롭다운 'x configuration'과 '+ configuration'에서 각각 A 계산. +형: 행1 [kT kT kT kT], 행2 [0 −R·kT 0 R·kT], 행3 [R·kT 0 −R·kT 0], 행4 [km −km km −km]. x형은 행2·3의 0이 없고 모든 성분이 ±σ(=√2·R·kT/2). 행1·행4(총추력·요)는 배치와 무관. 튜터 예측과 일치. 사용자는 '둘다 확인했어'라고 보고했으며 부호 패턴 해석은 튜터가 설명했다(사용자 서술 아님).
- A04-06 완료 근거: 첨부 화면 — W=12.7530, T_prop=3.1883, N=4000, kT=1.9927e-07, km=1.9927e-09. 튜터 검산 W=(1.02+0.28)·9.81=12.753 N, T_prop=W/4=3.18825 N, kT=3.18825/4000²=1.99266e-7 N/rpm², km=0.01·kT 일치. 튜터 보충: rad/s 환산 kT=kT_rpm·(60/2π)²≈1.817e-5(3단원 값 1.8e-5와 같은 크기). 단위(N/rpm², N·m/rpm²)는 튜터가 설명, 사용자 서술 아님.
- A04-07 완료 근거: 첨부 화면 — 두 셀(N 스윕·subplot 그래프) 실행, 추력 그래프는 0~약 20 N, 모멘트 그래프는 0~약 0.2 N·m의 포물선형 곡선. 튜터 검산: 10000 rpm에서 T=kT·1e8≈19.93 N, M≈0.199 N·m 일치. 4000 rpm 값(T=3.1883 N, M≈0.0319 N·m)은 사용자가 보고하지 않았고 튜터 계산값이다.
- A04-08 완료 근거: 첨부 화면 — quad_m 4×4(×1e-6; 행1 0.1993, 행2 [0.0183 −0.0183 −0.0183 0.0183], 행3 [0.0183 0.0183 −0.0183 −0.0183], 행4 [0.0020 −0.0020 0.0020 −0.0020]), f=[12.7530;0;0;0], f(1)−W=0. 사용자 Reflect 답: '배치가 바뀌면 quad_m의 롤·피치 행이 바뀌고(0이 들어감) 호버링 f는 그대로, 호버링 시 합이 0이 되기 때문' — 맞음(+형에서는 롤·피치 행에 0이 들어가고 총추력·요 행과 f는 동일).
- A04-09 완료 근거: 사용자가 Save the Parameter Values 셀을 실행하고 '저장했어'라고 보고. 생성된 파일 이름(코드상 x형이면 x_quad_params.mat)·경로 메시지·저장 변수는 사용자가 보고하지 않아 확인하지 못했다. 5단원에서 파일을 불러올 때 존재 여부를 확인한다.
- A05-01 완료 근거: 사용자가 w=[4000 4000 4000 4000] 실행 후 UAV Animation에서 호버링(Up 0 근처, 궤적 점)을 확인(X형 선택). 균형은 4단원 결과(f(1)−W=0, 모멘트 0)로 확인. 사용자 서술 설명은 없음.
- A05-02 완료 근거: 4025 rpm 약 +8 m 상승, 3975 rpm 약 −8 m 하강(첨부 화면). 추력∝ω²(4025는 1.0126배, 순힘 약 0.16 N). 원인 설명은 튜터가 했고 사용자 서술은 없음. 실행 시간은 Scope 가로축 0~10초.
- A05-03 완료 근거: X형에서 앞 프로펠러 1·2, 뒤 3·4(mixer 행3 [σ σ −σ −σ]와 실험으로 확정). w=[4000 4000 4025 4025]에서 North(+) 약 40 m 이동. 처음 w=[4025 4000 4000 4025]를 전진으로 보았으나 East(+) 이동으로 roll임이 확인됨(사용자가 두 조합의 방향을 직접 실험해 정리). 힘 Scope(Fx 0→4.6 N, Fy 0, Fz −0.08→−0.93 N)로 10초 시점 θ≈−21°(−0.37 rad)를 튜터가 역산. 사용자 원인 답: 한쪽 프로펠러 출력이 계속 높아 호버링을 하며 이동하지 못하고 유지할 수 없어 떨어진다. 튜터 보완: 일정한 모멘트가 각가속도를 만들어 각도가 시간의 제곱으로 커지는데 기울기를 되돌리는 제어기가 없음.
- A05-04 완료 근거: X형 w=[4025 4000 4000 4025] 실행에서 East(+) 약 40 m 이동(첨부 화면, 이전 대화). 1·4번을 올리면 mixer 행2(Qx) 양의 모멘트로 오른쪽 roll이 됨. φ 부호는 큰 Scope 범례를 켜지 않아 직접 확인하지 못했고, 반대 입력의 힘 Scope(Fy<0)로 부호를 추정했다. 왼쪽 입력 w=[4000 4025 4025 4000]은 East −40 m, Fx 0, Fy 0→−4.6 N, Fz −0.08→−0.93 N(10초 시점 기울기 약 21°)으로 오른쪽과 대칭이다. 이 왼쪽 결과는 A05-05에 사용한다.
- A05-05 완료 근거: 왼쪽 roll 입력 w=[4000 4025 4025 4000]에서 East −40 m, Fy −4.6 N(오른쪽 roll과 대칭). Reflect 사용자 답: 1번만 올리면 x형은 roll과 pitch 둘 다 +, +형은 pitch만 +. mixer 행(x형 [σ −σ −σ σ]·[σ σ −σ −σ], +형 [0 −R·kT 0 R·kT]·[R·kT 0 −R·kT 0])과 일치.
- A05-06 완료 근거: 반시계 w=[3975 4025 3975 4025]에서 힘 Scope Fx·Fy≈0, Fz≈−5×10⁻⁴ N이고 큰 Scope의 파란 선이 −0.08(계산 ψ=½·(Qz/I)·t²=−0.080 rad와 일치, 범례 미확인). 시계 w=[4025 3975 4025 3975]에서 +0.08. 총추력 비 sum(w.^2)/(4*4000^2)=1.0000(정확히 1.0000391). 시계 Fz 축 숫자(−89.67×10⁻⁴)가 반시계(−49.8×10⁻⁵)와 달라 보이나 원인 미확인(둘 다 0에 가까움). 사용자 Reflect 답: 시계는 ψ가 +로 바뀜(올리는 쌍을 바꿈).
- A06-01 완료 근거: load x_quad_params.mat kT quad_m W M g 실행(kT=1.9927e-07, M=1.3, W=12.753, g=9.81, 오류 없음, 4단원 저장 파일에 변수 모두 존재). 추력 곡선 그래프(가로 Speed rpm 0~10000, 세로 Thrust N 0~20, 10000 rpm 약 20 N) 제출. 원문에는 이 구간의 Try·Exercise·Reflect 질문이 없다. 튜터가 비선형 곡선·가속도 부호·투사체와의 차이를 설명했다(사용자 요청).
- A06-02 완료 근거: 사용자가 모델 화면 제출 — set altitude 20 → Sum(+ −) → e → PID Controller → prop_speed → Subsystem(altitude) → measurement → Sum 피드백, 오른쪽 Scope·Mux 연결 확인. Initialization 탭에서 소스 내부, 적분기 4000, 필터 0 확인. 구조는 튜터가 원문 .slx 내부를 읽은 것과 일치(안쪽: prop_speed→제곱→×kT→×4=thrust, M→×g=gravity, Sum(+ −)→×1/M→a→적분→z′→적분→z). PID 이득은 기본값(A06-03에서 설정).
- A06-03 완료 근거: P=80, I=0, D=0 Scope 화면 제출(0~60초). altitude:1(노랑)=목표 20, altitude:2(파랑)=실제 고도가 0~약 43 m를 주기 약 10초로 진폭 감소 없이 진동. prop_speed 약 2200~5600 rpm(시작 5600), thrust 시작 약 25 N. 튜터 예측(5600 rpm, 25 N, 주기 약 10초=2π√(M/k), k=P·8·kT·4000≈0.51 N/m)과 일치. 위쪽 43 m는 추력이 속도 제곱에 비례하는 비선형성 때문(아래 +12.2 N, 위 −8.2 N)으로 설명. 감쇠 요소가 없어 진폭 유지.
- A06-04 완료 근거: P=120, I=0, D=40 Scope 화면 제출. 고도가 약 60 m 첫 고점 후 감쇠 진동(약 8초 주기)하며 약 40초 이후 20 m 근처 정착(눈대중). prop_speed 축 ×10³ 약 90, thrust 축 약 6000 N: t=0 목표 점프에 대한 미분 킥(D·N·e=40·100·20=80,000 rpm +6400, 필터 계수 기본 100, 지속 약 0.01 s, 튜터 근사 속도 약 20 m/s)이 원인. P=80 대비 진폭 감소는 D가 속도 비례 감쇠 역할을 하기 때문(튜터 근사 ζ≈0.13, 주기 약 8.3초). 사용자 서술 설명은 없음.
- 튜터 정정(5단원): Scope 해석 중 ‘θ가 −90°를 넘어 뒤집힘’은 틀린 설명이었다. 큰 Scope(V_e, X_e, φθψ, q 혼합 축)의 하늘색 선(약 −1.8)은 범례 미확인으로 정체 불명이다.
- 보충 후보: 시간 간격, 속도·가속도, 수치 적분, 좌표계·회전행렬, 힘·토크, 관성, 피드백, 제어기 각 항. 이해 상태를 추정해 완료 처리하지 않는다.

## 10. 다음 수업과 업데이트 규칙

1. A01-05: Simulate & Plot 버튼으로 1D 코드를 직접 실행한 결과 확인 → A01-04(독자 연습 유도) → Try 4문항(A01-06~A01-08).
2. 준비 확인 후 `Scripts/ProjectileMotion.mlx`의 Free Fall / Numerical Approximation으로 시작한다.
3. 최초 계산 실습 위치는 A01-01: Set Up Variables 및 한 시간 간격 계산. 전체 스크립트를 Run All로 실행하도록 안내하지 않는다.
4. 매 수업은 현재 위치·진행률 → 배울 내용 → 핵심 개념·단위·좌표 → 실습 한 단계 → 결과 확인·이해 확인 순서로 진행한다.
5. 사용자의 결과를 확인한 후에만 다음 실습으로 이동한다. 오류가 있으면 진도를 멈추고 오류를 먼저 해결한다.
6. 수업 종료 시 실제 완료 ID, 결과/설명 근거, 파일명, 문제·해결, 현재 섹션과 다음 행동을 갱신한다. 완료 수를 다시 계산해 최신 파일을 제공한다.
7. 새 대화에서 이 파일을 읽고 기록된 위치·분모를 유지한다. 기록에 없는 완료 상태를 추측하지 않는다.
8. 사용자가 “학습 인계서 작성해 줘”라고 요청하면 교재·환경·완료 ID·현재 위치·두 진행률·실제 파일·이해/보충·미해결 오류·다음 실습·전체 진도표를 이 기록과 대조해 작성한다.

9. 원문 우선 규칙: 교재 문제는 GitHub 저장소 원문(release 61167f7)을 직접 읽어 그대로 진행한다. 튜터가 만든 추가 과제는 ‘추가(선택)’로 표시하고 진행률 분모·분자에 넣지 않는다. 사용자가 원문 캡처를 매번 보낼 필요는 없고, 사용자의 실행 결과·오류만 요청한다.

9-1. 사용자 선호(2026-10-21): 과제·질문은 교재 원문의 Try·Exercise·Reflect만 낸다. 튜터 추가 계산·질문은 하지 않거나 ‘추가(선택)’로만 표시하고 생략해도 된다. 설명은 원문 순서대로 해 준다.
9-2. 사용자 선호(2026-10-21): 모든 단계에서 추가 설명을 많이 한다. 원문에 나온 내용(원문 순서·식·그림·코드의 의미), 결과가 그렇게 나온 이유(수치 검산·물리적 원인), 이전 단원·투사체와의 연결, 흔한 오해, 이후 제어와의 연결 등 여러 방면으로 자세히 풀어서 이해하며 진행하게 한다. 실행 결과만 받고 넘어가지 않는다. 과제·질문은 9-1대로 원문 것만 낸다.

10. 단원 총정리 규칙: 한 단원의 모든 체크포인트가 완료되면 다음 단원으로 넘어가기 전에 총정리를 한다. 내용은 (1) 단원에서 배운 핵심 개념·식·단위, (2) 실제로 만든 파일·변수·결과 값, (3) 교재와 튜터 설명이 다른 점·주의사항, (4) 다음 단원과의 연결이다. 답변에 요약하고 이 파일의 ‘12. 단원 총정리’에 같은 내용을 추가한다. 새 대화에서도 동일하게 적용한다.

## 11. 수업 기록

| 날짜 | 수행 내용 | 실제 완료 ID | 수업 종료 진행률 | 다음 위치 |
|---|---|---|---|---|
| 2026-10-13 | 교재 파일 조사, 진도표와 제작 기준 구성. 사용자 실습 없음 | 없음 | 교재 0/79=0%, 제작 0/20=0% | E00 준비 시작 전 |

| 2026-10-13 | 첨부 ver 화면에서 설치 제품 32개와 운영체제 확인. UAV.prj 열기 안내, 결과 대기 | 없음 | 교재 0/79=0%, 제작 0/20=0% | E00: 프로젝트 열기 대기 |

| 2026-10-13 | 첨부 화면에서 UAV.prj 및 StartUp App 정상 열림 확인. 첫 단원 Live Script 열기 안내, 결과 대기 | 없음 | 교재 0/79=0%, 제작 0/20=0% | ProjectileMotion.mlx 열기 대기, A01-01 실행 전 |

| 2026-10-13 | 첨부 image(20261013-081601).png에서 첫 단원 정상 열림 확인. 자유낙하 모델과 한 시간 간격 계산 설명, 첫 섹션 실행 안내 | 없음: A01-01 진행 중 | 교재 0/79=0%, 제작 0/20=0% | Set Up Variables 실행 결과·이해 확인 대기 |

| 2026-10-13 | 첫 간격 표·그래프 및 사용자 이해 확인. v0=20 m/s 변경 확인. 반복 갱신 섹션 3회 실행 안내 | A01-01 | 교재 1/79=1.3%, 제작 0/20=0% | A01-02 실행 결과 대기 |

| 2026-10-13 | Step 2 고정 문제 보고. 첨부 표·그래프에서 두 번째 간격 결과 확인. 전체 초기화 가능성 설명 및 반복 섹션 Run Section 한 번 안내 | 추가 완료 없음 | 교재 1/79=1.3%, 제작 0/20=0% | Step 3 추가 여부 확인 대기 |

| 2026-10-13 | Step 1~4 누적 표·그래프 확인(v0=10 m/s 검산). 속도·위치 변화 설명과 속도 0 시점 1.02초 확인 | A01-02 | 교재 2/79=2.5%, 제작 0/20=0% | A01-03 원문 확인 대기 |

| 2026-10-13 | A01-03 원문 화면 확인. 사용자가 직접 생각한 답 204를 제시(풀이 없음, 확신 없음). 검산 결과 203.87→204로 일치. t_end=2v0/g와 n=t_end/dt 설명 | 추가 완료 없음 | 교재 2/79=2.5%, 제작 0/20=0% | n_timesteps 직접 계산·정수 여부 답변 대기 |

| 2026-10-13 | 사용자가 t_end=2.0387, n_timesteps=203.8736 실행. Reflect 답을 코드 셀에 한글로 입력해 Invalid text character 오류 발생. 오류 원인과 해결 방법(% 주석) 안내 | 추가 완료 없음 | 교재 2/79=2.5%, 제작 0/20=0% | 오류 해결 후 Reflect 확정, A01-03 완료 처리 |

| 2026-10-13 | 오류를 %로 해결하고 n_timesteps = ceil(t_end/dt) → 204 확인. Reflect 직접 답변 확인 | A01-03 | 교재 3/79=3.8%, 제작 0/20=0% | A01-04 원문 화면 확인 대기 |

| 2026-10-13 | 원문을 GitHub 저장소에서 직접 확인(61167f7). 사용자가 A01-04 안내 중 일부(근 선택·v0=50/p0=10 수치 계산)가 원문에 없는 추가 과제임을 지적. 원문은 ‘Details are left as an exercise to the reader.’ 문장과 Try 4문항(m·v0·dt 변경, MATLAB 오류). 사용자 화면의 dt 컨트롤은 0.001 | 추가 완료 없음 | 교재 3/79=3.8%, 제작 0/20=0% | 사용자가 Simulate & Plot을 직접 실행한 결과 대기 |

| 2026-10-13 | 사용자가 1D 코드를 실행해 비행시간 약 2.04초·최고 높이 5 m 이상 보고(검산 일치). m을 바꿔도 변화 없는 이유를 질문하여 설명(m이 계산식에 없음, F=−mg를 m으로 나누면 상쇄) | A01-05 | 교재 4/79=5.1%, 제작 0/20=0% | 사용자의 질량 설명(A01-06) 확인 후 Try v0 |

| 2026-10-13 | 사용자가 질량 설명 직접 제출(계산식에 m 없음, 힘을 질량으로 나누면 상쇄). v0 20 예측: 비행시간 2배, 최고 높이 약 20 m(검산 일치, 높이는 v0의 제곱에 비례해 4배) | A01-06 | 교재 5/79=6.3%, 제작 0/20=0% | v0=20 실제 그래프 확인·‘왜’ 설명 대기 |

| 2026-10-13 | v0=20 그래프 첨부(속도 20→−20, 최고 약 20.4 m, 4.08초). 예측과 일치. 비행시간은 v0에 비례, 최고 높이는 v0²에 비례하는 이유 설명 | A01-07 | 교재 6/79=7.6%, 제작 0/20=0% | Try 3(dt 변경) 결과 대기 |

| 2026-10-13 | dt=1 그래프 첨부와 설명(위치 곡선이 선형으로, 속도는 거의 그대로). 끝점이 0 아래(약 −9.4 m)로 내려가는 점과 이유 보충 | 추가 완료 없음(A01-08 진행 중) | 교재 6/79=7.6%, 제작 0/20=0% | Try 4 오류 조건 탐색 대기 |

| 2026-10-13 | Try 4: 사용자가 p0=−5까지 정상, −5.5부터 오류, 음수 p0에서 음수 v0도 오류라고 보고. 경계 −v0²/(2g)=−5.1 m와 일치. 물리적 이유(땅 아래에서 출발해 땅 높이에 못 올라옴) 설명 | 추가 완료 없음(A01-08 진행 중) | 교재 6/79=7.6%, 제작 0/20=0% | 오류 메시지 문구와 사용자 설명 확인 대기 |

| 2026-10-13 | 오류 화면 첨부(v0=9, p0=−5, dt=0.001: Colon operands must be real scalars). 루트 안 값 음수로 tEnd가 복소수가 된 것으로 확인. 사용자 요청으로 추가 질문 없이 A01-08 완료 처리, 2D Exercise 1 안내 | A01-08 | 교재 7/79=8.9%, 제작 0/20=0% | Exercise 1 코드 결과 대기 |

| 2026-10-14 | Exercise 1 결과 보고(vx0=vy0=35.355, v0=50, angle=45)와 ‘왜 v0를 곱하는가, vx0·vy0는 무엇인가’ 질문. 설명 후 Exercise 2 골격 안내 | A01-09 | 교재 8/79=10.1%, 제작 0/20=0% | Exercise 2 코드·궤적 그래프 대기 |

| 2026-10-14 | 튜터 골격의 `...`(MATLAB 줄 이음 기호)와 `==` 때문에 난 오류를 정리하고, 사용자가 4개 빈칸을 직접 채워 실행. 궤적 그래프 확인(사거리 약 255 m, 최고 약 63.7 m). 사용자 코드·그래프 확인 | A01-10 | 교재 9/79=11.4%, 제작 0/20=0% | Projectile_1D.slx 구성 1단계(적분기·Scope) 결과 대기 |

| 2026-10-14 | Projectile_1D 1단계 모델 화면 확인. 신호 라벨 위치 어긋남과 Scope 입력 2 미연결을 지적. Hit Crossing·Stop Simulation·시간 설정·실행 안내 | 추가 완료 없음(A01-11 진행 중) | 교재 9/79=11.4%, 제작 0/20=0% | 완성 모델과 Scope 실행 결과 대기 |

| 2026-10-14 | 사용자가 모델 화면과 교재 ‘Adding Drag’ 화면을 함께 첨부하고 ‘교재대로 가르치는 게 맞는가’ 질문. 답변: 순서와 Try·Exercise·Reflect 문항은 교재, 체크포인트 ID·진행률·보충 설명·Exercise 2 골격·Simulink 단계 분할은 튜터 추가임을 구분해 안내. 모델의 Hit Crossing이 v에 연결된 점과 Stop Simulation 누락 지적 | 추가 완료 없음(A01-11 진행 중) | 교재 9/79=11.4%, 제작 0/20=0% | Hit Crossing를 p에 연결, Stop Simulation 추가, 시간 설정, 실행 결과 대기 |

| 2026-10-14 | 모델 수정과 실행 결과 확인(정지 T=10.3899 s, 최고 약 137 m, p(0)=10·v(0)=50). 검산 일치. 교재 항력 단원 모델 내부 지침(1D 모델 복사 → 항력 하위 구성 → 연결) 확인 후 안내 | A01-11 | 교재 10/79=12.7%, 제작 0/20=0% | 항력 모델 구성 화면·Scope 결과 대기 |

| 2026-10-14 | 항력 모델 화면 확인: 블록 구성·연결은 맞으나 Gain이 1(α=1)로 남아 있음. Scope T=4.7809 s·최고 약 13 m가 α=1 수치 검산(4.781 s, 12.77 m)과 일치. Gain을 0.1로 고치도록 안내 | 추가 완료 없음(A01-12 진행 중) | 교재 10/79=12.7%, 제작 0/20=0% | α=0.1 재실행 결과와 Reflect 3문항 대기 |

| 2026-10-14 | Gain 0.1로 수정한 항력 모델 확인(정지 약 4.75 s, 최고 약 26.5 m, 속도 약 −10 m/s로 수렴). Reflect 3문항 답변(속도 직선→곡선, 위치 훨씬 낮게, 항력 계수 키우면 더 낮게, 땅 도달 약 4.75 s) | A01-12 | 교재 11/79=13.9%, 제작 0/20=0% | A01-04 유도 시작 |

| 2026-10-14 | A01-04: 사용자가 v0=50, p0=10, g=9.81을 a,b,c에 대입해 근의 공식으로 −0.2초와 10.4초를 구하고 양수 근을 선택. 문자 식 전개와 근 선택 근거는 튜터가 보충. 1단원 완료. 교재 RigidTransforms 원문 확인 후 2단원 시작 안내 | A01-04 | 교재 12/79=15.2%, 제작 0/20=0% | A02-01 점군 표시 결과 대기 |

| 2026-10-15 | A02-01: 첫 섹션 실행 결과(찻주전자 점군, X·Y·Z 축 −5~5) 확인. 교재 변환 셀 구성 확인 후 A02-02 안내 | A02-01 | 교재 13/79=16.5%, 제작 0/20=0% | A02-02 순차 변환 결과 대기 |

| 2026-10-15 | A02-02: 순차 변환 3장 확인(tform1 후 x 약 2·y 약 −3·z 4~6, tform2 후 x 4~8·z 1~4, tform3 후 y·z 방향으로 이동). 사용자가 ‘x,y,z 순서로 회전했고 이전 상태가 이어져 회전했다’고 설명. 원점 기준 회전이라 위치도 함께 이동함을 보충 | A02-02 | 교재 14/79=17.7%, 제작 0/20=0% | A02-03 전체 변환 결과와 순차 결과 비교 대기 |

| 2026-10-15 | A02-03: 전체 변환 그림 확인(찻주전자가 x 약 2·y −5~−2·z 3~6 부근). 사용자가 ‘tform3 결과와 다르다’고 관찰. 이유 설명(순차 변환은 이동된 뒤 원점 기준 회전이 이어져 위치가 달라지고, 전체 변환은 회전 후 이동 + 회전 합성 순서·관례 영향) | A02-03 | 교재 15/79=19.0%, 제작 0/20=0% | Try 1(tform1·tform3 교체) 결과 대기 |

| 2026-10-15 | A02-04: 사용자가 tform1·tform3의 회전을 교체해 실행(이동 [x y z]는 tform1에 남음). 순차 결과의 모양(방향)이 전체 변환과 같다고 관찰. 위치는 이동이 처음에 적용되어 달라짐(대략 (4.2,−3.3,−0.3) vs (2,−3,4))을 설명. Try 2 슬라이더 안내 | A02-04 | 교재 16/79=20.3%, 제작 0/20=0% | A02-05 슬라이더 실험 결과 대기 |

| 2026-10-15 | A02-05: x축 180°로 찻주전자 뒤집기 확인. 순차 변환(tform1·2·3)에서는 프레임 밖으로 나갔으나 전체 변환(ptCloudOut)에서는 나가지 않는 이유(전체 변환은 최종 위치가 이동값 그대로, 순차 변환은 이동이 회전에 같이 돌아감)를 설명. 교재 helper rotationMatrix는 Rx*Ry*Rz임을 확인. A02-06 안내 | A02-05 | 교재 17/79=21.5%, 제작 0/20=0% | A02-06 애니메이션 코드 결과 대기 |

| 2026-10-15 | A02-06 코드 화면 확인: 끝점 값(x_rot 180, y_rot 0, z_rot 90, 이동 1,−1,1)과 tform·tform1~3만 정의되어 있고 linspace 경로와 for 안의 pctransform은 아직 없음(ptCloudOut = ptCloud 그대로라 움직이지 않음). 경로 정의와 반복문 작성 방법 안내 | 추가 완료 없음(A02-06 진행 중) | 교재 17/79=21.5%, 제작 0/20=0% | 완성한 애니메이션 코드와 실행 결과 대기 |

| 2026-10-15 | A02-06: y_path·z_path의 끝값 오타와 for 안에서 끝값을 쓰던 부분을 고쳐 애니메이션이 부드럽게 동작함(사용자 보고). 사용자가 ‘위치와 회전이 함께 일어나 끝점이 (1,−1,1)이 아닌 것 같다’고 질문 → 모델 원점이 정확히 (1,−1,1)로 가고 눈에 보이는 중심은 R·c+t로 어긋남을 설명, 확인 방법 안내 | 추가 완료 없음(A02-06 Reflect 대기) | 교재 17/79=21.5%, 제작 0/20=0% | Reflect(투사체 운동과 회전 운동 결합) 답변 대기 |

| 2026-10-15 | A02-06: 사용자가 disp로 원래 중심 c=(0.0372, 0, 1.7251)과 마지막 중심 (4.7251, −3.0372, 3.0)을 확인(값: 회전 180·90·90, 이동 3·−3·3). 튜터 검산 R·c+t와 정확히 일치. Reflect 답변(매 단계 투사체 방정식으로 위치, 회전 방정식으로 각도를 계산해 rigidtform3d에 함께 전달) 확인. A02-07 안내 | A02-06 | 교재 18/79=22.8%, 제작 0/20=0% | 6자유도 플랫폼 예제 결과 대기 |

| 2026-10-15 | A02-07: 6DOF 플랫폼 예제를 열고 실행한 화면 확인(6DOF Euler Angles 블록, 입력 F_xyz·M_xyz, 출력 속도·위치·오일러각·몸체 속도·회전율, Scope 결과). Return Here 실행 확인. 힘·모멘트→가속도→속도→위치(각도)의 이중 적분 관계 설명. A02-08 안내 | A02-07 | 교재 19/79=24.1%, 제작 0/20=0% | QuaternionExample 실행 결과 대기 |

| 2026-10-15 | A02-08: 예제 실행·확인 보고와 코드(eul3=[0 89 0], eul4=[180 89 180], quaternion(deg2rad(...),'euler','ZYX','frame')) 제시. 각도 단위(도→deg2rad 라디안), 순서 ZYX, frame 확인. 두 오일러각의 실제 회전 차이가 약 2°임을 튜터가 검산. 2단원 완료. 3단원 교재 원문 확인 후 안내 | A02-08 | 교재 20/79=25.3%, 제작 0/20=0% | A03-01 omega_hover 계산 결과 대기 |

| 2026-10-16 | A03-01: 프로펠러 모델 파일 위치 안내(Scripts/PropellerModel.mlx 존재). 사용자 코드의 식 sqrt(M*g/(4*k_T))는 맞았으나 변수 이름 omegaHover와 omega_hover가 달라 CheckEx1이 기본값 0을 받음을 설명. 이름을 맞춘 뒤 CheckEx1 ‘Correct’(351 rad/s, 3356 rpm) 확인. A03-02 Exercise 2 안내 | A03-01 | 교재 21/79=26.6%, 제작 0/20=0% | A03-02 CheckEx2 결과 대기 |

| 2026-10-16 | A03-02·A03-03: CheckEx2 a ‘increases’ Correct, b ‘decreases’ Correct 확인. 사용자 설명(허브에 가까울수록 x가 작아 분모가 작아지고 tan가 커지며 끝 쪽은 반대)이 맞음. 전진 비행에서 블레이드를 비틀어야 하는 이유 보충. A03-04 안내 | A03-02, A03-03 | 교재 23/79=29.1%, 제작 0/20=0% | A03-04 추력·토크 곡선과 Reflect 대기 |

| 2026-10-16 | A03-04 Reflect: 사용자가 ‘비율이 거의 100배(실제 90배)이고 그래프 차이는 k_T와 k_m 값의 차이 때문’이라고 답함. 맞음. 두 식 모두 ω²이라 비율 T/Q=90은 ω와 무관하고 단위가 달라 절대 비교가 아닌 비율로 봐야 함을 보충(ω=900에서 T=14.58 N, Q=0.162 N·m). A03-05 Exercise 3 안내 | A03-04 | 교재 24/79=30.4%, 제작 0/20=0% | A03-05 Simulink 모델 대기 |

| 2026-10-16 | A03-05: 사용자가 SimplePropellerModel 모델 화면 제출(ω=900, kT=1.8e-5, km=2.0e-7, ε=1, 제곱 블록·Product 2개·Display 2개). Display T=14.58 N, Q=0.162 N·m가 튜터 계산과 일치. 3단원 완료. 4단원 교재 원문 확인 후 A04-01 안내 | A03-05 | 교재 25/79=31.6%, 제작 0/20=0% | A04-01 Mquad와 프로펠러 위치 결과 대기 |

| 2026-10-16 | A04-01: 사용자가 Mquad=1.3 kg과 +형 프로펠러 좌표(R=0.13 m) 제출, 모두 일치. R=0.13 m는 교재 Rval이나 좌표 과제는 튜터 추가임을 설명 | A04-01 | 교재 26/79=32.9%, 제작 0/20=0% | A04-02 관성 셀 실행 결과 대기 |

| 2026-10-16 | A04-02: 사용자가 + 형 관성 셀 결과 제출(M=1.3, Ixx=Iyy=0.0061, Izz=0.0117). 검산 일치. 관성 구성(원판·평행축·직육면체·45° 회전) 설명 | A04-02 | 교재 27/79=34.2%, 제작 0/20=0% | A04-03 x형 실행·Reflect 대기 |

| 2026-10-16 | A04-03: 사용자가 x형 실행 결과 제출(+형과 동일 수치). 대칭 때문에 Ixx·Iyy·Izz가 같고 바뀌는 것은 pB 좌표·몸체 45° 회전 유무임을 설명. Reflect 답변은 아직 없어 완료 아님 | 추가 완료 없음 | 교재 27/79=34.2%, 제작 0/20=0% | Reflect 답변 대기 |

| 2026-10-16 | A04-03 Reflect: 사용자가 'pB 좌표와 Ibody 회전이 바뀐다'고 답함, 맞음. 다음으로 추력·요 토크 모델과 믹서 안내 | A04-03 | 교재 28/79=35.4%, 제작 0/20=0% | A04-04 믹서 행렬 결과 대기 |

| 2026-10-16 | A04-04: 사용자가 x형 믹서 행렬 A 화면 제출(튜터 예측과 일치)과 Reflect 답(같은 방향 회전 → 요 회전). 교재 pB가 드롭다운으로 배치를 고른다고 정정 | A04-04 | 교재 29/79=36.7%, 제작 0/20=0% | A04-05 + 형 믹서 비교 대기 |

| 2026-10-16 | A04-05: 사용자가 x형·+형 믹서 행렬 화면 제출('둘다 확인했어'). 드롭다운과 결과 일치 확인, +형은 롤·피치가 각각 y·x축 프로펠러 쌍으로만 생기는 구조임을 설명 | A04-05 | 교재 30/79=38.0%, 제작 0/20=0% | A04-06 kT·km 계산 결과 대기 |

| 2026-10-16 | A04-06: 사용자가 Estimate Constants 결과 제출(W=12.753, T_prop=3.1883, kT=1.9927e-7, km=1.9927e-9). 검산 일치. rpm 기준 단위와 rad/s 환산 설명 | A04-06 | 교재 31/79=39.2%, 제작 0/20=0% | A04-07 성능 곡선 대기 |

| 2026-10-16 | A04-07: 사용자가 성능 곡선 그래프 제출. 포물선 형태·10000 rpm 값 검산 일치. 4000 rpm 값은 튜터가 제시 | A04-07 | 교재 32/79=40.5%, 제작 0/20=0% | A04-08 힘·토크 결과 대기 |

| 2026-10-16 | A04-08: 사용자가 quad_m·f·f(1)−W 결과 제출(f=[12.753;0;0;0], f(1)−W=0, quad_m은 x형 패턴). 호버 조건 확인. Reflect 답변은 아직 없어 완료 아님 | 추가 완료 없음 | 교재 32/79=40.5%, 제작 0/20=0% | Reflect 답변 대기 |

| 2026-10-16 | A04-08 Reflect: 사용자가 배치 변경 시 롤·피치 행이 바뀌고 호버링 f는 그대로라고 답함, 맞음. 다음으로 파라미터 저장 안내 | A04-08 | 교재 33/79=41.8%, 제작 0/20=0% | A04-09 저장 결과 대기 |

| 2026-10-16 | A04-09: 사용자가 파라미터 저장 실행 후 '저장했어'라고 보고(파일명 미확인). 4단원 완료. 단원 총정리 규칙(10번)과 4단원 총정리(12절) 추가 | A04-09 | 교재 34/79=43.0%, 제작 0/20=0% | 5단원 시작 |

| 2026-10-20 | 5단원 시작. 원문 확인(release 61167f7). 파일 2개 존재 확인, X형 선택해 첫 셀 실행. 호버 첫 시도는 w 미설정으로 낙하, 같은 셀에서 w 설정 후 호버 확인. 4025/3975 상승·하강 확인 | A05-01, A05-02 | 교재 36/79=45.6% | A05-03 pitch |

| 2026-10-20 | A05-03: 1·4 올림은 roll(East), 3·4 올림은 pitch(North)로 확인. 힘 Scope 검산, 6DOF 블록 Mass 1.0·Inertia eye(3) 확인, 사용자 원인 답변 | A05-03 | 교재 37/79=46.8%, 핵심 37/53=69.8%, 제작 0/20=0% | A05-04 오른쪽 roll |

| 2026-10-20 | A05-04: 오른쪽 roll(East +) 확인. 왼쪽 roll 결과(East −40 m, Fy −4.6 N)도 확인. 방향·크기가 오른쪽·pitch와 대칭. Reflect 대기 | A05-04 | 교재 38/79=48.1%, 핵심 38/53=71.7%, 제작 0/20=0% | A05-05 Reflect |

| 2026-10-20 | A05-05 Reflect: 사용자가 x형은 roll·pitch 둘 다 +, +형은 pitch만 +라고 답함(맞음). 왼쪽 roll 결과 반영 | A05-05 | 교재 39/79=49.4%, 핵심 39/53=73.6%, 제작 0/20=0% | A05-06 Yaw |

| 2026-10-20 | A05-06: 반시계 [3975 4025 3975 4025](ψ −0.08), 시계 [4025 3975 4025 3975](ψ +0.08), 총추력 보존 계산 확인. 5단원 완료, 총정리 추가 | A05-06 | 교재 40/79=50.6%, 핵심 40/53=75.5%, 제작 0/20=0% | 6단원 시작 |

| 2026-10-20 | 6단원 시작. 원문 확인(첫 셀이 x_quad_params.mat에서 kT quad_m W M g를 불러옴, 직접 저장한 파일에 M·g가 들어 있는지는 미확인). A06-01 안내 | 추가 완료 없음 | 교재 40/79=50.6%, 핵심 40/53=75.5%, 제작 0/20=0% | A06-01 결과 대기 |

| 2026-10-21 | A06-01: 파라미터 불러오기 확인(M·g 포함), 추력 곡선 그래프 제출. 곡선이 휘는 이유, 가속도 양수의 의미, 투사체와의 차이를 상세 설명 | A06-01 | 교재 41/79=51.9%, 핵심 41/53=77.4%, 제작 0/20=0% | A06-02 |

| 2026-10-21 | A06-02: 폐루프 개념·모델 구조·오차 부호·PID 항 개요 설명. 사용자가 PID 연결과 적분기 4000 설정 화면 제출 | A06-02 | 교재 42/79=53.2%, 핵심 42/53=79.2%, 제작 0/20=0% | A06-03 |

| 2026-10-21 | A06-03: P=80 Scope 제출. 주기 10초·진폭 유지 확인, 원인(스프링 비유, 비선형) 설명. A06-04 안내 | A06-03 | 교재 43/79=54.4%, 핵심 43/53=81.1%, 제작 0/20=0% | A06-04 |

| 2026-10-21 | A06-04: P=120, I=0, D=40 Scope 제출. 감쇠·정착(약 40초)·첫 고점 60 m·시작 스파이크(미분 킥) 설명. A06-05 안내 | A06-04 | 교재 44/79=55.7%, 핵심 44/53=83.0%, 제작 0/20=0% | A06-05 |

| 2026-10-21 | A06-05: P=200, I=50, D=150 실행 시 오류(t=0.3764 s 중지) 화면 제출. 원인 분석(미분 킥, 음수 명령의 제곱) 및 A06-06 설정 안내 | 추가 완료 없음(A06-05 진행 중) | 교재 44/79=55.7%, 핵심 44/53=83.0%, 제작 0/20=0% | 제한·필터 적용 후 실행 결과 대기 |

## 12. 단원 총정리

### 4단원 Quadcopter Basics 총정리 (2026-10-16, 9/9 완료)
1. 핵심 개념·식·단위
   - 몸체 좌표계: x 앞, y 오른쪽, z 아래. 추력은 −z 방향. 프로펠러 1·3 반시계(ε=+1), 2·4 시계(ε=−1).
   - 질량 Mquad = 4m + Mbody = 4×0.07 + 1.02 = 1.30 kg.
   - 관성: 프로펠러는 얇은 원판 + 평행축 정리, 몸체는 직육면체(+형은 45° 회전). 결과 Ixx=Iyy=0.0061, Izz=0.0117 kg·m² (+형·x형 동일).
   - 추력 T_i = kT·ω², 요 반작용 토크 Q_z,i = ε_i·km·ω². 믹서 [T;Qx;Qy;Qz] = A·[ω1²..ω4²].
   - 상수 추정(4000 rpm 호버): W=12.753 N, T_prop=3.1883 N, kT=1.9927e-7 N/rpm², km=0.01·kT=1.9927e-9.
   - 호버: 네 속도가 같으면 f=[12.753;0;0;0], f(1)−W=0.
2. 실제로 한 것: A04-01~A04-09 모두 실행 결과 확인. 믹서 A를 x형·+형 모두 계산, quad_m 숫자 행렬 확인, Data 폴더에 파라미터 저장(파일명 사용자 미보고).
3. 주의사항: kT 단위는 rpm 기준(N/rpm²)이며 3단원의 rad/s 기준 값(1.8e-5)과 (60/2π)²≈91.2 배 차이로 환산됨. 믹서 셀의 pB는 드롭다운으로 배치를 선택한다(튜터가 한때 '항상 x형'이라 잘못 설명했다가 정정). 같은 방향으로 모든 프로펠러를 돌리면 요 토크가 합쳐져 기체가 회전한다. 교재의 A 식에는 ω가 적혀 있으나 코드는 ω²를 입력한다.
4. 다음 단원 연결: 5단원 Quadcopter Movement에서 프로펠러 속도를 서로 다르게 주었을 때 롤·피치·요·상승 운동이 어떻게 생기는지 본다. 4단원에서 만든 mixer와 파라미터 파일을 사용한다.

### 5단원 Quadcopter Movement 총정리 (2026-10-20, 6/6 완료)
1. 핵심 개념·식·단위
   - UAV_Sim.slx: w[rpm]를 제곱해 mixer(quad_m)에 곱해 [T;Qx;Qy;Qz]를 만들고, 몸체 좌표의 중력(R·[0;0;W])에서 추력을 빼서 6DOF 블록에 힘·모멘트로 넣는다. sim은 실행 순간의 작업공간 w를 읽는다.
   - 호버: 네 w가 4000 rpm이면 추력=무게, 모멘트 0. 상승·하강은 네 w를 같이 바꿈(4025: 약 +8 m, 3975: 약 −8 m, 10초). 추력은 ω²에 비례.
   - X형(앞 1·2, 뒤 3·4): pitch 앞으로 [4000 4000 4025 4025](North +), roll 오른쪽 [4025 4000 4000 4025](East +), 왼쪽 [4000 4025 4025 4000](East −), yaw 반시계 [3975 4025 3975 4025](ψ −0.08), 시계 [4025 3975 4025 3975](ψ +0.08). 힘은 몸체 좌표에서 pitch 시 Fx, roll 시 Fy로 나타남.
   - 부호: ψ 양수는 +z(아래) 기준이라 위에서 볼 때 시계. 개루프에서는 일정한 모멘트가 각가속도를 만들어 각도가 시간의 제곱으로 커지고(10초에 약 21°) 되돌릴 장치가 없어 불안정.
   - yaw는 대각선 쌍을 올리고 내려 총추력(Σω²)을 보존. x형에서 1번만 올리면 roll·pitch 둘 다 +, +형은 pitch만 +.
2. 실제로 한 것: x형으로 첫 셀 실행(드롭다운), A05-01~06 모두 w를 직접 바꿔 sim 실행·화면 확인, 힘 Scope와 큰 Scope(범례 미확인) 해석, 6DOF 블록 파라미터 확인. 새로 만든 파일은 없음(.mlx 수정 포함).
3. 주의사항: 6DOF 블록은 Mass 1.0·Inertia eye(3)으로 4단원 기체(1.3 kg, 0.0061)와 다름(상승·각가속도 검산으로 확인). 호버는 무관. 튜터 설명 오류 정정: 전진 입력을 처음 앞 1·2번으로 읽은 건 맞았지만 w=[4025 4000 4000 4025]를 전진으로 오해한 건 사용자 실험으로 roll임을 확정, ‘θ가 −90°를 넘어 뒤집힘’은 틀림(10초 약 −21°). 애니메이션은 항상 +형 기체를 그림. w를 설정하고 같은 셀에서 sim 실행해야 함. 큰 Scope 신호 이름은 범례로 확인하지 못함.
4. 다음 단원 연결: 6단원 Quadcopter Control에서 PID 피드백으로 고도·자세를 안정화한다. 5단원의 w 조합은 제어기가 자동 계산할 입력이다. 개인 제작(B)에서는 6DOF 질량·관성을 4단원 값과 일치시킨다.
