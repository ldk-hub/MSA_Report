# MSA_project
[![HitCount](http://hits.dwyl.com/ldk-hub/MSA_project.svg)](http://hits.dwyl.com/ldk-hub/MSA_project)
[![HitCount](https://img.shields.io/badge/lisence-MIT-green.svg)](https://github.com/ldk-hub/MSA_project/blob/master/LICENSE)

프로젝트 목적 MSA의 기능 구현 및 샘플케이스 구성

![22](https://user-images.githubusercontent.com/12209348/75217751-47116c80-57db-11ea-9b8d-69af722f8dbf.PNG)

선정 기준 
 대부분 기존의 모놀리틱 -> MSA 전환 케이스가 실무에서 많이 활용될 것으로 추정

서비스별 DB의 분리 부분별 관리 및 프로세스 분할 


## 변경 키워드
  - 톰캣에서 < - > hikariCP 전환
  - 유레카 
  - 리본 
  - 히스트릭스 
  - 줄
  - 서킷브레이커




## 계획
chapter 1. - 서비스별 분산구조 구성 테스트 
       유레카 서버에 로그인, 회원가입, 메인화면 구성
       유레카 클라이언트에서는 통계대시보드, 차트 통계,캘린더 페이지 구성
chapter 2. - 서비스 부하분산 테스트
         
chapter 3. - 서킷브레이커 테스트



## 개발 환경
 - java, jsp , springboot
 - hikariCP
 - Jquery, ajax, jpa
 - postgresqlDB, OracleDB
 
 
 
 ## 진행이슈
  - 노트북의 메모리와 CPU가 2개의 db구동과 여러개의 서비스 실행과정에서 OOM이 발생 해당 테스트 환경 대응방안 모색 
