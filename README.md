# MSA_project  
[![HitCount](http://hits.dwyl.com/ldk-hub/MSA_project.svg)](http://hits.dwyl.com/ldk-hub/MSA_project)
[![HitCount](https://img.shields.io/badge/lisence-MIT-green.svg)](https://github.com/ldk-hub/MSA_project/blob/master/LICENSE)

프로젝트 목적 MSA의 기능 구현 및 샘플케이스 구성  
![22](https://user-images.githubusercontent.com/12209348/75217751-47116c80-57db-11ea-9b8d-69af722f8dbf.PNG)

MSA 사용목적 대규모 트래픽 몰리는 서비스 경우  
하나의 시스템에서 트래픽이몰리거나 유입이 많은 서비스를 분산시켜 장애 대응 및 세부 관리를 할수있음.  
 - 기존의 모놀리틱 -> MSA 전환   

## 변경 키워드  
  - 톰캣에서 < - > hikariCP   
  - 유레카  
  - 리본 
  - 히스트릭스  
  - 줄  
  - 서킷브레이커  

## 계획  
- chapter - 서비스별 분산구조 구성 테스트   
       * 유레카 서버에 로그인, 회원가입, 메인화면 구성  
       * 유레카 클라이언트에서는 통계대시보드, 차트 통계,캘린더 페이지 구성  
chapter 2. - 서비스 부하분산 테스트  
         
chapter 3. - 서킷브레이커 테스트  

## 개발 환경  
 - java, jsp , springboot  
 - hikariCP  
 - Jquery, ajax, jpa, Mybatis  
 - postgresqlDB, OracleDB ->H2(DB중 가벼움)  
 
 ## 진행이슈  
  - 노트북의 메모리와 CPU가 2개의 db구동과 여러개의 서비스 실행과정에서 OOM이 발생 해당 테스트 환경 대응방안 모색   
  - 메모리 점유율 이슈 (간헐적으로 블루스크린발생)sts 최적화 작업, oracle xe, postgresqldb, 노트북 프로세스 모두 종료 후 세팅 등    
  - 노트북 메모리 이슈는 기존 오라클, 포스트그레스큐엘을 >H2, 포스트그레스큐엘을 사용하여 테스트예정  
  - 포스트그레스큐엘은 jpa로만 구성, H2는 마이바티스로 구성  
  - 기존 대시보드 프로젝트를 MSA시스템 구성으로 채택  
  
