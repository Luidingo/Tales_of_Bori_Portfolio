# 🥁 JGTale (Tales of Bori VR) - Portfolio

**한국 전통 악기 장구를 VR로 연주하는 리듬 게임**

<div align="center">

![Unreal Engine](https://img.shields.io/badge/Unreal%20Engine-5.4.4-0E1128?style=for-the-badge&logo=unrealengine)
![Meta Quest](https://img.shields.io/badge/Meta%20Quest-3%2F3S-0467DF?style=for-the-badge&logo=meta)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Blueprint](https://img.shields.io/badge/Blueprint-0E1128?style=for-the-badge&logo=unrealengine)

**Version 1.1.12** | **Development: 2025.06 - 2025.12**

> **Note**: This is a portfolio showcase version. Some implementation details and proprietary information have been redacted for confidentiality.

</div>

---

## 📑 목차

1. [📖 프로젝트 소개](#-프로젝트-소개)
2. [🎯 필수 플러그인 안내](#-필수-플러그인-안내)
3. [🖼️ 스크린샷](#️-스크린샷)
4. [🏗️ 기술 스택](#️-기술-스택)
5. [🎯 핵심 기능](#-핵심-기능)
6. [📊 시스템 아키텍처](#-시스템-아키텍처)
7. [🗂️ 프로젝트 구조](#️-프로젝트-구조)
8. [🎮 주요 시스템 설명](#-주요-시스템-설명)
9. [🚀 주요 기술 구현](#-주요-기술-구현)
10. [🥽 VR 개발 가이드](#-vr-개발-가이드)
11. [🔨 빌드 및 배포](#-빌드-및-배포)
12. [🔧 트러블슈팅](#-트러블슈팅)
13. [⚠️ 알려진 이슈 및 제한사항](#️-알려진-이슈-및-제한사항)
14. [📜 라이센스](#-라이센스)

---

## 📖 프로젝트 소개

**JGTale (Tales of Bori VR)** 은 한국 전통 악기인 장구를 Meta Quest VR 환경에서 실제처럼 연주할 수 있는 리듬 게임입니다. 사내 제작 Rhythm Editor에서 제작된 악보를 기반으로 음악에 맞춰 장구를 연주하며, 전통 음악과 현대 VR 기술의 만남을 경험할 수 있습니다. <br>
※ 사내 보안에 따라 소스 코드를 비공개하였으며, 상세 아키텍처는 해당 README 문서를 통해 파악 가능합니다.

### 주요 특징

- **실제 장구 연주 경험**: VR 컨트롤러로 채를 잡고 물리 기반으로 장구를 연주
- **전통 장구 악보 시스템**: 덕(오른손), 쿵(왼손), 덩(양손) 3가지 타입의 노트
- **다양한 게임 모드**: 음악 모드(곡 플레이), 자유 모드(연습), 스토리 모드(예정)
- **Meta 계정 연동**: Meta Quest 계정 기반 인증 및 프로필 시스템
- **실시간 판정 시스템**: Perfect/Great/Good/Bad/Miss 5단계 판정
- **서버 연동**: 곡 목록 다운로드, 랭킹, 기록 저장
- **몰입형 VR 환경**: 한국 전통 가옥을 배경으로 한 아름다운 공간

### 개발 역할

- **VR Interaction**: Physics Handle 기반 Grab 시스템, 입력 처리
- **Rhythm System**: 판정 로직, 노트 생성, 오디오 동기화
- **Asset Management**: 서버 연동 파일 다운로드, 로컬 캐싱, 런타임 로딩
- **UI/UX**: Widget 시스템, HUD, 메뉴 구현
- **Performance Optimization**: Quest 최적화, LOD, HISM 적용
- **Build & Deploy**: Android 빌드, MQDH 배포, 앱 스토어 심사 대응

---

## 🎯 필수 플러그인 안내

⚠️ **본 프로젝트는 다음 플러그인을 반드시 설치해야 정상 빌드됩니다.**

### 📁 MetaXR

- **버전**: 71.0.0
- **다운로드**: https://developers.meta.com/horizon/downloads/package/unreal-engine-5-integration/71.0
- **설치 경로**: `Plugins/MetaXR/`
- **사용 이유**: Unreal Engine 5.4.4에서 가장 안정적인 버전

### 📁 MetaXRInteraction

- **버전**: 71.0.0
- **다운로드**: https://developers.meta.com/horizon/downloads/package/meta-xr-interaction-sdk-unreal/71.0.0
- **설치 경로**: `Plugins/MetaXRInteraction/`

---

## 🖼️ 스크린샷

### 음악 모드 - 게임플레이
<!-- 스크린샷 추가 예정 -->
*장구 앞에서 날아오는 노트를 타이밍에 맞춰 연주하는 모습*

### 자유 모드 - 연습 화면
<!-- 스크린샷 추가 예정 -->
*리듬 패턴을 선택하여 자유롭게 연습할 수 있는 인터페이스*

### 곡 선택 화면
<!-- 스크린샷 추가 예정 -->
*서버에서 다운로드한 곡 목록과 난이도 선택*

### 결과 화면
<!-- 스크린샷 추가 예정 -->
*플레이 결과 및 등급 표시*

---

## 🏗️ 기술 스택

### Core Technology
- **Engine**: Unreal Engine 5.4.4
- **Language**: C++ (Core Logic) + Blueprint (Gameplay)
- **Platform**: Meta Quest 3 / Quest 3S
- **VR SDK**: MetaXR 71.0.0

### VR & Rendering
- **Hand Tracking**: Meta Hand Tracking API
- **Physics**: Unreal Physics Engine (Physics Handle for grab)
- **Rendering**: 
  - Forward Shading
  - Mobile Multi-View
  - Instanced Stereo
- **Optimization**: HISM, LOD, Static Lighting

### Backend Integration
- **Authentication**: Meta Account Auth + JWT
- **API Communication**: RESTful HTTP (JSON)
- **Storage**: Presigned URL 기반 파일 스토리지

### Key Unreal Modules
- **Audio**: USoundWaveProcedural, AudioComponent
- **Physics**: PhysicsHandleComponent, CollisionComponent
- **UI**: UMG (Widget)
- **Networking**: HTTP Module
- **VR**: OculusVR Plugin, OpenXR

---

## 🎯 핵심 기능

### 1. 🎵 음악 모드

#### 곡 선택 및 다운로드
- 서버에서 곡 목록 조회 (`SongCatalogSubsystem`)
- Presigned URL을 통한 곡 파일 다운로드 (Audio, Sheet, Image)
- 다운로드 진행률 실시간 표시
- 로컬 캐시 시스템 (`SongAssetCacheSubsystem`)

#### 게임플레이
- **노트 시스템**:
  - 덕(Deok): 오른손으로 장구 오른편 타격
  - 쿵(Kung): 왼손으로 장구 왼편 타격
  - 덩(Deong): 양손 동시 타격
- **판정 시스템**:
  - Perfect: 200점 (±50ms)
  - Great: 150점 (±100ms)
  - Good: 100점 (±150ms)
  - Bad: 50점 (±200ms)
  - Miss: 0점 (범위 외)
- **실시간 HUD**: 콤보, 점수, 판정 표시
- **오디오 동기화**: `RhythmSyncSubsystem`을 통한 정확한 타이밍

#### 결과 및 기록
- 등급 계산 (S, A, B, C, D, F)
- 서버에 기록 저장 (`SongRecordSubsystem`)
- 랭킹 확인 (`RankingBoardWidget`)

### 2. 🎨 자유 모드

#### Practice Mode (연습 모드)
- 배경 선택 기능
- 자유롭게 장구 연주
- 실시간 소리 피드백

#### Rhythm Mode (리듬 연습)
- 리듬 패턴 목록 선택
- 리듬 미리보기
- 반복 연습 가능

### 3. 📖 스토리 모드

- **현재 상태**: 미구현 (EntryPoint만 존재)
- **예정**: 스토리 기반 튜토리얼 및 챕터 진행

### 4. 🔐 인증 시스템

#### Meta 계정 연동
- Meta Account Auth를 통한 Nonce + UserId 발급
- 서버에 Oculus 계정 등록 및 로그인
- JWT 기반 토큰 관리

#### 프로필 시스템
- 사용자별 다중 프로필 생성 가능
- 프로필별 색상 커스터마이징
- 프로필별 게임 기록 관리

---

## 📊 시스템 아키텍처

### 앱 플로우 차트 & 클래스 계층도 간결 버전
<img width="2613" height="1586" alt="앱 플로우 차트_간결 버전" src="https://github.com/user-attachments/assets/29d4a016-98c7-4fec-b10e-04705c2c9ab7" />
<img width="2613" height="1586" alt="클래스 다이어그램_간결 버전" src="https://github.com/user-attachments/assets/bda9e60a-c416-4c06-96a0-6ad8b9273fe1" />

<details>
<summary><b>📋 상세 플로우차트 및 다이어그램 보기</b></summary>

시스템 아키텍처의 상세 다이어그램은 프로젝트 문서를 참고해주세요.

**주요 구성 요소**:
- **Core Actors**: PlayerPawn, JangguActor, NoteSpawner, NoteActor, Stick
- **Subsystems**: RhythmSyncSubsystem, SongCatalogSubsystem, AccountAuthSubsystem
- **Components**: HandsGrabberComponent, JudgementZoneComponent, HUDControllerComponent
- **UI Widgets**: 30+ 위젯 (Auth, Music, Rhythm, Settings, Loading)

</details>

---

## 🗂️ 프로젝트 구조

### 핵심 컴포넌트

```
JGTale/
├── Source/
│   ├── JGTale/
│   │   ├── Actor/                   # 게임 액터
│   │   │   ├── PlayerPawn           # VR 플레이어
│   │   │   ├── JangguActor          # 장구 악기
│   │   │   ├── NoteSpawner          # 노트 생성기
│   │   │   ├── NoteActor            # 개별 노트
│   │   │   └── Stick                # 장구채
│   │   │
│   │   ├── Component/               # 액터 컴포넌트
│   │   │   ├── HandsGrabberComponent    # Physics Handle 기반 Grab
│   │   │   ├── JudgementZoneComponent   # 판정존
│   │   │   └── MetaAccountAuthComponent # Meta 인증
│   │   │
│   │   ├── Subsystem/               # 게임 서브시스템
│   │   │   ├── RhythmSyncSubsystem      # 오디오 동기화
│   │   │   ├── SongCatalogSubsystem     # 곡 목록 관리
│   │   │   ├── AccountAuthSubsystem     # 인증 관리
│   │   │   └── SongAssetCacheSubsystem  # 로컬 캐시
│   │   │
│   │   ├── Manager/                 # 매니저 클래스
│   │   │   ├── RhythmNoteManager        # 판정 로직
│   │   │   ├── RhythmHUDStatManager     # 통계 관리
│   │   │   └── RhythmAudioPlayer        # 오디오 재생
│   │   │
│   │   ├── Widget/                  # UMG 위젯
│   │   │   ├── Auth/                    # 인증 UI
│   │   │   ├── Music/                   # 음악 모드 UI
│   │   │   ├── Rhythm/                  # 리듬 연습 UI
│   │   │   └── Settings/                # 설정 UI
│   │   │
│   │   └── Data/                    # 데이터 타입
│   │       ├── RhythmNoteTypes          # 노트 데이터
│   │       └── SongCatalogTypes         # 곡 메타데이터
│   │
│   └── JGTale.Build.cs              # 빌드 설정
│
├── Content/
│   ├── Maps/                        # 레벨
│   ├── UI/                          # UMG 에셋
│   ├── Audio/                       # 효과음
│   └── Models/                      # 3D 모델
│
├── Plugins/
│   ├── MetaXR/                      # Meta XR SDK 71.0.0
│   └── MetaXRInteraction/           # Meta XR Interaction SDK
│
└── Config/
    ├── DefaultEngine.ini            # 엔진 설정
    └── DefaultGame.ini              # 게임 설정
```

---

## 🎮 주요 시스템 설명

### 1. 노트 시스템 (RhythmNoteTypes)

#### 노트 타입
```cpp
UENUM(BlueprintType)
enum class ENoteType : uint8
{
    None,
    Deok,    // 덕 (오른손, 장구 오른편)
    Kung,    // 쿵 (왼손, 장구 왼편)
    Deong    // 덩 (양손, 동시 타격)
};
```

#### 노트 데이터 구조
```cpp
USTRUCT(BlueprintType)
struct FNoteData
{
    GENERATED_BODY()
    
    UPROPERTY(BlueprintReadWrite)
    ENoteType Type;
    
    UPROPERTY(BlueprintReadWrite)
    FNoteTimingData Timing;  // BeatIndex, SubIndex
    
    UPROPERTY(BlueprintReadWrite)
    float Time;  // 밀리초 단위 타임스탬프
    
    UPROPERTY(BlueprintReadWrite)
    int32 LocalBaseIndex;  // 64th Note 기준 인덱스
};
```

### 2. 판정 시스템 (RhythmNoteManager)

#### 판정 로직
```cpp
// RhythmNoteManager::TryJudgeInZone()
EJudgeResult URhythmNoteManager::TryJudgeInZone(
    ENoteType NoteType,
    EHandSide HandSide,
    float CurrentTimeMs
)
{
    // 1. 판정 가능한 노트 찾기
    FNoteData* TargetNote = FindJudgeableNote(NoteType, CurrentTimeMs);
    if (!TargetNote)
        return EJudgeResult::Miss;
    
    // 2. 타이밍 차이 계산
    float TimeDiff = FMath::Abs(CurrentTimeMs - TargetNote->Time);
    
    // 3. 판정 결정
    if (TimeDiff <= 50.0f)
        return EJudgeResult::Perfect;
    else if (TimeDiff <= 100.0f)
        return EJudgeResult::Great;
    else if (TimeDiff <= 150.0f)
        return EJudgeResult::Good;
    else if (TimeDiff <= 200.0f)
        return EJudgeResult::Bad;
    else
        return EJudgeResult::Miss;
}
```

### 3. 오디오 동기화 시스템 (RhythmSyncSubsystem)

#### 동기화 메커니즘
```cpp
// RhythmSyncSubsystem::StartSongFromCache()
void URhythmSyncSubsystem::StartSongFromCache(const FString& SongId)
{
    // 1. 오디오 로드
    RhythmAudioPlayer->LoadFromWav(AudioPath);
    
    // 2. 노트 데이터 준비 (비동기)
    NoteSpawner->PrepareActiveSongAsync();
    
    // 3. 동기화 설정
    NoteSpawner->SetAudioSync(RhythmAudioPlayer);
    
    // 4. 재생 시작
    RhythmAudioPlayer->PlayFrom(0);
    NoteSpawner->StartNotesAtWorldTime(GetWorld()->GetTimeSeconds());
}
```

### 4. VR 상호작용 (HandsGrabberComponent)

#### Physics Handle 기반 Grab
```cpp
// HandsGrabberComponent::GrabStick()
void UHandsGrabberComponent::GrabStick(UPhysicsHandleComponent* PhysicsHandle, AStick* Stick)
{
    if (!PhysicsHandle || !Stick)
        return;
    
    // Physics Handle로 Grab
    UPrimitiveComponent* StickMesh = Stick->GetMeshComponent();
    PhysicsHandle->GrabComponentAtLocation(
        StickMesh,
        NAME_None,
        Stick->GetActorLocation()
    );
    
    // 손 위치 추적 시작
    bIsGrabbing = true;
    GrabbedStick = Stick;
}
```

---

## 🚀 주요 기술 구현

### 1. Meta 계정 인증

```cpp
// MetaAccountAuthComponent::StartAuthentication()
void UMetaAccountAuthComponent::StartAuthentication()
{
    // 1. Meta SDK 초기화
    if (!InitializeMetaSDK())
    {
        OnAuthFailed.Broadcast("Meta SDK initialization failed");
        return;
    }
    
    // 2. Nonce 생성
    FString Nonce = GenerateNonce();
    
    // 3. Meta 계정에서 UserId 가져오기
    FString MetaUserId = GetMetaUserId();
    
    // 4. 서버에 인증 요청
    AccountAuthSubsystem->LoginWithOculus(Nonce, MetaUserId);
}
```

### 2. 곡 다운로드 및 캐싱

```cpp
// SongCatalogSubsystem::DownloadBaseAssetsIfNeeded()
void USongCatalogSubsystem::DownloadBaseAssetsIfNeeded(
    const FString& SongId,
    FOnDownloadComplete OnComplete
)
{
    // 1. 캐시 확인
    if (SongAssetCache->IsCached(SongId))
    {
        OnComplete.Execute(true);
        return;
    }
    
    // 2. Presigned URL 요청
    RequestPresignedUrls(SongId, [this, SongId, OnComplete](TArray<FString> Urls)
    {
        // 3. 병렬 다운로드
        TArray<TFuture<bool>> DownloadTasks;
        DownloadTasks.Add(Async(EAsyncExecution::ThreadPool, [=]() 
        {
            return DownloadFile(Urls[0], GetAudioCachePath(SongId));
        }));
        DownloadTasks.Add(Async(EAsyncExecution::ThreadPool, [=]() 
        {
            return DownloadFile(Urls[1], GetSheetCachePath(SongId));
        }));
        DownloadTasks.Add(Async(EAsyncExecution::ThreadPool, [=]() 
        {
            return DownloadFile(Urls[2], GetImageCachePath(SongId));
        }));
        
        // 4. 완료 대기
        bool bAllSuccess = true;
        for (auto& Task : DownloadTasks)
        {
            bAllSuccess &= Task.Get();
        }
        
        OnComplete.Execute(bAllSuccess);
    });
}
```

---

## 🥽 VR 개발 가이드

### Quest 최적화 필수 사항

#### 1. 렌더링 설정

**Project Settings → Platforms → Android:**
```ini
[/Script/AndroidRuntimeSettings.AndroidRuntimeSettings]
bSupportsVulkan=True
bBuildForES31=True
bSupportsVulkanSM5=False

[/Script/Engine.RendererSettings]
r.Mobile.ShadingPath=1  ; Forward Shading
r.MobileHDR=True
r.MobileMultiView=True  ; Mobile Multi-View (필수)
vr.InstancedStereo=True ; Instanced Stereo (필수)
```

**⚠️ 중요**: 이 설정들을 **반드시** 활성화해야 Quest에서 정상 동작합니다!

#### 2. 성능 최적화

**HISM (Hierarchical Instanced Static Mesh) 사용:**
```cpp
// 환경 오브젝트는 HISM으로 배치
UHierarchicalInstancedStaticMeshComponent* HISM = 
    CreateDefaultSubobject<UHierarchicalInstancedStaticMeshComponent>(TEXT("Trees"));
HISM->SetStaticMesh(TreeMesh);

for (int32 i = 0; i < 100; i++)
{
    FTransform Transform = GenerateRandomTransform();
    HISM->AddInstance(Transform);
}
```

**LOD (Level of Detail) 설정:**
- LOD 0: 0-5m (Full Detail)
- LOD 1: 5-15m (Medium)
- LOD 2: 15-30m (Low)
- LOD 3: 30m+ (Very Low)

**Static Lighting 사용:**
- Movable Light 최소화
- Lightmap Resolution: 32-128
- Dynamic Shadows OFF (성능 이슈)

#### 3. 그래픽 품질 설정

**성능 목표:**
- Draw Calls: 1000 이하
- 환경 메시: ~10,000 tris
- 텍스처: 최대 2048x2048 (ASTC 압축)

### VR 상호작용 모범 사례

#### Physics Handle 설정
```cpp
// HandsGrabberComponent.cpp
UPhysicsHandleComponent* PhysicsHandle = NewObject<UPhysicsHandleComponent>(this);
PhysicsHandle->LinearDamping = 200.0f;    // 부드러운 이동
PhysicsHandle->LinearStiffness = 750.0f;  // 반응성
PhysicsHandle->AngularDamping = 500.0f;
PhysicsHandle->AngularStiffness = 1500.0f;
PhysicsHandle->InterpolationSpeed = 50.0f;
```

#### VR 멀미 방지
- 텔레포트 이동 사용
- 스무스 이동 비활성화
- 가이드 스플라인 따라 자동 이동
- 카메라 흔들림 최소화

---

## 🔨 빌드 및 배포

### Android (Quest) 빌드 체크리스트

#### 1. 빌드 전 필수 확인 사항

**✅ 엔진 설정:**
```ini
[/Script/AndroidRuntimeSettings.AndroidRuntimeSettings]
MinSDKVersion=29
TargetSDKVersion=32

[/Script/Engine.RendererSettings]
r.Mobile.ShadingPath=1
r.MobileMultiView=True
vr.InstancedStereo=True
r.MobileHDR=True
```

**✅ VR 설정:**
- Forward Shading 활성화
- Instanced Stereo 활성화
- Mobile Multi-View 활성화

**✅ 앱 서명:**
- Keystore 파일 설정 (보안상 비공개)

#### 2. 빌드 절차

```
1. File → Package Project → Build Configuration → Shipping
2. File → Package Project → Android → Android (ASTC)
3. 빌드 시간: 약 20-40분
4. 결과물: .apk 파일
```

#### 3. MQDH 배포

```bash
# Quest 기기를 USB로 연결
# MQDH에서 Device Manager 확인
# APK 설치 및 실행
```

#### 4. 앱 스토어 상태

**현재 상태**: Meta Quest Store 얼리액세스 심사 중

---

## 🔧 트러블슈팅

### 주요 이슈 및 해결 방법

#### 1. VR 렌더링 이슈

**증상**: Quest에서 화면이 깨지거나 양쪽 눈 이미지가 다름

**해결**:
```ini
; Config/DefaultEngine.ini
[/Script/Engine.RendererSettings]
vr.InstancedStereo=True
r.MobileMultiView=True
```

#### 2. 채 Grab 실패

**증상**: 컨트롤러로 채를 잡을 수 없음

**해결**: Physics Handle 초기화 확인 및 재생성

#### 3. 오디오 동기화 실패

**증상**: 노트와 음악이 맞지 않음

**해결**: 
- 오디오 파일 샘플레이트 확인 (44100 Hz 또는 48000 Hz)
- 비행 시간 재조정
- JSON 노트 데이터 검증

#### 4. 곡 다운로드 실패

**증상**: 다운로드 시작 후 403 Forbidden 에러

**해결**: Presigned URL 만료 시 재요청 로직 구현

#### 5. 성능 저하

**증상**: 60fps 아래로 떨어짐

**해결**:
- HISM 사용으로 드로우콜 감소
- LOD 적용
- Static Lighting 사용
- Occlusion Culling 강화

---

## ⚠️ 알려진 이슈 및 제한사항

### 현재 알려진 버그

#### 1. 성능 - 간헐적 프레임 드롭
- **발생 조건**: 드로우콜 1000+, 폴리곤 1500K+
- **완화 조치**: HISM, LOD, Static Lighting 적용

#### 2. 물리 - 채 충돌 어색함
- **증상**: 채가 장구를 여러 번 치는 현상
- **원인**: Physics Handle의 물리 연산 특성
- **완화 조치**: 연속 충돌 쿨다운 (100ms), 최소 속도 임계값 설정

#### 3. 오디오 - 특정 곡 노트 싱크 불일치
- **증상**: 일정 구간만 싱크 안맞음
- **원인**: 에디터 노트 배치 오류 가능성
- **완화 조치**: 해당 곡 재편집, 비행 시간 수동 조정

### 알려진 제한사항

- **멀티플레이**: 현재 싱글플레이어 전용
- **스토리 모드**: 미구현
- **최대 곡 길이**: 5분
- **타겟 플랫폼**: Quest 3/3S 전용

---

## 📜 라이센스

본 프로젝트는 Unreal Engine C++ 및 Blueprint로 개발되었으며, **상업용 프로젝트**입니다.

### Portfolio Notice

이 README는 포트폴리오 목적으로 작성된 공개 버전입니다. 다음 정보는 기밀 유지를 위해 수정되었습니다:
- 서버 API 엔드포인트 및 인증 정보
- 내부 개발 프로세스 및 도구
- 보안 관련 설정 및 키 정보
- 프로젝트 팀 연락처

### Status

- **개발 상태**: Meta Quest Store 얼리액세스 심사 중
- **프로젝트 기간**: 2025.06 - 2025.12
- **플랫폼**: Meta Quest 3 / 3S

---

## 🙏 Acknowledgments

- **Unreal Engine** by Epic Games
- **Meta XR SDK** by Meta
- **Tales of Bori Development Team**

---

<div align="center">

**Portfolio Version - For Demonstration Purposes**

[🔝 맨 위로 돌아가기](#-jgtale-tales-of-bori-vr---portfolio)

</div>
