# Swimmer's Plot Generator

임상 연구를 위한 Swimmer's Plot 생성 웹 앱입니다.

## 기능

- 엑셀(.xlsx, .xls) 및 CSV 파일 업로드
- 드래그 앤 드롭 지원
- Cohort별 그룹핑
- 치료 기간 또는 환자 ID 기준 정렬
- 반응색 구간 막대: C1D1~첫 평가 회색, 평가 시점부터 다음 평가까지 반응색(CR/PR/SD). PD는 빨간 ● 마커, 막대는 PD에서 끝
- 마지막 반응은 LastFU_date(또는 사망일)까지 유지된 것으로 표시. 회색 점선은 PD·drop-out 이후 생존 추적 구간에만
- ASCT 이벤트 마커 지원
- SVG/PNG 다운로드

## 데이터 형식

엑셀 파일에 다음 컬럼이 필요합니다:

| 컬럼명 | 설명 | 필수 |
|--------|------|------|
| Cohort | 코호트/Arm 구분 (A, B 등) | 선택 |
| Patient_ID | 환자 식별자 | 필수 |
| C1D1 | 치료 시작일 (Cycle 1 Day 1) | 필수 |
| Resp_date1 | 첫 번째 반응 평가일 | 필수 |
| Response1 | 첫 번째 반응 결과 (CR/PR/SD/PD) | 필수 |
| Resp_date2, Response2, ... | 추가 반응 평가 (최대 10개) | 선택 |
| ASCT_date | 자가조혈모세포이식 날짜 | 선택 |
| Tx_status / EOT_date / Dropout_date / LastDose_date | ongoing·EOT·dropout 및 날짜 | 선택 |
| LastFU_date | 마지막 추적일 = 막대 끝 | 선택 |
| Death_date | 사망일 | 선택 |
| AE_name1, AE_date1, AE_grade1, ... | 주요 이상반응 (막대 위 라벨) | 선택 |

## 로컬 개발

```bash
# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 빌드
npm run build
```

## 배포

### Vercel 배포 (추천)

1. 이 저장소를 GitHub에 push
2. [Vercel](https://vercel.com)에서 GitHub 연동
3. "Import Project" → 저장소 선택 → Deploy

### GitHub Pages 배포

1. `vite.config.js`에서 `base`를 저장소 이름으로 변경
2. `npm run build` 실행
3. `dist` 폴더를 GitHub Pages로 배포

## 라이선스

MIT License
