# 기업연계 project

## 프로젝트 설명
- AWS 클라우드 환경을 활용해 ETL(추출, 변환, 로드) 전 과정을 구축하는 프로젝트
- ETL 과정과 H&M data를 활용한 고객 맞춤 - 상품 추천 서비스 구현을 목표로 함.

## 프로젝트 기간
2023.11.09 - 2023.12.15 (5주/4인)

## 아키텍처
![image](https://github.com/yeardream-de-project-team11/project-team11/assets/104144701/599d8a4a-4499-4121-a609-efc6966a3728)


## 역할 
- 팀장으로서 기업 담당자와의 커뮤니케이션 담당
- EMR 파티셔닝/압축 단계 customer script 작성 [[link]](https://github.com/kclown0/aws-emr-project/blob/main/scripts/emr_parition_customers.py)
- Airflow Athean table dag 작성 [[link]](https://github.com/kclown0/aws-emr-project/blob/main/airflow/dag/athena_create_table.py)
- Superset과 Athena 연동 하는 부분을 담당

## Dataset
H&M data - 약 2년 간의 article(상품), customer(고객), transaction(거래), img(이미지) data로 구분 됨.
- image - 각 article_id에 해당하는 이미지 data (31gb)
- article.csv - 구매 가능한 각 article_id에 대한 상세 메타데이터(0.04gb)
- customer.csv - 데이터 세트의 각 customer_id에 대한 메타데이터(0.2gb)
- transaction.csv - 각 날짜에 대한 각 고객의 구매 내역과 추가 정보로 구성된 데이터(3.49gb)


### 기술 스택
<div style="text-align: left;">
   <img src="https://img.shields.io/badge/EC2-007396?style=for-the-badge&logo=S3&logoColor=white">
  <img src="https://img.shields.io/badge/S3-007396?style=for-the-badge&logo=S3&logoColor=white"> 
  <img src="https://img.shields.io/badge/EMR-3776AB?style=for-the-badge&logo=EMR&logoColor=white">
  <img src="https://img.shields.io/badge/Athena-007395?style=for-the-badge&logo=Athena&logoColor=white">
  <br> <img src="https://img.shields.io/badge/docker-007396?style=for-the-badge&logo=S3&logoColor=white">
   <img src="https://img.shields.io/badge/Airflow-007396?style=for-the-badge&logo=S3&logoColor=white">
  <br> <img src="https://img.shields.io/badge/Superset-007396?style=for-the-badge&logo=S3&logoColor=white">
  <img src="https://img.shields.io/badge/Prometheus-007396?style=for-the-badge&logo=S3&logoColor=white">
  <img src="https://img.shields.io/badge/Grafana-007396?style=for-the-badge&logo=S3&logoColor=white">
  </div>

## 프로젝트 상세 설명
1. kaggle H&M data 사용, AWS를 활용한 ETL 과정을 구축
2. 각 data 별로 파티셔닝과 압축을 진행해 S3에 적재.
  <br> 2-1. article의 경우 csv 파일 형태의 data를 product_group_name 별로 나눈 후 parquet 형식으로 저장.
  <br> 2-2. customer의 경우 csv 파일 형태의 data를 age 별로 나눈 후 parquet 형식으로 저장.
  <br> 2-3. transaction의 경우 csv 파일 형태의 data를 year, month 별로 나눈 후 parquet 형식으로 저장.
3. 파티셔닝과 압축 된 data를 Athena를 사용해 table 생성.
4. Superset(data 시각화툴)과 Athena를 연동하여 data 시각화 진행.
5. ETL 과정을 Airflow를 사용하여 자동화 및 slack 알람 시스템 구축.
6. Prometheus, Grafana를 사용하여 모니터링 구축.

## 프로젝트 회고
- ETL 전반의 과정을 AWS를 통해 구축해볼 수 있었습니다.
- EC2에 Airflow를 설치하여 진행했을 때 리소스 포화 상태가 발생하였습니다. 인스턴스 업그레드를 통해 문제를 해결하였는데 <br>다음에는 다른 워크플로우를 사용해 진행해보고 싶습니다. 

