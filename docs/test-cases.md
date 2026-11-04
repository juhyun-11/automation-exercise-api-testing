# API Test Cases

## Verify Login

| TC ID | Scenario | Test Condition | Expected Result | Actual Result | Result |
|---|---|---|---|---|---|
| VL-01 | Valid Credential | Valid email + Valid password | responseCode 200 / User exists! | responseCode 200 / User exists! | PASS |
| VL-02 | Invalid Password | Valid email + Wrong password | responseCode 404 / User not found! | responseCode 404 / User not found! | PASS |
| VL-03 | Missing Password | Password parameter 미전송 | responseCode 400 / Missing parameter | responseCode 400 / Missing parameter | PASS |
| VL-04 | Empty Password | password="" | 명시적 스펙 없음 | responseCode 404 / User not found! | Observed |

## Search Product

| TC ID | Scenario | Test Condition | Expected Result | Actual Result | Result |
|-------|----------|----------------|-----------------|---------------|--------|
| SP-01 | Valid Search | 존재하는 검색어 | responseCode 200 / 상품 목록 반환 | responseCode 200 / 상품 목록 반환 | PASS |
| SP-02 | Empty Search | search_product="" | 명시적 스펙 없음 | responseCode 200 / 상품 목록 반환 | Observed |
| SP-03 | Missing Parameter | search_product 파라미터 미전송 | responseCode 400 | responseCode 400 | PASS |
