# 프론트엔드 TASK-03: transposition 반영과 상태 구분

## 목적

서로 다른 수순으로 같은 포지션에 도달해도 UI가 동일 PositionNode 기준으로 메타데이터를 표시하도록 검증한다.

## 오너

- 프론트엔드 리드

## 선행 조건

- `TASK-02-lookup과-metadata-패널-연결.md`
- 백엔드 transposition fixture 수신

## 입력물

- transposition 샘플 세트
- UX/UI의 transposition 표현 가이드

## 작업 내용

1. Path A, Path B가 같은 포지션에 도달할 때 같은 lookup 결과를 쓰도록 상태 갱신 규칙을 점검한다.
2. 이전 이동 이력이 metadata 표시에 개입하지 않도록 캐시 경계를 정리한다.
3. transposition 상태와 일반 탐색 상태의 UI 차이를 정리한다.
4. 미등록, 로딩, 오류 상태와 transposition 표시가 섞이지 않도록 규칙을 적는다.

## 산출물

- transposition 처리 체크포인트
- 캐시 오염 방지 메모
- 상태 충돌 방지 규칙

## 수용 기준

- 경로가 달라도 같은 포지션에서 같은 metadata가 보인다.
- sequence history 기반 표시 로직이 남아 있지 않다.
- QA가 transposition 재현 절차를 문서만 보고 실행할 수 있다.

## 차단 시 에스컬레이션

- 동일 포지션에서 다른 metadata가 보이면 즉시 결함을 P1로 승격한다.
