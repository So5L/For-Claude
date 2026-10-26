# MATLAB/Simulink 드론 시뮬레이션 개인 학습 진행 기록

기준일: 2026-10-22 (한국 시간)  
진도표 버전: 1.0  
학습 언어: 한국어  
상태: 핵심 1~6단원 완료(53/53). 선택 7단원 Multidomain Physical Modeling 시작 전. (이 파일은 6단원 완료·7단원 시작 시점의 백업/인계 기록)

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
| 그 외 제품 | 6절 설치 목록 확인. 실제 예제의 라이선스 사용 가능 여부·실행은 미확인 |
| 운영체제·PC | PC A(집): macOS 26.5.2, MATLAB R2026a Update 5, 교재 /Users/min/Documents/MATLAB/Quadcopter-Modeling-Simulation-release. PC B(회사, 2026-10-26 확인): Windows, MATLAB R2026b 26.2.0.3386108, 교재 C:\Users\DAL_DAS2\Documents\MATLAB\Quadcopter-Modeling-Simulation. 사용자는 두 PC를 오가며 사용. 새 대화 시작 시 현재 PC의 `version`·`ver` 확인 필요 |
| 교재 경로 | /Users/min/Documents/MATLAB/Quadcopter-Modeling-Simulation-release (UAV.prj 프로젝트로 열림) |
| MATLAB 숙련도 | 기초 수준 |
| 수학·제어 | 배운 경험 있음, 필요 개념은 기초부터 보충 |
| 학습 시간 | 고정 일정 없음 |
| 현재 위치 | 핵심 1~6단원 완료(53/53). 7단원 Multidomain Physical Modeling 시작 전 |
| 마지막 실행 | 6단원 A06-13 Reflect 완료, 6단원 총정리 작성(2026-10-22) |
| 다음 행동 | 13절 ‘7단원 시작 준비’대로 진행: 원문 확인 → Simscape 계열 제품 설치 확인 → A07-01 안내 |
| 병행 가능 경로 | 개인 시뮬레이터 제작 B01~B20(7절). 사용자가 2026-10-22에 별도로 B 진행을 선택했음. 이 백업은 B 진행 전 스냅샷이므로 B 진행 상황은 반영되지 않음 |

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
| 공식 교재 본 단원 | 6/11 | 54.5% |
| 공식 교재 기반 체크포인트 | 53/79 | 67.1% |
| 핵심 체크포인트 | 53/53 | 100.0% |
| 개인 시뮬레이터 작업 | 0/20 | 0% |
| 선택 3차원 시각화 | 0/1 | 미시작 |

## 4. 전체 단원과 학습 체크포인트

각 항목 형식: ID — 원문 실습 위치 — 할 일 — 완료 조건. 1~6단원 전체 완료, 7~11단원은 미시작이다.

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
진도: 13/13

- [x] A06-01 — **Propeller Thrust vs Speed**: 파라미터를 불러와 추력 곡선을 실행한다. 완료 조건: 속도·추력 단위와 수직 운동식의 질량·부호를 확인한다.
- [x] A06-02 — **Closed-Loop / Exercise·Initialization**: QuadcopterPID_Vertical.slx에 PID를 연결하고 적분기 초기값을 설정한다. 완료 조건: 오차→제어기→prop_speed 경로와 초기값 4000을 기록한다.
- [x] A06-03 — **Proportional / Try**: P=80, I=0, D=0으로 실행한다. 완료 조건: 목표·실제 고도 및 진동 결과를 기록한다.
- [x] A06-04 — **Derivative / Try**: P=120, I=0, D=40으로 실행한다. 완료 조건: 앞선 결과와 응답 차이를 설명한다.
- [x] A06-05 — **PID / Try**: P=200, I=50, D=150으로 실행한다. 완료 조건: 목표·실제 고도와 세 제어항의 역할을 설명한다.
- [x] A06-06 — **PID - Anti-windup + Saturation**: 교재의 출력 제한·적분기 제한·역계산·필터 설정을 적용한다. 완료 조건: 설정표와 제한 적용 전후 고도·명령 결과를 제출한다.
- [x] A06-07 — **Quadcopter Hover Control**: UAV_Hover_Sim.slx에 고도 제어기를 구현한다. 완료 조건: 목표 높이로 이동하고 호버하는 응답을 제출한다.
- [x] A06-08 — **Quadcopter Hover Control / PID Tuner**: PID Tuner로 호버 제어기의 이득을 조정한다. 완료 조건: 실제 적용한 이득과 조정 전후 결과를 제출한다. 제품 미설치 시 보류하며 완료로 처리하지 않는다.
- [x] A06-09 — **Position Control / Try baseline**: XY_Control.slx를 실행하고 제어 경로를 추적한다. 완료 조건: 위치 제어·자세 제어·프로펠러 명령의 연결을 기록한다.
- [x] A06-10 — **Position Control / altitude**: 목표 고도를 변경한다. 완료 조건: 목표·실제 고도와 애니메이션 결과를 비교한다.
- [x] A06-11 — **Position Control / X and Y**: X·Y 목표를 변경한다. 완료 조건: 목표·실제 위치와 roll·pitch의 관계를 기록한다.
- [x] A06-12 — **Position Control / yaw**: yaw 목표를 변경한다. 완료 조건: 목표·실제 yaw와 회전 단위를 기록한다.
- [x] A06-13 — **Position Control / Reflect**: Propeller Speed 하위 시스템을 조사한다. 완료 조건: mixer·부호 있는 제곱근의 의미와 물리적 제한을 실제 블록값을 근거로 설명한다.

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

