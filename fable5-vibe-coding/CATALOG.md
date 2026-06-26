# Claude Fable 5 — 바이브 코딩 사례 카탈로그 (PPT용)

> 작성일 2026-06-26 · Fable 5 출시(2026-06-09) 직후 공개된 "바이브 코딩" 사례 모음.
> **Part 1** = 내가 직접 렌더링해 **GIF로 추출한** 오픈소스 데모(+사용 프롬프트).
> **Part 2** = 웹에서 검색된 사례 전체 목록(제작자·원본 링크·공개 프롬프트). 원본 영상은 X/YouTube에 있어 이 환경에서 직접 추출 불가 → 링크로 제공.

---

## ⚠️ 먼저 읽어주세요 — GIF 추출 관련 제약

- 검색된 사례의 **원본 데모 영상 대부분은 X(트위터)·YouTube에 게시**되어 있습니다.
- 이 작업 환경의 네트워크 정책이 **GitHub 계열 호스트만 허용**하고 X·YouTube·imgur 등은 차단(403)해서, **그 원본 영상 파일은 직접 다운로드/추출할 수 없었습니다.**
- 대신, **코드가 GitHub에 공개된 Fable 5 데모**를 직접 받아 **헤드리스 Chromium으로 실행→화면 녹화→GIF 변환**했습니다. (`gifs/` 폴더의 6개)
  - 즉 Part 1의 GIF는 "원본 바이럴 클립"이 아니라 **동일한 공개 코드를 내가 재실행해 만든 화면**입니다. 내용·결과물은 동일합니다.
- Part 2의 사례들은 **원본 X 링크**를 그대로 드리니, PPT에 넣을 클립은 해당 링크에서 직접 캡처(예: macOS의 화면 기록 → GIF 변환)하시면 됩니다.

---

## Part 1 — 직접 추출한 GIF (6개) + 프롬프트

