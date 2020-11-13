# MSA_STUDY
[![HitCount](http://hits.dwyl.com/ldk-hub/SpringCloudConfigTEST.svg)](http://hits.dwyl.com/ldk-hub/SpringCloudConfigTEST)

## EUREKA, Ribbon API

Saas 구조 - 12 팩터 앱 자세한 내용 : https://12factor.net/ko/

## MSA - 마이크로서비스 아키텍처란? 
대용량 트래픽을 커버리지하기 위한 서버 중앙화 다중클라이언트 대상으로 실시간 배포를 할 수 있는 강점이 있음. 서비스 로스타임이 없다.(즉시반영)
대규모 서비스 경우 각 서비스별로 모듈화하여 개발할 수 있는 구조 만약 서비스 모듈에서 오류가 발생하게되면 해당서비스만 로스되며 다른서비스에는 영향이 가지 않는 구조 

## 기존 모노리틱 아키텍처와 마이크로 서비스 아키텍처의 차이점
![1](https://user-images.githubusercontent.com/12209348/71953552-f099a000-3225-11ea-98c8-0536deea6d72.PNG)

 - 모노리틱 : 하나의 서버에 모든 시스템 구성을 사용.
 - 마이크로서비스아키텍처 : 서비스는 중앙관리 서버에서 그외 서비스별로 vm 구성을 쪼개어 사용하여 관리하는 구조 
 
 * eureka   
     바야흐로 클라우드 시대, 서버는 실제 서버 컴퓨터에서 돌아가지않고 아마존과 같은 호스팅 업체가 관리하는 클라우드 서버에서 실행된다.   
     서버 IP는 유동적으로 변경되고 서버 관리자는 이에 대한 조치를 일일이 하기 힘듬으로 동적으로 이동하는 서버(eureka client)를 관리하는 서버(eureka server)를 구성하여 조치한다.   
     이렇게 실제 클라이언트의 요청을 처리하는 서버(eureka client)들 사이에서 Middle-tier(중간다리) 역할을 하는것이 eureka server이다.   
     eureka client 관리뿐 아니라 로드 밸런싱이나 장애 복구 기능까지 제공한다.   

     eureka_discovery   
   -  Service Registry: 서비스(eureka client)가 자기 자신의 정보를 Eureka Server에 등록하는 행동   
   -  Service Discovery: 클라이언트가 요청을 보내면 Service Registry 되어있는 서비스 들을 Eureka Server에서 발견하는 과정  
   -  Eureka 구성 요소 관련  
   -  Eureka Server: Eureka Client들을 관리(등록, 제어, 삭제, 제공) 하는 서버  
   -  Eureka Client: Service Registry 하여 서비스에 대한 비지니스 로직을 처리하는 클라이언트, 다른 Eureka Client 들과 연동하여 비지니스 로직을 처리한다.  
   -  Eureka Service: Eureka Server에 등록된 서비스를 가리킴, Eureka Client가 제공하는 서비스로 하나의 서비스의 원활한 수행을 위해 동시에 같은 서비스를 지원하는 여러개의 Eureka Client 가 동작할 수 있다.  
   -  Eureka Instance: Eureka에 등록되어 목록에서 조회 가능한 Eureka Service를 의미  

  * 리본 (부하분산 처리) 
   - 클라이언트 로드밸런서
   - 기본 라운드로빈(RR) 방식의 부하분산 처리가능 
   - 스프링클라우드로 부터 서버목록을 전달받아 사용가능
   - 클라이언트에서 서버에 접근하는 방식으로 3번이상 연결실패 시 다른 서버로 연결시도함.
  
  * 로드밸런서에서 로드밸런싱이 이뤄지지않고 
    - api-gateway에서 로드밸런스 됨. ribbon은 eureka 서비스 사용시 내부에서 같이 작동한다.
    - HTTP,TCP,UDP 모두지원 함
    - 대상의 지속적인 ping을 체크하여 서비스 UP/DOWN을 판단할 수 있음.
 
 * 기존 서버사이드 방식과 리본의 방식 
  ![1](https://user-images.githubusercontent.com/12209348/67823500-b6fe3780-fb06-11e9-98c6-ddaef4ff87fb.PNG)
 
 * 서킷 브레이커
  - 서킷 브레이커 경우 전류 차단기 처럼 
  - 서로의 접점이 문제가 발생 할 경우 해당 문제부분을 일시적으로 차단시켜주어 기존의 사용중인 서비스는 유지하고 문제되는부분만 격리시켜주는 기능

 * 넷플릭스OSS (키워드)
   - ZUUL: 클라이언트의 요청을 해당 경로로 전달하는 역할
   - HYSTRIX :서킷브레이커 라이브러리를 제공(시스템 장애생기면 연쇄작용으로 무너지지않게 차단기역할)
   - RIBBON : 로드밸런싱 기능
   - EUREKA : 유레카 서버에서 유레카 클라이언트 대상으로 중앙 관리를 할 수 있는 구조
 

## MSA 사용목적  
대규모 트래픽 몰리는 서비스 경우  
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
 
  * 예제개발 진행예정 항목리스트
   - 기존의 adminDashBoard프로젝트를 2분할하여 MSA로 구성계획 및 설계안 작성
   - 두개의 DBMS로 분할 postgresql, oracle DB 
   - 유입이 많을 것같은 서비스를 별도의 서비스로 분할하여 
   - 모노리틱으로 구성된 프로젝트를 MSA로 구성하는 방향으로 컨셉을 잡아 설계
   
### 프로젝트 History  
 기존의 진행했던 프로젝트 경우 대부분 메이븐 환경과 기존 레거시 환경을 따라가는 방향으로 개발하였으나 최근 다양한 방법으로 개발환경을 사용함으로 스펙트럼을 넓혀가고 있다.  
 그중  히카리CP와 그레이들 ORM기반 JPA hibernate MSA 역시 이와 같은 맥락이다.  
 그래서 이와 같은 내용을 정리하고 실습을 통해 직접 프로젝트를 구성해볼 것이다.   
   
## HikariCp란?

정의 : DataBase와의 커넥션풀 관리해줌. 이전 프로젝트에서 굉장히 유용하게 사용하였음. 무중단서비스
HikariCP는 미리정해놓은 만큼의 커넥션은 Pool에 담아놓고 요청이있을시 Thread가 커넥션을 요청하고 Hikari는 Pool내에 있는 커넥션을 연결해줌.


## 그레이들(Gradle)란?
현재로서는 분명히 maven의 점유율이 더 높고 더 익숙하신 분들이 많은 상황이지만
gradle 의 추격이 더 빨라지고 있어서 조만간 상황이 역전될 가능성이 더 높다고 하는 사람들이 많아지고 있으며
그래들이 조금더 빠른 성능과 간결한 설정의 매력을 보유하고 있어 인기도가 상승중이라고 합니다.
소규모의 프로젝트에서는 큰 차이가 없어서 익숙한 maven 을 사용해도 무방할지라도
규모가 커질수록 gradle 을 사용하는 것이 체감상 더욱 유리하다고 합니다.

빠른 성능과 간결한 설정을 들 수 있다. https://gradle.org/maven-vs-gradle/ 참고.
아무래도 maven 의 단점을 보완한 최신 툴이고, 계속해서 많은 버전 업그레이드를 진행하고 있어 그 격차가 계속 벌어지고 있는 듯 하다.
동일한 역할을 하는 툴이므로 maven 에 익숙한 분들은 굳이 약간의 성능을 느끼기 위해 gradle 로 갈아타려 하지 않을 수도 있다.
빌드만 잘되면 그 뿐이지만... gradle 의 엄청난 기능들과 확장성을 공부한다면 마음이 바뀔 수도 있을지 모른다.

#### 메이븐 vs 그레이들 (메이븐)
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>

   <groupId>com.example</groupId>
   <artifactId>demo-maven</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <packaging>jar</packaging>

   <name>demo-maven</name>
   <description>Demo project for Spring Boot</description>

   <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>1.5.4.RELEASE</version>
      <relativePath/> <!-- lookup parent from repository -->
   </parent>

   <properties>
      <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
      <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
      <java.version>1.8</java.version>
   </properties>

   <dependencies>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter</artifactId>
      </dependency>

      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-test</artifactId>
         <scope>test</scope>
      </dependency>
   </dependencies>

   <build>
      <plugins>
         <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
         </plugin>
      </plugins>
   </build>


</project>

```

##  메이븐 vs 그레이들 ()
```
buildscript {
    ext {
        springBootVersion = '1.5.4.RELEASE'
    }
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}

apply plugin: 'java'
apply plugin: 'idea'
apply plugin: 'org.springframework.boot'

version = '0.0.1-SNAPSHOT'
sourceCompatibility = 1.8

repositories {
    mavenCentral()
}


dependencies {
    compile('org.springframework.boot:spring-boot-starter')
    testCompile('org.springframework.boot:spring-boot-starter-test')
}
```

## 유레카 주요 정의
Eureka Instance : 유레카에 등록되어 목록에서 조회가능한 유레카 서비스를 의미함.
Eureka client : 서비스들의 위치정보를 알아내기 위해 유레카에 질의하는 서비스
Eureka server : 유레카 서비스 자신을 등록하는 서버이자 유레카클라이언트가 가용한 서비스목록을 요청하는서버
Eureka service : 유레카 클라이언트에 의해 발견의 대상이 되도록 유레카에 등록을 요청한 서비스를 가르킴


#### 메이븐 가이드 공식
https://docs.gradle.org/current/dsl/org.gradle.api.Project.html

## H2 란?


