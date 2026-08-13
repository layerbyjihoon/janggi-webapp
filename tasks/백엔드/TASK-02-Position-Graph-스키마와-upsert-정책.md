# 백엔드 TASK-02: Position Graph 스키마와 upsert 정책

## 목적

유저별 단일 Position Graph를 중복 없이 저장하는 데이터 구조와 upsert 정책을 확정한다.

## 오너

- 백엔드 리드

## 선행 조건

- `TASK-01-canonical-serialization과-key-규칙-정의.md`

## 입력물

- PositionNode, MoveEdge, PositionFormation 요구사항

## 작업 내용

1. `positions`, `position_edges`, `position_formations` 테이블 구조를 잠근다.
2. `UNIQUE INDEX positions(owner_id, position_key)`를 포함한 인덱스 전략을 문서화한다.
3. Position upsert와 Edge upsert의 중복 방지 규칙을 정의한다.
4. formation metadata와 edge 저장을 분리한 이유를 명확히 적는다.

## 산출물

- 스키마 초안
- upsert 정책 문서
- 중복 방지 규칙 메모

## 수용 기준

- 같은 포지션 중복 row 생성이 정책상 차단된다.
- transposition 시나리오에서 같은 PositionNode 재사용 경로가 설명된다.
- QA가 중복 생성 방지 테스트 포인트를 문서만으로 도출할 수 있다.

## 차단 시 에스컬레이션

- `owner_id + position_key` 고유성 보장이 불가능하면 데이터 모델 재검토를 요청한다.
