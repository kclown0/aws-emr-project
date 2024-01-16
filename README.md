# 기업연계 project

## 프로젝트 설명
- AWS 클라우드 환경을 활용해 ETL(추출, 변환, 로드) 전 과정을 구축하는 프로젝트
- ETL 과정과 H&M data를 활용한 고객 맞춤 - 상품 추천 서비스 구현을 목표로 함.

## 프로젝트 기간
2023.11.09 - 2023.12.15 (5주/4인)

## 아키텍처
![image](https://github.com/yeardream-de-project-team11/project-team11/assets/104144701/599d8a4a-4499-4121-a609-efc6966a3728)

[역할] 
- 팀장으로서 기업 담당자와의 커뮤니케이션 담당
- EMR 파티셔닝/압축 단계 customer script 작성
- airflow athean table dag 작성
- superset과 athena 연동 하는 부분을 담당

## Dataset
H&M data - article(상품), customer(고객), transaction(거래), img(이미지) data로 구분 됨.



## 프로젝트 상세 설명
1. kaggle H&M data 사용, AWS를 활용한 ETL 과정을 구축
2. 각 data 별로 파티셔닝과 압축을 진행해 S3에 적재.
   2-1. article의 경우 csv 파일 형태의 data를 product_group_name 별로 나눈 후 parquet 형식으로 저장.
   2-2. customer의 경우 csv 파일 형태의 data를 age 별로 나눈 후 parquet 형식으로 저장.
   2-3. transaction의 경우 csv 파일 형태의 data를 year, month 별로 나눈 후 parquet 형식으로 저장.
4. 파티셔닝과 압축 된 data를 Athena를 사용해 table 생성
5. superset과 athena를 연동하여 data 시각화 진행
6. ETL 과정을 Airflow를 사용하여 자동화 진행

### 기술 스택
<div style="text-align: left;">
  <img src="https://img.shields.io/badge/S3-007396?style=for-the-badge&logo=S3&logoColor=white"> 
  <img src="https://img.shields.io/badge/EMR-3776AB?style=for-the-badge&logo=EMR&logoColor=white">
  <img src="https://img.shields.io/badge/Athena-007395?style=for-the-badge&logo=Athena&logoColor=white"> 
  </div>
