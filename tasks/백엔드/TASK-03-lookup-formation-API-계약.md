# 백엔드 TASK-03: lookup formation API 계약

## 목적

프론트엔드가 `position_key` 기반으로 현재 포지션과 formation metadata를 안정적으로 조회할 수 있는 API 계약을 만든다.

## 오너

- 백엔드 리드

## 선행 조건

- `TASK-01-canonical-serialization과-key-규칙-정의.md`
- `TASK-02-Position-Graph-스키마와-upsert-정책.md`

## 입력물

- UX/UI의 상태 정의 초안
- 프론트엔드의 필수 응답 필드 요구사항

## 작업 내용

1. 현재 포지션 lookup API의 입력과 출력 필드를 고정한다.
2. 미등록, 성공, 시스템 오류 응답의 상태 구분 방식을 정의한다.
3. formation metadata 조회/수정 API의 필드 구조를 확정한다.
4. outgoing edge와 현재 PositionNode ID를 포함할지 여부를 문서화한다.

## 산출물

- API 계약서
- 응답 예제 3종
- 필드 사전

## 수용 기준

- 프론트엔드가 추가 질의 없이 metadata 패널을 구현할 수 있다.
- QA가 응답 예제만으로 lookup/오류/미등록 검증 시나리오를 작성할 수 있다.
- sequence string 기반 조회가 계약에서 배제된다.

## 차단 시 에스컬레이션

- 성공 응답과 미등록 응답이 구분되지 않으면 계약 승인을 중단한다.
