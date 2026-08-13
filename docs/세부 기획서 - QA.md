# 한국 장기 연구 웹앱 세부 기획서 - QA

## 1. 역할 목적

QA의 목표는 `현재 포지션 lookup 실패`, `동일 포지션 중복 저장`, `문서형 UX 잔재`, `엔진 상태와 포진 lookup의 상호 오염`을 초기에 잡아내는 것이다.

## 2. 최고 우선순위 검증 축

- 같은 포지션이 항상 같은 `position_key`로 계산되는가
- 서로 다른 경로가 같은 PositionNode로 합쳐지는가
- 등록 포지션과 미등록 포지션이 정확히 구분되는가
- 엔진 실패가 formation lookup 흐름을 깨지 않는가

## 3. 테스트 레벨

### 요구사항 검증

- 문서에서 `새 연구`, `최근 연구`, `문서 저장` 같은 잔존 개념이 남아 있으면 반환한다.
- lookup 키가 `position_key`인지 확인한다.

### 기능 검증

- 수 적용
- 현재 포지션 serialization
- `position_key` 생성
- PositionNode lookup
- `primary_formation_name` 표시
- 미등록 포지션 표시
- transposition 병합
- 엔진 시작/중지/실패 상태

### 회귀 검증

- 동일 fixture에 대한 key 일관성
- 중복 node 미생성
- edge 무결성
- formation metadata 조회 일관성

## 4. 핵심 시나리오

### Scenario 1. 등록 포지션 lookup

- 시작 포지션에서 지정된 수를 둔다.
- 새 포지션의 `position_key`를 생성한다.
- lookup 결과를 확인한다.

기대 결과:

- 등록된 PositionNode가 반환되고 `primary_formation_name`이 즉시 표시된다.

### Scenario 2. 미등록 포지션 lookup

- 미등록 포지션으로 이동한다.

기대 결과:

- 시스템 오류가 아니라 `미등록 포지션` 상태가 표시된다.

### Scenario 3. Transposition 병합

- Path A와 Path B 두 경로로 같은 포지션에 도달한다.

기대 결과:

- 두 경로 모두 같은 PositionNode ID를 반환한다.
- 포진명과 메타데이터가 동일하다.

### Scenario 4. key 일치성

- FE와 BE가 같은 fixture 포지션에 대해 key를 계산한다.

기대 결과:

- 결과 key가 완전히 일치한다.

### Scenario 5. 엔진 실패 내성

- 엔진 초기화 실패 또는 분석 중지 상황을 만든다.

기대 결과:

- 포지션 lookup과 포진명 표시는 계속 동작한다.
- 사용자는 엔진 오류와 포진 미등록을 혼동하지 않는다.

## 5. 결함 우선순위 기준

### P1

- 같은 포지션이 서로 다른 key로 계산됨
- 동일 포지션이 중복 노드로 저장됨
- 등록 포지션이 미등록으로 표시됨
- 엔진 오류가 formation lookup 실패처럼 보임

### P2

- 별칭 노출 순서 오류
- 미등록 라벨 카피 문제
- transposition 시각 표현의 일관성 부족

## 6. 릴리즈 차단 조건

- P1 결함 1건 이상 존재
- FE/BE key fixture 결과가 다름
- transposition 시나리오에서 node 재사용이 실패함
- 문서형 UX 잔재가 남아 사용자 흐름을 혼동시킴

## 7. 사전 준비물

- canonical serialization 규칙 문서
- `position_key` golden fixture
- transposition 샘플 시나리오
- lookup 성공/미등록/오류 응답 예제

## 8. 자동화 우선순위

- FE/BE 공통 fixture 기반 key 비교 테스트
- PositionNode upsert 중복 방지 테스트
- transposition 병합 테스트
- lookup miss와 시스템 오류 구분 테스트

## 9. 완료 기준

- 핵심 시나리오 5개가 모두 통과한다.
- P1 결함이 0건이다.
- 동일 포지션 중복 생성이 재현되지 않는다.
- sequence history 없이도 formation lookup이 정확히 동작한다.
