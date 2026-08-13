# 프로젝트 관리 TASK-02: Gate B position_key 계약 동결

## 목적

FE, BE, QA가 같은 포지션을 같은 `position_key`로 다루도록 계약을 동결한다.

## 오너

- PM

## 선행 조건

- `TASK-01-Gate-A-도메인-해석-동결.md`

## 입력물

- 백엔드의 canonical serialization 초안
- 프론트엔드의 position 계산 요구사항
- QA의 fixture 요구사항

## 작업 내용

1. canonical serialization 범위와 `side_to_move` 포함 여부를 결정 회의 안건으로 묶는다.
2. `position_key` 생성 규칙, canonical representation 보관 여부, 동일성 검증 방식을 잠근다.
3. FE, BE, QA가 재사용할 fixture 포맷과 승인 절차를 문서화한다.
4. 결정 이후 변경 요청이 들어오면 영향 범위를 추적한다.

## 산출물

- Gate B 결정 로그
- 공용 fixture 승인본
- 계약 변경 영향도 메모

## 수용 기준

- FE와 BE가 같은 fixture에서 같은 `position_key`를 산출한다.
- QA가 fixture를 기반으로 자동화 테스트를 설계할 수 있다.
- 계약 변경 시 재작업 범위를 PM이 추적할 수 있다.

## 차단 시 에스컬레이션

- `position_key` 규칙이 두 번 이상 뒤집히면 구현 잠금과 재승인 절차를 연다.
