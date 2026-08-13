# 백엔드 TASK-04: fixture 테스트와 핸드오프

## 목적

FE와 QA가 바로 사용할 수 있는 fixture, transposition 예제, 검증 절차를 제공한다.

## 오너

- 백엔드 리드

## 선행 조건

- `TASK-03-lookup-formation-API-계약.md`

## 입력물

- canonical serialization 명세
- API 응답 예제

## 작업 내용

1. 동일 포지션 2경로 transposition fixture를 만든다.
2. lookup 성공, 미등록, 오류 응답 샘플을 정리한다.
3. 중복 node 미생성 검증 절차를 QA용으로 문서화한다.
4. 프론트엔드가 mock에서 실제 API로 전환할 때 필요한 결선 순서를 적는다.

## 산출물

- golden fixture 승인본
- transposition 샘플 세트
- FE/QA 핸드오프 노트

## 수용 기준

- FE와 QA가 같은 fixture를 재사용할 수 있다.
- 중복 저장 방지 검증이 사람이 아니라 절차로 설명된다.
- 세로 슬라이스 통합 전에 필요한 샘플이 모두 제공된다.

## 차단 시 에스컬레이션

- transposition 예제가 불충분하면 QA 승인 전까지 핸드오프 완료로 처리하지 않는다.
