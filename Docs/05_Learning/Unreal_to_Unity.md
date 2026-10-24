---
tags: [learning, mapping]
updated: 
---

# 언리얼 → 유니티 개념 매핑

> 1:1 대응이 아닌 것이 많다. "비슷하지만 다른 점" 열을 꼭 읽는다.

## 기본 구조
| 언리얼 | 유니티 | 비슷하지만 다른 점 |
|---|---|---|
| Actor | GameObject | GameObject는 기능이 거의 없는 "그릇". 모든 동작은 컴포넌트가 담당 |
| ActorComponent / SceneComponent | Component / MonoBehaviour | 유니티는 Transform이 항상 1개 붙어 있음. 상속보다 컴포넌트 조합이 기본 |
| Blueprint 클래스 | Prefab | Prefab은 "설정이 끝난 GameObject 묶음"이지 새 클래스가 아님. 로직은 C# 스크립트 |
| Child Actor / Attach | Transform 부모-자식 계층 | 계층 구조가 씬의 기본 조직 방식 |
| Level / World | Scene | 여러 씬을 Additive로 동시 로드 가능 |
| Level Streaming / World Partition | Additive Scene Loading / Addressables | 자동 스트리밍은 기본 제공 안 됨 |
| GameMode / GameState | 없음 (직접 설계) | 보통 부트스트랩 씬 + 매니저 오브젝트 또는 순수 C# 서비스로 구성 |
| Subsystem | 없음 (직접 설계) | ScriptableObject 싱글턴, static 서비스, `RuntimeInitializeOnLoadMethod` 등으로 대체 |
| PlayerController / Pawn | 없음 | Input System + 직접 만든 컨트롤러 컴포넌트 |
| DataAsset / DataTable | ScriptableObject | 에셋으로 저장되는 데이터 객체. 런타임에 값을 바꾸면 에디터에선 저장됨에 주의 |
| UPROPERTY(EditAnywhere) | `[SerializeField]` | 직렬화 가능한 필드만 인스펙터에 노출 |
| Soft Object Reference | Addressables / `AssetReference` | 직접 참조(필드)는 씬 로드 시 함께 로드됨 |

## 생명주기
| 언리얼 | 유니티 |
|---|---|
| Constructor / PostInitializeComponents | `Awake()` (생성자 사용 금지) |
| BeginPlay | `Start()` (첫 프레임 전), `OnEnable()` (활성화될 때마다) |
| Tick | `Update()` / `FixedUpdate()`(물리) / `LateUpdate()`(카메라) |
| EndPlay / BeginDestroy | `OnDisable()` / `OnDestroy()` |
| Tick Group / 우선순위 | Script Execution Order, `[DefaultExecutionOrder]` |

## 언어 (C++ → C#)
| C++ / 언리얼 | C# / 유니티 | 주의 |
|---|---|---|
| UObject GC + 수동 메모리 | .NET GC | 할당이 곧 GC 스파이크. Update 내 `new` 최소화 |
| 포인터 / TWeakObjectPtr | 참조 타입 | 파괴된 UnityEngine.Object는 `== null`이 true (오버로드). `?.`, `??`는 이를 무시하니 주의 |
| struct vs class (거의 동일) | struct=값 타입, class=참조 타입 | 의미가 완전히 다름. 복사 vs 공유 |
| Delegate / Multicast Delegate | `delegate`, `event`, `Action<T>`, UnityEvent | 구독 해제 안 하면 누수·파괴된 객체 호출 |
| Latent Action / Timer | Coroutine, `Awaitable`(Unity 6+), async/await | 코루틴은 GameObject 비활성화 시 중단 |
| TArray / TMap | `List<T>` / `Dictionary<K,V>` | |
| UE_LOG | `Debug.Log` | 빌드에도 남음. 조건부 컴파일 고려 |
| Hot Reload / Live Coding | Domain Reload | 스크립트 변경 시 static 상태 초기화. Enter Play Mode Options 설정에 따라 다름 |

## 시스템
| 언리얼 | 유니티 |
|---|---|
| Enhanced Input | Input System 패키지 |
| UMG | uGUI (Canvas) / UI Toolkit |
| Niagara | Particle System / VFX Graph |
| Material Editor | Shader Graph |
| Animation Blueprint | Animator Controller (Mecanim) |
| Collision Channel | Layer + Layer Collision Matrix |
| Gameplay Tags | 없음 (enum, ScriptableObject 등으로 구성) |
| Automation Test | Unity Test Framework (EditMode / PlayMode) |
| Unreal Insights | Profiler, Memory Profiler, Frame Debugger |

## 내가 추가한 매핑
| 언리얼 | 유니티 | 메모 |
|---|---|---|
