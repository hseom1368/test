# Fable 5 vs 이전 모델 — 동일 프롬프트 비교 (GIF)

질문: "GIF까지 존재하는 사례 중, **Fable 5 이전 모델로 같은 프롬프트**를 줬을 때 결과를 **비교**한 사례가 있나?"
답: **있습니다.** 가장 잘 정리된 검증이 아래 yukurash의 arena 저장소이며, **GIF가 GitHub에 공개**돼 있어 그대로 받고 좌우 비교본으로 합성했습니다.

> ⚠️ 다른 비교 사례(아래 "추출 불가" 참고)는 원본이 X·YouTube에 있어 이 환경에서 직접 추출할 수 없었습니다. arena는 GitHub 호스팅이라 가능했습니다.

## 출처
- **저장소:** https://github.com/yukurash/fable5-vs-opus48-arena
- **라이브 데모(전 성과물 직접 조작 가능):** https://yukurash.github.io/fable5-vs-opus48-arena/
- **검증 규칙:** 완전히 동일한 프롬프트를 **1턴·인간 개입 없이**(Claude Code 헤드리스 `claude -p`) 투입. 각 런은 동일한 고정 시작 상태(git `base`)에서 실행. 모델은 서로의 존재도, 채점 기준(숨은 테스트)도 모름.

## 비교 종목 & 프롬프트

### Task C-1 — "절대 누르면 안 되는 버튼" (자유 연출)
3줄 프롬프트만 주고 발상·연출을 겨룸 (`prompt_c1_do-not-press-button.md`):
> 「絶対に押してはいけないボタン」のWebサイトを作ってください。静的な HTML/CSS/JS のみで、index.html をブラウザで開けば動くように。外部ライブラリCDN可。あとはすべてお任せ。面白くしてください。
> (= "'절대 누르면 안 되는 버튼' 웹사이트를 만들어라. 정적 HTML/CSS/JS만, index.html로 바로 동작, CDN 허용. 나머지는 전부 맡긴다. 재미있게.")

### Task C-2 — Windows 95 풍 데스크톱 (규정 연출)
14개 요건(창 시스템·그림판·지뢰찾기·메모장·휴지통 등) spec을 주고 구현 (`prompt_c2_win95-desktop.md`, `spec_c2_win95.md`).

## 결과 요약 (저자 측정값)

**C-1 (버튼, 각 2런)**
| | Fable 5 run1 | Fable 5 run2 | Opus 4.8 run1 | Opus 4.8 run2 |
|---|---|---|---|---|
| 실행시간 | 427s | 408s | 197s | 115s |
| 비용 | $2.77 | $2.49 | $0.60 | $0.36 |
| 규모 | 3파일/1,297줄 | 3파일/1,411줄 | 1파일/672줄 | 1파일/412줄 |

**C-2 (Win95, 기능 14점 만점)**
| | Fable 5 run1 | Fable 5 run2 | Opus 4.8 run1 |
|---|---|---|---|
| 기능 점수 | **0/14** ⚠️ | **14/14** | **14/14** |
| 실행시간 | 981s | 1,664s | 772s |
| 비용 | $5.64 | $10.75 | $3.16 |

⚠️ **흥미로운 실패 사례:** Fable 5 run1은 기동을 담당하는 `shell.js`를 **빼먹은 채 납품**해 BIOS 부팅 화면에서 멈춤(작성된 2,327줄 자체 품질은 높았음). run2에서는 완동품 납품. → PPT에서 "강력하지만 1턴 신뢰성 변동" 메시지로 활용 가능.

**참고(객관 채점 Task A, ToDo REST API):** 숨은 테스트 27건 → Fable 5 **27/27**, Opus 4.8 **27/27** (동점). 합계 9런 완주율 Fable 4/5, Opus 4/4. 총비용 Fable $23.88 vs Opus $5.74.

## GIF 파일

**`side-by-side/` — 좌우 비교본(라벨: Fable 5 | Opus 4.8), PPT 바로 사용**
- `07_compare_c1_button_fable5_vs_opus48.gif` — 버튼 run1 비교
- `09_compare_c1run2_button_fable5_vs_opus48.gif` — 버튼 run2 비교
- `08_compare_c2_win95_fable5_vs_opus48.gif` — Win95 (Fable 5 run2 완동품 vs Opus 4.8 run1)

**`originals/` — 저자가 만든 원본 GIF 7종(개별 화면)**
- `c1-fable5-run1-v2.gif`, `c1-fable5-run2-v2.gif`, `c1-opus48-run1-v2.gif`, `c1-opus48-run2-v2.gif`
- `c2-fable5-run2-demo-v2.gif`(완동품), `c2-opus48-run1-demo-v2.gif`(완동품), `c2-fable5-run1-broken-v2.gif`(BIOS 멈춤)

---

## 같은 성격의 다른 비교 사례 (원본 X/YouTube → 직접 추출 불가, 링크만)
- **물리 시뮬 비교** Fable 5 vs Opus 4.8 — 동일 프롬프트 3종(이중진자/골턴보드/회전드럼 물 WCSPH), 라이브러리 없는 HTML5. Fable 쪽이 물 시뮬에서 더 안정적. (@atomic_chat_hq) https://x.com/atomic_chat_hq/status/2064488894398161377
- **Physarum 점균 시뮬** Fable 5 Max vs GPT-5.5 Very High — 동일 과제, 알고리즘 품질은 Fable 우세·시간/비용은 GPT 우세. (@AlicanKiraz0) https://x.com/AlicanKiraz0/status/2064424400494186867
- **"같은 앱 빌드" 영상** Opus 4.8 vs Fable 5 (RAW RESULTS) — YouTube: https://www.youtube.com/watch?v=TzJCly4YgDQ
- **포트폴리오 비교(렌더 가능 후보)** 같은 이력서로 생성 — Fable 5: https://github.com/GunalHincal/portfolio-fable5 / Opus 4.8: https://github.com/GunalHincal/portfolio-opus4.8
