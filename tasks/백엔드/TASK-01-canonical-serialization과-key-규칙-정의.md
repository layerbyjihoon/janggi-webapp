# 백엔드 TASK-01: canonical serialization과 key 규칙 정의

## 목적

같은 포지션이 항상 같은 canonical representation과 같은 `position_key`를 갖도록 규칙을 고정한다.

## 오너

- 백엔드 리드

## 선행 조건

- 프로젝트 관리 Gate A 완료

## 입력물

- `docs/세부 기획서 - 백엔드.md`
- `docs/세부 기획서 - 프로젝트 관리.md`

## 작업 내용

1. board 90칸 순회 순서와 기물 enum 표현을 확정한다.
2. `side_to_move` 표현과 canonical string 포맷을 정의한다.
3. 해시를 쓸 경우 원본 canonical representation 보관 방식을 결정한다.
4. FE와 QA가 재사용할 golden fixture 포맷을 설계한다.

## 산출물

- canonical serialization 명세
- `position_key` 생성 규칙
- golden fixture 초안

## 수용 기준

- 동일 포지션 샘플에서 같은 representation이 재현된다.
- FE가 같은 입력으로 같은 key를 만들 수 있을 정도로 규칙이 구체적이다.
- QA가 이 규칙으로 자동화 비교 테스트를 설계할 수 있다.

## 차단 시 에스컬레이션

- board 순회 순서나 `side_to_move` 표현에 합의가 안 되면 Gate B 승인 요청을 올린다.