- XY_Control.slx의 Propeller Speed 하위 시스템은 Mass 1, Gain 9.81/4를 쓰며 1 kg 기체를 가정한다(4단원 1.3 kg과 다름). UAV_Hover_Sim의 UAV_Sim도 같은 6DOF(질량 1.0·관성 eye(3)) 계열로 추정(블록 확인은 UAV_Sim만).
- 제한 없는 PID(P=200, I=50, D=150)는 발산한다(t=0.376 s, 미분 킥 + 음수 명령의 제곱). A06-06의 출력 제한 0~10000·안티와인드업·필터 계수 10과 함께 써야 한다. 제곱(u²)은 부호를 잃게 하고 부호 있는 제곱근·제곱의 한 쌍은 부호를 보존한다.
- PID Tuner(선형 근사) 예측과 실제 응답은 다를 수 있다. 조정 후 반드시 실행해 확인한다.
- Scope 신호는 순서(:1, :2, :3)로 해석한다. <Xe>는 NED(North, East, Down)라 높이가 음수로 나온다. <rpy>는 roll, pitch, yaw 순, 단위 rad. yaw는 라디안이며 양수는 위에서 볼 때 시계 방향.
- ‘Run Section’ 후 출력이 없는 것은 오류가 아니다(load·clear만 있는 셀).

## 9. 현재 파일·문제·이해 기록

### 실제 생성·확인한 사용자 파일

| 파일 | 역할 | 상태 |
|---|---|---|
| learning_progress.md | 전체 진도·현재 위치·인계 기록 | 최신본(이 파일) |
| Data/x_quad_params.mat | 4단원에서 저장한 x형 파라미터(kT, quad_m, W, M, g 포함 확인) | 존재·로드 확인 |
| QuadcopterPID_Vertical.slx, UAV_Hover_Sim.slx, XY_Control.slx | 6단원에서 PID 추가·값 변경 실행 | 수정본 저장 여부·파일명 미확인 |

공식 교재 원본을 확인하기 위해 내려받은 파일은 사용자 제작물로 집계하지 않는다. 개인 제작 파일(personal_*.m/.slx)은 아직 없다.

### 해결한 실행 문제

- 1단원: 코드 셀에 한글 문장을 %없이 입력한 오류, 튜터 골격의 줄 이음(...)·== 오류, Run Section 대신 전체 Run으로 표가 초기화되는 문제.
- 3단원: 변수 이름(omegaHover vs omega_hover) 불일치로 CheckEx1이 0을 받은 문제.
- 5단원: w를 설정하지 않고 sim만 실행해 낙하(w는 같은 셀에서 설정). 전진 입력을 roll로 오해한 것은 실험으로 교정.
- 6단원: P=200, I=50, D=150(제한 없음) 발산 오류 → 제한·안티와인드업·필터 10 적용으로 해결. Run Section 무반응은 출력 없는 셀이라 정상.

