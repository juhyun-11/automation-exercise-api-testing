# API Test Cases

## Verify Login

| TC ID | Scenario | Test Condition | Expected Result | Actual Result | Result |
|---|---|---|---|---|---|
| VL-01 | Valid Credential | Valid email + Valid password | responseCode 200 / User exists! | responseCode 200 / User exists! | PASS |
| VL-02 | Invalid Password | Valid email + Wrong password | responseCode 404 / User not found! | responseCode 404 / User not found! | PASS |
| VL-03 | Missing Password | Password parameter 미전송 | responseCode 400 / Missing parameter | responseCode 400 / Missing parameter | PASS |
| VL-04 | Empty Password | password="" | 명시적 스펙 없음 | responseCode 404 / User not found! | Observed |
