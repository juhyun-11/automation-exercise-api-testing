# Automation Exercise API Testing

Postman으로 [Automation Exercise](https://automationexercise.com/api_list)의 API를 검증하는 REST API 테스트 프로젝트입니다.
요청 파라미터 조건(정상, 값 오류, 누락, 빈 값)별로 케이스를 나누고, 응답의 HTTP 상태 코드와 본문의 `responseCode`·메시지를 함께 검증했습니다.

## Test Targets

| API | 케이스 |
|---|---|
| `POST /api/verifyLogin` | VL-01~04: 정상 계정, 잘못된 비밀번호, 비밀번호 누락, 빈 비밀번호 |
| `POST /api/searchProduct` | SP-01~03: 정상 검색, 빈 검색어, 검색 파라미터 누락 |

케이스별 조건·기대 결과·실제 결과는 [docs/test-cases.md](docs/test-cases.md)에 정리했습니다.

## Project Structure

```text
├── docs/
│   └── test-cases.md                                # 테스트 케이스 및 실행 결과
└── postman/
    └── postman_collection.json                      # Postman 컬렉션
```

## Findings

- 테스트한 오류 응답에서는 HTTP 상태 코드가 200으로 반환되고, 본문의 `responseCode`(200, 400, 404 등)를 통해 업무 처리 결과가 구분되는 것을 확인했습니다.
- 로그인 API(VL-01~04)와 상품 검색 API(SP-01, SP-02)는 HTTP 상태 코드와 `responseCode`를 별도로 검증했습니다.
- 명시적 스펙이 없는 케이스(VL-04, SP-02)는 실제 응답을 관찰하고 `Observed`로 기록했습니다. 확인된 동작과 명세에 정의된 기대 결과를 구분하기 위해서입니다.
- 상품 검색 API에서는 응답의 `products`가 배열 형식인지 확인하고, 정상 검색(SP-01)에서는 상품이 1개 이상 반환되는지 검증했습니다.

## How to Run

1. [Automation Exercise](https://automationexercise.com/)에서 테스트용 계정을 직접 가입합니다.
2. Postman에서 `Import`로 `postman/postman_collection.json`을 불러옵니다.
3. 변수 `test_email`, `test_password`에 가입한 계정 값을 설정합니다. (컬렉션 파일에는 계정 정보가 포함되어 있지 않습니다.)
4. 컬렉션 `...` → `Run collection`으로 전체 실행합니다.

## Latest Result

- 실행 방식: Postman Collection Runner (로컬)
- 실행일: 2026-11-04
- 결과: 7개 요청 전체 통과 (명세 미정의 케이스는 관찰 결과 기준)

## Improvements

- 존재하지 않는 이메일 로그인 케이스(VL-05) 추가
- Newman을 이용한 GitHub Actions 연동
