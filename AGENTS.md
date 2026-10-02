# AGENTS.md

이 저장소는 **대한민국 자치법규 데이터**다. 각 자치법규는 광역·기초 지자체 계층 아래의 `본문.md` 파일이다. 자세한 사용법은 스킬 [`ordinance-kr`](.agents/skills/ordinance-kr/SKILL.md)에 있다 — 조회·검색·지자체 경로 탐색 전에 읽어라.

## 구조

```
{광역}/{기초 또는 _본청 또는 _교육청}/{자치법규종류}/{자치법규명}/본문.md
```

- 자치법규종류: `조례` `규칙` `훈령` `예규` `고시` `의회규칙` (`기타`는 제외)
- 각 `본문.md` 상단에 YAML frontmatter(`자치법규ID`, `자치법규명`, `자치법규종류`, `지자체기관명`, `지자체구분`, `공포일자`, `본문출처`, `출처` 등).

## 반드시 지킬 것

- **commit hash는 안정 식별자가 아니다.** 정규화 규칙 개선 시 저장소 전체가 재구성되고 **force-push**된다. 장기 참조는 hash가 아니라 **`자치법규ID`/`자치법규일련번호` + `공포일자` + law.go.kr URL**로 하라. 동기화: `git fetch --all && git reset --hard origin/main`.
- **`공포일자` 신뢰**: 보정 시 `공포일자보정: true`, 원문은 `공포일자원문`에 보존. Git 날짜보다 frontmatter 값을 본다.
- **`본문출처: parsing-failed`**는 원천 XML에 본문 조문/부칙이 없는 경우다(별표·첨부만).

## 이 포크에 대하여

`saya6k/ordinance-kr`는 `legalize-kr/ordinance-kr`의 포크이며, GitHub Actions(`.github/workflows/sync-upstream.yml`)가 **매월 1회** 업스트림으로 **미러(hard-reset + force-push)**한다. 업스트림 콘텐츠를 통째로 덮어쓰므로 **데이터에 직접 커밋하지 마라 — 다음 동기화에 사라진다.** fork-local 파일(`AGENTS.md`, `.agents/`, sync 워크플로우)만 보존된다. 업스트림에는 어떤 쓰기도 하지 않는다(fetch 전용).
