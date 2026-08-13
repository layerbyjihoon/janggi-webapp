# 프론트엔드 TASK-02: lookup과 metadata 패널 연결

## 목적

현재 `position_key`에 대한 lookup 결과를 사용자에게 `primary_formation_name` 중심으로 정확히 보여주는 UI 상태를 정의한다.

## 오너

- 프론트엔드 리드

## 선행 조건

- `TASK-01-position-loop와-serialization-정렬.md`
- UX/UI 상태 명세 초안
- 백엔드 응답 예제 초안

## 입력물

- metadata 패널 요구사항
- lookup 성공, 미등록, 오류 응답 예제

## 작업 내용

1. lookup 결과를 UI 상태 모델로 변환하는 규칙을 정리한다.
2. `primary_formation_name`, `formation_names[]`, 설명 필드 표시 순서를 정의한다.
3. 로딩, 미등록, 오류 상태를 서로 분리된 상태 머신으로 설계한다.
4. 한 수 직후 언제 포진명 영역이 갱신되는지 타이밍을 문서화한다.

## 산출물

- metadata 패널 상태 표
- lookup 결과 매핑 규칙
- 상태 전이 다이어그램 또는 텍스트 명세

## 수용 기준

- 등록 포지션과 미등록 포지션이 오해 없이 구분된다.
- QA가 포진명 갱신 타이밍을 기준으로 검증 시점을 잡을 수 있다.
- 엔진 오류가 lookup 오류처럼 보이지 않는다.

## 차단 시 에스컬레이션

- 응답 예제로 상태 구분이 불가능하면 백엔드 계약 보완을 요청한다.
