# km-board 리디자인 초안

기존 대시보드를 새 디자인으로 다시 그린 시안입니다.
**숫자는 전부 예시값이고 데이터 연결은 되어 있지 않습니다.**

```
redesign/
├─ README.md            이 파일
├─ PAGES.md             전체 페이지 목록 · 확정된 규칙
├─ index.html           2. 업체 대시보드
├─ overview.html        1. 전체 업체
├─ campaigns.html       3. 캠페인 · 소재
├─ keywords.html        4. 키워드 · 검색어   ← 데이터 정합성 수정 후 확정
├─ hourly.html          5. 시간대 · 요일
├─ todo.html            6. 할 일
├─ input.html           7. 데이터 관리
├─ design-system.html   참고 — 색 · 글자 · 부품 기준표
└─ sections/            대시보드를 붙일 수 있는 9조각으로 분할
   ├─ README.md         붙이는 순서
   └─ dash-01 ~ dash-09
```

## 올리는 법

저장소 **루트에 그대로 올리면 안 됩니다.** 파일명이 기존 페이지와 같아서
지금 돌아가는 대시보드를 덮어씁니다. 이 `redesign` 폴더째로 올리세요.

올린 뒤 `사이트주소/redesign/index.html` 로 확인할 수 있습니다.
되돌리려면 `redesign` 폴더만 지우면 됩니다.

## 확정된 것

| 항목 | 값 |
|---|---|
| 글씨체 | Pretendard (jsDelivr CDN) |
| 화면 순서 | 전체 업체 → 대시보드 → 캠페인 → 키워드 → 시간대 → 할 일 → 데이터 관리 |
| 강조색 | `#8b7cff` — 선택 · 링크 · 브랜드 **전용** |
| 성과색 | 초록 `#3ddc97` / 주황 `#f5a524` / 빨강 `#ff6b85` — 좋고 나쁨은 이 셋으로만 |
| 숫자 | `font-variant-numeric: tabular-nums`, 표에서 우측 정렬 |
| 기준 폭 | 1440px |

전체 토큰은 `design-system.html` 참고.

## 이번 개편의 핵심

**분석·판단 층을 화면이 대신 읽어주게 한 것**입니다.

- `sections/dash-04-alerts.html` — CPA 상승을 클릭단가와 전환율 기여도로 쪼개 막대로 표시
- `sections/dash-07-campaign-insight.html` — 시간대와 키워드를 캠페인 단위로 묶어 제안
- `campaigns.html` — 제안 실행 추적 (적용함 체크)
- `overview.html` — 14개 계정 중 확인이 필요한 곳만 위로

## 알려진 이슈

`keywords.html`은 저장된 키워드 합계가 대시보드 합계와 어긋나는 문제
(캠페인별 상위 25개만 저장하던 설정)가 있어 수집기 수정 중입니다.
수정 후 숫자를 맞춰야 확정됩니다.
