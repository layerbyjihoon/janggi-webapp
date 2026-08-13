# QA TASK-01: fixture 기반 검증 전략

## 목적

FE와 BE가 같은 포지션에서 같은 `position_key`를 산출하는지 비교할 공용 검증 전략을 만든다.

## 오너

- QA 리드

## 선행 조건

- 프로젝트 관리 Gate B 초안
- 백엔드 fixture 초안

## 입력물

- `docs/세부 기획서 - QA.md`
- canonical serialization 명세

## 작업 내용

1. FE/BE 공통 fixture 비교 절차를 정의한다.
2. key mismatch 발생 시 어떤 레이어를 먼저 확인할지 triage 순서를 정한다.
3. lookup 성공, 미등록, 오류 응답 검증용 샘플 세트를 정리한다.
4. 자동화 우선순위를 key 일치성 중심으로 묶는다.

## 산출물

- fixture 비교 체크리스트
- triage 순서표
- 자동화 우선순위 메모

## 수용 기준

- 같은 fixture에 대한 비교 절차가 재현 가능하다.
- key mismatch를 FE/BE 어느 쪽 문제인지 좁혀갈 수 있다.
- 프로젝트 관리의 Gate B와 검증 전략이 연결된다.

## 차단 시 에스컬레이션

- fixture 입력 정의가 불완전하면 테스트 설계 완료로 처리하지 않는다.
