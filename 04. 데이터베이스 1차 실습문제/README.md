# 데이터베이스 1차 실습문제

## 📝 문제 목록

### 문제 1: 매장별 월별 매출 분석
**매장의 월별 매출을 조회하는 SQL을 작성하세요.**  

🔹 **해결 방법**  
- `payment` 테이블에서 **결제 금액을 집계**  
- `결제 날짜(payment_date)`를 기준으로 **월별 데이터를 그룹화**  

🔹 **결과 화면**  
![문제 1 결과 화면]([https://github.com/user-attachments/assets/https://private-user-images.githubusercontent.com/193302801/409574649-7f4aac85-b4fc-4d67-a652-ab8ee05edb2f.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzg2NzY5NjcsIm5iZiI6MTczODY3NjY2NywicGF0aCI6Ii8xOTMzMDI4MDEvNDA5NTc0NjQ5LTdmNGFhYzg1LWI0ZmMtNGQ2Ny1hNjUyLWFiOGVlMDVlZGIyZi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMjA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDIwNFQxMzQ0MjdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mNWIwY2E5MWVmOWQ1YzY5MTJjY2JkMDRkYTgwZjJiODEzZDlhOTBmNzY5NDkzMGRmZGQ5N2M3YjRlMjZjZDQ3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.FbDY4a037o4r0f82txxYNSkpRYzyywaQt8YD3MQGH40)


---

### 문제 2: 특정 배우가 출연한 영화의 매출 기여도 분석
**특정 배우(예: "TIM HACKMAN")가 출연한 영화가 총 매출에 얼마나 기여했는지 조회하세요.**  

🔹 **해결 방법**  
1. **배우 ID 조회**  
   - `actor` 테이블에서 해당 배우의 ID를 조회  
2. **영화 목록 조회**  
   - `film_actor`와 `film` 테이블을 연결하여 해당 배우가 출연한 영화 목록 확인  
3. **매출 기여도 계산**  
   - `rental`과 `payment` 테이블을 조인하여 총 매출 기여도를 계산  

🔹 **결과 화면**  
`[결과 화면]`

---

### 문제 3: 가장 신속한 대여 및 반환 서비스 제공 매장 분석
**어떤 매장이 가장 신속하게 대여 및 반환 처리를 하는지 조회하세요.**  

🔹 **해결 방법**  
- 대여 및 반환 간의 시간 차이를 계산  
  - `AVG(TIMESTAMPDIFF(DAY, rental_date, return_date))` 사용  
  - `rental_date`와 `return_date`를 이용해 반환까지 걸린 시간을 평균으로 계산  

🔹 **결과 화면**  
`[결과 화면]`

---

### 문제 4: 대여되지 않은 영화 목록 찾기
**대여되지 않은 영화를 조회하세요.**  

🔹 **해결 방법**  
1. **대여된 영화와 대여되지 않은 영화 비교**  
   - `inventory` 테이블과 `rental` 테이블을 `LEFT JOIN`하여 대여되지 않은 영화 목록 조회  

🔹 **결과 화면**  
`[결과 화면] -> 43건 조회되어야 함`

---

### 문제 5: 고객의 활동성 분석
**고객의 대여 횟수와 평균 결제 금액을 기반으로 상위 5명의 VIP 고객을 조회하세요.**  

🔹 **해결 방법**  
- 고객별 대여 횟수 및 평균 결제 금액을 계산  
- `rental`과 `payment` 테이블을 `JOIN`하여 고객별 데이터를 집계  

🔹 **결과 화면**  
`[결과 화면]`

---

### 문제 6: 특정 카테고리의 대여 트렌드 분석
**특정 카테고리(예: "Action")의 대여 트렌드를 분석하여 월별 대여 횟수를 조회하세요.**  

🔹 **해결 방법**  
1. **카테고리 ID 조회**  
   - `category` 테이블에서 해당 카테고리 ID를 조회  
2. **월별 대여 횟수 집계**  
   - `film_category`와 `rental`을 `JOIN`하여 대여 데이터를 분석  

🔹 **결과 분석**  
`Action 장르의 결과`

---

### 문제 7: 특정 기간 동안 대여된 영화 목록
**특정 기간(예: 2005년 5월 1일부터 2005년 5월 31일) 동안 5회 이상 대여된 영화 목록과 대여 건수를 조회하세요.**  

🔹 **해결 방법**  
- `rental_date`를 기준으로 특정 기간 내 대여 데이터를 필터링  
- 서브쿼리(인라인 뷰) 사용하여 5회 이상 대여된 영화만 조회  

🔹 **결과 화면**  
`[결과 화면]`

---

### 문제 8: 고객의 평균 대여 간격 분석
**고객들이 평균적으로 얼마나 자주 영화를 대여하는지 분석하고,  
평균 대여 시간이 가장 짧은 고객 5명을 조회하세요.**  

🔹 **해결 방법**  
1. **대여 간격 계산**  
   - 동일 고객의 `rental_date`를 기준으로 대여 간격을 계산  
2. **인라인 뷰 사용**  
   - 고객별 평균 대여 시간을 구한 후 최단 대여 간격 상위 5명 출력  

🔹 **결과 화면**  
`[결과 화면]`

## 📢 출처
> **더조은컴퓨터아카데미, 빅데이터 기반 AI(인공지능) 서비스 개발자 취업캠프, 2024년 12월**

