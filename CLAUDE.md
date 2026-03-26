# Coupon Performance Dashboard

## 프로젝트 개요
- W12 YoY 쿠폰 매출 하락 사유 분석 대시보드
- GitHub Pages로 배포: `index.html` 단일 파일

## 데이터 소스
- 테이블: `socar-data.socar_biz_profit.profit_socar_reservation`
- 필터: `coupon_policy_id IS NOT NULL`
- 기준: 반납일(return_at_kst), ISOWEEK 12
- 단위: 백만원 (1e6 KRW)

## 핵심 지표 정의
- **GPM**: Profit / Revenue (%)
- **CM%**: Contribution Margin / Revenue (%)
- **매출(Revenue)**: profit_socar_reservation.revenue 컬럼 (렌트+수수료+유류비 등 합산, 할인 반영 후)

## 쿠폰 구조 변경 이력
- **#15445** `[특별할인] 대여요금 50% 할인 (4시간 이상)` (TARGET)
  → 2026년 **#16152~#16156** (NORMAL 시간대별 할인)으로 전환
  - #16152: 4~8시간 미만 40% 할인
  - #16153: 8~24시간 미만 45% 할인
  - #16154: 1박2일 50% 할인
  - #16155: 2박3일 55% 할인
  - #16156: 3박4일 60% 할인

## 대시보드 구성 원칙
- 매출(Revenue) 관점 우선, GP는 참고용
- "어디서 매출이 빠졌는지" 한눈에 볼 수 있는 구조
- 일별 Gap → Division별 → 쿠폰별 순서로 drill-down
