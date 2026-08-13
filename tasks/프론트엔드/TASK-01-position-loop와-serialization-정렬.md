# 프론트엔드 TASK-01: position loop와 serialization 정렬

## 목적

수 적용 이후 새 board state를 계산하고, canonical serialization과 `position_key`를 일관되게 생성하는 클라이언트 루프를 설계한다.

## 오너

- 프론트엔드 리드

## 선행 조건

- 프로젝트 관리 Gate A 완료
- 백엔드의 canonical serialization 초안 수신

## 입력물

- `docs/세부 기획서 - 프론트엔드.md`
- 백엔드 golden fixture 초안

## 작업 내용

1. 보드 상태 갱신과 합법 수 적용 흐름을 정리한다.
2. `board[90] + side_to_move` 기반 serialization 계층 경계를 정의한다.
3. canonical representation에서 `position_key`를 만드는 경로를 문서화한다.
4. 실제 API 전까지 mock lookup으로 동작 검증이 가능한 상태를 만든다.

## 산출물

- position 계산 루프 설계 메모
- serialization 체크포인트 목록
- mock lookup 연결 계획

## 수용 기준

- 같은 포지션에서 항상 같은 key가 생성되는 흐름이 설명된다.
- 백엔드 fixture와 비교 가능한 단계가 분리돼 있다.
- QA가 key mismatch 발생 지점을 추적할 수 있다.

## 차단 시 에스컬레이션

- 백엔드 규칙과 다른 serialization 결과가 나오면 즉시 Gate B 재확인을 요청한다.
