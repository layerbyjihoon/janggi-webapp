# QA TASK-03: transposition과 저장 무결성 회귀

## 목적

서로 다른 경로가 같은 PositionNode로 병합되는지, 중복 저장이 발생하지 않는지 회귀 관점으로 잠근다.

## 오너

- QA 리드

## 선행 조건

- `TASK-02-lookup과-상태-검증-시나리오.md`
- 백엔드 transposition 샘플 세트

## 입력물

- Path A / Path B 예제
- 중복 방지 규칙 문서

## 작업 내용

1. 같은 포지션 2경로 접근 시 같은 PositionNode ID를 반환하는지 검사 절차를 만든다.
2. 중복 node 생성 여부와 edge 무결성 검증 포인트를 정리한다.
3. formation metadata가 PositionNode 기준으로 동일하게 조회되는지 회귀 항목에 넣는다.
4. sequence history 기반 조회가 재유입되지 않았는지 점검한다.

## 산출물

- transposition 회귀 시나리오
- 저장 무결성 점검표
- 회귀 범위 메모

## 수용 기준

- 중복 node 미생성 여부를 시나리오로 재현할 수 있다.
- QA가 P1 여부를 transposition 결과만으로 판정할 수 있다.
- edge 저장과 formation metadata 조회가 분리돼 검증된다.

## 차단 시 에스컬레이션

- 동일 포지션 중복 저장이 1건이라도 재현되면 즉시 P1로 보고한다.