### 이해 확인 요약 (사용자 서술 위주)

- 1단원: 질량이 계산식에서 상쇄되는 이유, v0 변화(비행시간 ∝ v0, 최고 높이 ∝ v0²), 시간 간격 오차, 2차원 분해, Simulink 투사체·항력 모델 구성.
- 2단원: 순차 변환과 전체 변환의 위치 차이 이유(원점 기준 회전), 변환 순서 영향, 6DOF 입력(힘·모멘트)·출력, 쿼터니언 단위·순서.
- 3단원: 추력=kT·ω², 허브·끝단 유입각, 추력·토크 비 90배(비율은 ω와 무관), SimplePropellerModel 구성.
- 4단원: 질량·관성 계산, mixer A 부호 패턴(x형·+형), kT·km 추정(rpm 기준), 성능 곡선, 파라미터 저장.
- 5단원: X형 w 조합(앞 1·2/뒤 3·4): pitch [4000 4000 4025 4025], roll [4025 4000 4000 4025], yaw [3975 4025 3975 4025]. 사용자가 방향을 실험으로 확인. 개루프 불안정 설명은 사용자가 방향을 맞게 서술.
- 6단원: P/D/I 역할과 실험 비교 요약은 12절. Reflect에서 ‘음수가 양수가 되어 폭주’를 정확히 짚었고 제곱근과 제곱의 구분은 튜터가 바로잡음.

### 확인하지 못한 항목(미해결)

- 5단원 시계 yaw 실행의 Fz 축 숫자가 반시계와 달라 보였으나 원인 미확인(둘 다 0에 가까움).
- 큰 Scope 일부 신호의 범례, PID 설정 화면 일부는 그래프로만 확인했고 직접 보지 못함.

- 보충 후보: 수치 적분, 좌표계·회전행렬, 힘·토크, 관성, 피드백, 이득 조정, 제한과 안티와인드업, 직렬 제어.

## 10. 수업 진행 규칙