| # | 파일 | 사례 | 제작자 / 저장소 | 프롬프트 공개 |
|---|------|------|----------------|:---:|
| 1 | `gifs/01_redcliffs_3d_battle.gif` | 적벽대전 208 — 전(全) 3D 전장 재현 | [yazelin/red-cliffs-3d](https://github.com/yazelin/red-cliffs-3d) | ✅ 전문 |
| 2 | `gifs/02_flappy_3d_aetherwing.gif` | AETHERWING — 3D 플래피버드 | [SaiAmartya/flappy-bird-3D](https://github.com/SaiAmartya/flappy-bird-3D) | ⚠️ 자율 빌드 |
| 3 | `gifs/03_minecraft_hollow.gif` | Hollow — 브라우저 마인크래프트 클론 | [monsilaro/minecraft.js](https://github.com/monsilaro/minecraft.js) | ⚠️ 부분 |
| 4 | `gifs/04_elvenwood_forest.gif` | Elvenwood — 절차적 엘프 숲 (100% 코드 생성) | [huntsyea/elvenwood](https://github.com/huntsyea/elvenwood) | ✅ 요지 |
| 5 | `gifs/05_amazonia_living_archive.gif` | Amazônia: The Living Archive — 3D 스크롤리텔링 | [SheinRG/amazonia](https://github.com/SheinRG/amazonia) | ⚠️ 미공개 |
| 6 | `gifs/06_calculus_3d_explorer.gif` | Calculus 3D Explorer — 인터랙티브 미적분 | [pianomanstride/calculus](https://github.com/pianomanstride/calculus) | ✅ 요지 |

### 1. 적벽대전 3D 전장 (red-cliffs-3d)
- **제작자:** yazelin · **도구:** Claude Code의 Fable 5 모델(effort: medium), 단일 HTML, 한 번의 대화
- **라이브:** https://yazelin.github.io/red-cliffs-3d/
- **원본 프롬프트 (저자가 "一字未改 = 한 글자도 안 고침"이라 명시):**
  > 以電視特別節目的3D運鏡方式和特效來介紹赤壁之戰，把地形和地名、船艦等標示出來；曹操為藍色，孫權為紅色，劉備為綠色，以時間軸來顯示戰爭過程中各軍勢的陣型、移動方向、將領姓名、重大事件、各軍戰力、要有計策發動效果、槍炮和天氣、軍隊、船艦狀態的特效，看起來要像遊戲讓玩家可互動或歷史節目自動播放，應可自由移動照相機角度。各軍軍旗需可清楚識別。使用單一html檔完成，並部署到我的github repo pages 上。最終交付給我pages連結。
  - (요약 번역) "TV 특집 다큐의 3D 카메라 워킹과 특효로 적벽대전을 소개하라. 지형·지명·함선을 표시하고 조조=파랑, 손권=빨강, 유비=초록. 타임라인으로 진형·이동방향·장수 이름·주요 사건·전력·계략 발동 효과·무기/날씨/함대 상태를 보여주고, 게임처럼 상호작용 가능하거나 다큐처럼 자동 재생되게. 카메라 자유 이동, 군기 식별 가능. **단일 HTML 한 파일**로 완성해 GitHub Pages에 배포하고 링크를 달라."
  - 모델이 ~1900줄 단일 HTML을 한 번에 작성하고, 스스로 브라우저로 자가 검증하며 6개 버그를 자체 수정. ("槍炮" 요구에 대해 서기 208년엔 화포가 없다며 활·화살·화공으로 대체하고 페이지에 명시)

### 2. AETHERWING — 3D 플래피버드 (flappy-bird-3D)
- **제작자:** SaiAmartya · **저자 표기:** *"created by Claude Fable 5 — designed, coded, play-tested, security-tested, and deployed autonomously."*
- Three.js 시네마틱 측면 카메라, 번들러/빌드 없는 순수 ES 모듈. 명시적 프롬프트 전문은 미공개(자율 빌드).

### 3. Hollow — 마인크래프트 클론 (minecraft.js)
- **제작자:** monsilaro · 복셀 월드(바이옴/청크/주야/체력), three.js. 1인칭. 프롬프트 전문 미공개(README에 "one-shot" 스크립트 언급).

### 4. Elvenwood — 절차적 엘프 숲 (elvenwood)
- **제작자:** huntsyea · **라이브:** https://elvenwood-five.vercel.app
- 텍스처/모델/에셋 없이 **단일 시드로 100% 코드 생성**. README 요지: *"Anthropic Fable 5와 three.js 실력 테스트. 월드 디자인·절차적 생성·셰이더·FPS 컨트롤·모바일 대응·성능·배포 전부를 Fable 5가 Claude Code에서 병렬 서브에이전트 함대를 지휘하며 라이브 스크린샷으로 비주얼을 반복 개선해 빌드. 사람이 코드를 쓰거나 고치지 않음."*

### 5. Amazônia: The Living Archive (amazonia)
- **제작자:** SheinRG · React + react-three-fiber + GSAP/Lenis 스크롤리텔링 3D 사이트(우림 보존 테마). 명시적 프롬프트 미공개.

### 6. Calculus 3D Explorer (calculus)
- **제작자:** pianomanstride · Three.js + KaTeX, 빌드 없음, EN/DE 이중언어, 7개 레벨.
- **프롬프트 (README 인용, 요지):** Claude Code `/loop`(동적·자기 페이스 모드)에서 **단일 지시**로 빌드 —
  > *"Build a 3D browser app that explains calculus playfully, from simple to advanced"* ("쉬운 것부터 고급까지, 미적분을 재미있게 설명하는 3D 브라우저 앱을 만들어라")
  - Fable 5가 8회 자율 반복(레벨당 1회)으로 스캐폴딩→레벨별 구현→자동 스모크 테스트 검증을 수행. 이중언어는 후속 프롬프트 1개로 추가.

---

## Part 2 — 웹 검색 사례 전체 목록 (원본 링크 + 프롬프트)

> 출처: 큐레이션 리포 [awesome-claude-fable-5](https://github.com/Anil-matcha/awesome-claude-fable-5)(X 게시물 88건 정리) + 개별 검색.
> 아래는 그중 **"바이브 코딩으로 무언가를 만든" 빌드/데모 사례**만 추린 것입니다(벤치마크·가격 논평 케이스는 제외).
> ▶ 데모 영상이 있는 항목은 원본 X 링크의 첨부 영상에서 직접 GIF 캡처하세요.

### 게임 · 인터랙티브
| 사례 | 제작자 | 원본 링크(영상 포함) | 프롬프트 |
|------|--------|------|------|
| 블랙홀 렌즈 효과 시뮬(Three.js, 60fps 단일 HTML, 원프롬프트) | @deveshcodes_ | https://x.com/deveshcodes_/status/2064437742189379745 | 요지 공개: "실시간 black hole lensing sim in Three.js" (중력 렌즈·도플러 가속 강착원반·광자구·색수차·절차적 별자리) |
| macOS풍 웹 OS(단일 HTML, 드래그 창·터미널·사운드 신디사이저·내장 마인크래프트) | @intheworldofai | https://x.com/intheworldofai/status/2064421915347812672 | 전문 미공개 |
| 손가락 트래킹 다이노 러너(11~12분, 914K토큰, 629줄) | @ai_for_success | https://x.com/ai_for_success/status/2064413182396108932 | 요지: "build a Dino runner game with finger tracking" |
| 마리오카트64풍 레이싱(2문장 프롬프트→4맵·3모드·음악·UI, ~15분) | @kieradev | https://x.com/kieradev/status/2064482704763085202 | 2문장(전문 미공개) |
| 터미널 마인크래프트(Rust, TUI, `cargo install termcraft-3d`) | @vikvang1 | https://x.com/vikvang1/status/2064500731848319303 | 전문 미공개 |
| 마인크래프트 클론(37분, ~3K줄, $12, 바이옴·동굴·광물·주야·몹) | @ydamitcodes | https://x.com/ydamitcodes/status/2064536076518363353 | "원프롬프트"(전문 미공개) |
| 이스탄불 플랫폼 게임(스프라이트시트+1지시→게임) | @ozansihay | https://x.com/ozansihay/status/2064973170780545535 | GPT Image 2 스프라이트시트를 참조로 "이미지를 게임으로" |
| 비즈니스 3D 도시 대시보드(원프롬프트, 창고·드론·주문 시각화) | @noisyb0y1 | https://x.com/noisyb0y1/status/2064970594118967756 | 전문 미공개 |
| HOLE.io풍 3D 게임 원샷(Three.js) | @thebuggeddev | https://x.com/thebuggeddev/status/2064968106104275008 | 전문 미공개 |
| 슈퍼마리오풍 게임(~2M토큰, 원샷) | @pankajkumar_dev | https://x.com/pankajkumar_dev/status/2064941888990593416 | "build a Super Mario Nintendo-style game" |
| Namma Metro 시뮬(벵갈루루 지하철 안에서 제작) | @anilbpai | https://x.com/anilbpai/status/2064927784833790091 | 전문 미공개 |
| Dusk Drive — 저폴리 드라이빙 게임(원프롬프트, 인간 편집 0) | @VincentLogic | https://x.com/VincentLogic/status/2064921358359011684 | 전문 미공개 |
| GTA 2 클론(2시간) | @techhalla | https://x.com/techhalla/status/2064682080445898957 | 전문 미공개 |
| DataEmpire — 웹 분석을 게임으로 | @marclou | https://x.com/marclou/status/2065029898243318093 | 전문 미공개 |

### 비주얼 · 3D · 디자인
| 사례 | 제작자 | 원본 링크 | 프롬프트 |
|------|--------|------|------|
| 스위스 레버 시계 무브먼트(Three.js, 실제 기어비 18000bph, 동작하는 이스케이프먼트, 비전 루프 자가검증) | @quanghuynt14 | https://x.com/quanghuynt14/status/2064509430650065278 | 요지: "full Swiss lever movement in Three.js" |
| 프렌즈 모니카 아파트 1인칭 3D(평면도 기반, $12) | @scottstts | https://x.com/scottstts/status/2064464351906673029 | **전문 공개**: "in @threejs, create a first person pov navigable 3d scene of the iconic Monica's apartment from tv show Friends correctly based on this floor plan, stay true to the original look and feel, use warm lighting" |
| 태양계 시뮬(물리 원리로 궤도 도출→일식 예측) | @tetumemo | https://x.com/tetumemo/status/2064477582930989357 | **전문 공개**: "Build a solar system simulation by deriving planetary orbital motion from the basic principles of physics and using that to predict solar eclipses." |
| MVMT 이커머스 이메일 목업(원프롬프트, 무편집) | @ecomchasedimond | https://x.com/ecomchasedimond/status/2064454139225297091 | **전문 공개**(매우 김 — 아래 `prompts/` 참조) |
| 스크린샷→GitHub UI 재현(Kilo Code, 10분, $4.07) | @coldopn | https://x.com/coldopn/status/2064435234465087638 | "GitHub UI 스크린샷을 붙여넣고 실기능까지 재현하라" |
| 피그마 캡처→랜딩페이지 클론 | @mikefutia | https://x.com/mikefutia/status/2065537778516205856 | 전문 미공개 |

### 장기 실행 · 대형 빌드
| 사례 | 제작자 | 원본 링크 | 비고 |
|------|--------|------|------|
| Spawn 5.0 게임엔진(1,687프롬프트·102세션·약 1주, 물리엔진·GI·100만 파티클·MMO 넷코드) | @jsnnsa | https://x.com/jsnnsa/status/2064420561078693941 | 대형 프로젝트 |
| Tenex 사이트 재구축 + 80페이지 신규 사이트 + 클립 자동화 파이프라인 | @JJEnglert | https://x.com/JJEnglert/status/2064469635190170105 | 릴레이 워크플로 |
| 인프라 장애 진단→수정 PR 자동 생성(Pod 로그·Cloud SQL·이미지 다이제스트 비교) | @ayushagarwal | https://x.com/ayushagarwal/status/2064422467557564862 | 에이전트 |
| 대형 PR 리뷰(74파일/+3,705/-1,246 → 실제 버그 3건 발견) | @ryanrhughes | https://x.com/ryanrhughes/status/2064411147076534705 | 코드리뷰 |
| 월드컵 예측기(샌드박스) | @upstash | https://x.com/upstash/status/2064702195333820846 | 데모 |
| Claude Code에서 웹앱 3개 | @0x3b33 | https://x.com/0x3b33/status/2064948399300825439 | 데모 |

> 추가로 공개 GitHub 데모(렌더 가능): [Braffolk/fable5-world-demo](https://github.com/Braffolk/fable5-world-demo) — Three.js/WebGPU 대규모 3D 월드(요세미티 등). **WebGPU 필수**라 헤드리스 환경에서는 렌더 불가해 GIF 미생성(실기기에서 라이브로 캡처 권장).

---

## 출처
- awesome-claude-fable-5 (큐레이션, 88사례): https://github.com/Anil-matcha/awesome-claude-fable-5
- Anthropic 공식 발표: https://www.anthropic.com/news/claude-fable-5-mythos-5
- 렌더링한 데모 저장소: 위 Part 1 표의 각 GitHub 링크