1. 매 수업은 현재 위치·진행률 → 배울 내용 → 핵심 개념·단위·좌표 → 실습 한 단계 → 결과 확인·이해 확인 순서로 진행한다. 답변마다 현재 진척률(교재 체크포인트, 핵심, 현재 단원, 제작)을 표로 알린다.
2. 교재 원문(GitHub release 61167f7, .mlx는 zip 안의 matlab/document.xml, .slx는 simulink/systems/*.xml)을 직접 읽어 원문 순서대로 진행한다. 읽지 못한 것은 추측하지 않는다.
3. 과제·질문은 교재 원문의 Try·Exercise·Reflect만 낸다. 튜터 추가 계산·질문은 하지 않거나 ‘추가(선택)’로만 표시하며 진행률에 넣지 않는다.
4. 설명은 많이 한다: 원문이 말하는 것, 결과가 그렇게 나온 이유(수치 검산·물리적 원인), 이전 단원·투사체와의 연결, 흔한 오해, 이후 제어와의 연결. 결과만 받고 넘어가지 않는다. 사용자가 이해하지 못했다고 하면 그 부분부터 다시 푼다.
5. 사용자 결과(스크린샷)에서 확인된 것만 사실로 쓰고, 추정은 ‘추정’이라고 쓴다. 튜터의 설명 오류는 즉시 정정하고 진도 파일에 기록한다.
6. 오류가 나면 진도를 멈추고 원인을 먼저 해결한다(오류 메시지 해석 → 원인 → 최소 수정).
7. 완료는 사용자 실행 결과나 직접 서술이 있을 때만 인정한다. 설명 청취만으로 완료 처리하지 않는다. 보류·건너뜀은 분모에 남기고 완료로 계산하지 않는다.
8. 매 답변 후 이 파일(learning_progress.md)을 갱신한다: 완료 ID와 근거, 파일명, 문제·해결, 현재 위치, 다음 행동, 진행률. 새 대화에서 이 파일과 프롬프트를 올리면 이어서 진행한다.
9. 단원이 끝나면 총정리(핵심 개념·식·단위, 실제로 만든 파일·결과 값, 교재와 튜터 설명이 다른 점·주의사항, 다음 단원 연결)를 답변하고 12절에 추가한다.
10. 한 번에 너무 많은 작업을 시키지 않는다. 단계마다 사용자가 실행한 결과를 확인한 뒤 다음으로 간다.
11. 사용자가 ‘학습 인계서 작성해 줘’라고 하면 교재·환경·완료 ID·현재 위치·두 진행률·실제 파일·이해/보충·미해결 오류·다음 실습·전체 진도표를 이 기록과 대조해 작성한다.

## 11. 수업 기록 요약

| 날짜 | 내용 | 교재 진행률 |
|---|---|---|
| 2026-10-13 | 교재 조사, 환경 확인(ver 32개 제품), 프로젝트 열기, 1단원 A01-01~03 | 3/79 |
| 2026-10-14 | 1단원 완료(투사체 1D·2D·Simulink·항력) | 12/79 |
| 2026-10-15 | 2단원 완료(Rigid Transforms) | 20/79 |
| 2026-10-16 | 3단원, 4단원 완료(프로펠러·기체 기초, 파라미터 저장) | 34/79 |
| 2026-10-20 | 5단원 완료(Quadcopter Movement, 개루프 pitch·roll·yaw) | 40/79 |
| 2026-10-21 | 6단원 A06-01~A06-06(식, 폐루프, P·PD·PID, 제한) | 46/79 |
| 2026-10-22 | 6단원 A06-07~A06-13 완료(호버 제어, PID Tuner, XY_Control, Reflect) | 53/79 |

세부 수업 기록은 사용자가 보관한 이전 대화와 이전 learning_progress.md(기록 전체판)에 있다. 이 파일은 인계용 요약이다.

## 12. 단원 총정리

### 1~3단원 총정리 요약
- 1단원 Projectile Motion: 위쪽 양 좌표, v(t+dt)=v+a·dt, p+=v_new·dt, n_timesteps=ceil(t_end/dt), t_end=(v0+√(v0²+2g·p0))/g, 질량 상쇄(a=F/m), 항력(−αv) 모델의 종단속도.
- 2단원 Rigid Transforms: rigidtform3d 회전·병진, 원점 기준 회전 때문에 순차 변환≠전체 변환(전체=회전 후 이동), 6DOF 블록 입출력, 쿼터니언.
- 3단원 Propeller Model: T=kT·ω², Q=km·ω², 호버 ω_hover=√(Mg/(4kT)), 단위 rad/s(4단원 이후는 rpm 기준 kT와 (60/2π)² 환산).


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

### 6단원 Quadcopter Control 총정리 (2026-10-22, 13/13 완료)
1. 핵심 개념·식·단위
   - 수직 운동: z̈ = (4kT·N² − M·g)/M (위쪽 양, 단위 m/s²). 추력은 속도 제곱에 비례(비선형), 호버 4000 rpm에서 추력 12.753 N = 무게. 원문 식의 질량 나눗셈 누락에 주의.
   - 폐루프: e = 목표 − 측정, 음의 피드백. P는 스프링(오차에 비례), D는 속도 비례 감쇠, I는 오차 누적(정착값 보정). 적분기 초기값 4000 = 호버 기준.
   - 실행 결과: P=80 → 주기 약 10초로 계속 진동. P=120·D=40 → 감쇠하나 약 40초 정착, 시작 미분 킥(86,000 rpm). P=200·I=50·D=150(제한 없음) → t=0.376 s에서 발산(음수 명령의 제곱 + 미분 킥). 제한 0~10000·back-calculation 1·적분기 제한·N=10 → 오버슈트 약 10%, 12~15초 정착. UAV_Hover_Sim 5 m(같은 이득) 오버슈트 약 64% → PID Tuner(P=116.48, I=17.24, D=193.20, N=17.25) 오버슈트 약 5%, 정착 약 20초(Tuner 예측보다 느림).
   - 위치 제어는 직렬: 위치 오차 → 원하는 roll·pitch(±0.1 rad 제한) → 자세 제어 → mixer(힘·모멘트→ω², 부호 있는 제곱근) → 프로펠러. X는 pitch(−), Y는 roll(+). yaw는 라디안, 양수=위에서 볼 때 시계. 위치 오차는 cos·sin(yaw)로 몸체 방향으로 회전.
   - 시간 규모: 고도·yaw 약 2~3초, 수평 위치 약 12초(기울이고 가속·감속 2단계).
2. 실제로 한 것: QuadcopterPID_Vertical.slx(PID 추가·설정), UAV_Hover_Sim.slx(PID 복사·Tuner), XY_Control.slx(고도 20·5, X·Y, yaw=pi/2 변경 실행). 수정한 모델 파일의 저장 여부와 파일명은 확인하지 못함.
3. 주의사항: 6DOF 블록 Mass 1.0·Inertia eye(3), XY_Control Mass 1·g 9.81/4 등 교재 상수는 현실적이지 않다. 제한 없는 PID는 발산할 수 있고 Tuner(선형 근사) 예측과 실제 응답이 다르다. Scope 신호는 순서(:1,:2,:3)로 해석(NED 위치·roll·pitch·yaw). 제곱(u²)은 부호를 잃게 하지만 부호 있는 제곱근·제곱 한 쌍은 부호를 보존. 큰 Scope 신호의 범례는 일부 확인하지 못함.
4. 다음 연결: 핵심 1~6단원 완료(53/53). 선택 7~11단원(총 26개)은 Simscape Electrical·Driveline 등 미설치 제품 확인이 필요한 부분이 있다. 개인 시뮬레이터 제작(B01~B20)은 4단원 파라미터(x_quad_params.mat)와 6단원 PID·제한·mixer를 직접 구현해 확인한다. 개인 제작에서는 질량·관성을 4단원 값과 일치시킨다.


## 13. 7단원 시작 준비 (새 대화에서 바로 시작하기 위한 안내)

**목표 단원**: 7. Multidomain Physical Modeling — 선택 심화, 파일 `Scripts/MultidomainPhysicalModeling.mlx`. 체크포인트 A07-01~A07-10(10개, 4절 참조). 현재 진도 0/10.

**시작 순서(수업 규칙 10절 그대로)**
1. 현재 위치·진행률을 표시한다(교재 53/79=67.1%, 핵심 53/53=100%, 제작 0/20, 7단원 0/10).
2. GitHub 원문(release 61167f7)의 `Scripts/MultidomainPhysicalModeling.mlx`를 직접 읽는다. Propeller_Model.slx, Propeller_Ref_Speed.slx 내부 블록·InitFcn도 읽는다(.slx는 zip 해제 후 simulink/systems/*.xml).
3. **제품 확인이 먼저다.** 이 단원은 Simscape Electrical(ee_lib), Simscape Driveline(sdl_lib), Simscape(fl_lib·nesl_utility)를 참조한다. 사용자 ver 목록(6절)에는 Simscape만 있고 **Simscape Electrical, Simscape Driveline은 없다.** 실행 전 사용자에게 `ver` 결과에서 이 두 제품 존재 여부와, 없다면 대학 라이선스로 추가 설치 가능한지(MATLAB 애드온 탐색기·MathWorks 계정) 확인을 요청한다. 실행이 불가능하면 A07 체크포인트는 ‘보류’로 기록하고(완료로 계산 안 함), 8단원(Trajectory Generation) 또는 개인 제작 B로 전환할지 사용자에게 묻는다.
4. 제품이 준비되면 A07-01(연결 예제 PWMControlledDCMotorExample 열기·실행)부터 안내한다. 원문의 Try·Exercise·Reflect만 과제로 낸다.
5. 7단원 개념은 많이 설명한다: Simscape(물리 네트워크: 전기·기계·신호 영역 사이 변환), DC 모터 모델, 6단원의 이상 속도원(속도를 입력하면 그대로 따라가는 모델)과 전류 제어 모터 모델의 차이, 프로펠러 추력·토크 곡선의 물리 모델과 3~4단원 kT·km 식의 연결.

**7단원 사전 지식(기록해 둔 사실)**
- 6단원에서 쓴 모델은 프로펠러 속도를 입력으로 주는 이상화 모델이다. 7단원은 전기 모터와 전류 제어까지 포함한 물리 모델로 간다.
- 6DOF 블록 질량·관성이 4단원 값과 다르다는 점(8절)은 7단원 모델에도 해당될 수 있으니 블록 값을 확인한다.
- 사용자는 설명을 많이 해 주길 원하고, 원문 과제만 내길 원한다(10절 3·4항).
