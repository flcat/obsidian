
# 권재찬            Kwon Jaechan	
    Phone: +82 010-4621-7342 / Email: flcat.xd@gmail.com 
	Linkedin ID: flcat / github: https://github.com/flcat
---
```
안녕하세요? 권재찬입니다. 저는 협업하는데에 있어 
팀원간 의견조율 능력이나 커뮤니케이션 능력이 출중합니다. 
아마추어 게이머로 활동할 당시 팀원간의 의견을 조율 및 상황을 판단하는 역할을 했고
여기서 제 커뮤니케이션 능력을 십분 발휘하여 경기도 대표로 우승하는 경험을 하였습니다. 
```
##### 상장 
![상장|300\*400](https://github.com/user-attachments/assets/1349d58f-7e89-46d9-8cae-bf4066d2abe4)

---



# **Portfolio** 
---
### Project Name : **고기요**
	 web : https://gogiyo.com/charts
	 github : https://github.com/flcat/meat_wholesale_price
#### **What ?**
```
현재 수입 쇠고기에 대한 정보만 제공중 추후 한우, 돼지, 닭에 대한 소,도매 정보 제공 예정
```
#### **Why ?**
```
재직중인 회사에서 수입 쇠고기에 대한 시세를 일일히 손수 검색, 조사하고 있기에 인력 낭비
를 줄이기 위해,  또, 현재 육류 경매시장 가격은 api로 제공되고 있지만 수입 쇠고기에 
대한 도매 시장가는 없기에 해당 프로젝트를 진행.
```

- ## **Tech stacks**
---
- ##### #SpringBoot 3.3.1 
```
> 클래스 데이터 공유(CDS) 지원
	Spring Boot 3.3에 도입된 가장 중요한 기능 중 하나는 클래스 데이터 공유(CDS)
	사용량을 예측할 수 없고 가격적인 부담을 덜기 위해 AWS t2.micro 프리티어를 선택한
	만큼 조금이라도 메모리적으로 이득을 봐야겠다고 판단
```
- ##### #Java21 
```
프로젝트 시작은 Java 17로 하였으나 AWS가 프리티어인만큼 과부하를 조금이라도 덜기위해 변경.
> Virtual Thread 지원
	Spring Boot 3.2부터 Virtual Thread를 지원 한다. (경량 스레드 목적)
	마찬가지로 java.lang.Thread의 인스턴스로서 구현된다.
	그러나 Virtual Thread는 OS thread 수에 종속되지 않는다.
	OS thread에서 실행되지만, Virtual Thread에서 실행되는 코드가 I/O blocking을 일으키면, 
	Java runtime은 해당 Virtual thread가 다시 실행이 가능해질 때까지 중지시킨다.
	따라서 OS thread는 다른 Virtual Thread를 실행시킬 수 있다.
	(실제 OS thread 수보다 더 많은 thread를 실행)
```
- ##### #PostgreSQL
```
	> 
	1. 데이터 모델의 복잡성
	2. 데이터 무결성:  제약 조건과 외래 키 관계를 더 엄격하게 지원하여 데이터 무결성을 보장.
	3. 인덱싱: 부분 인덱스, 다중 컬럼 인덱스 등 고급 인덱싱 기능을 제공하여 쿼리 성능을 최적화.
	4. 쿼리 성능: 복잡한 쿼리와 대규모 데이터셋에 우수한 성능 제공.
	5. 동시성 처리: MVCC(Multi-Version Concurrency Control)를 통한 동시성 처리 강점 보유.
	6. 확장성: 데이터를 지속적으로 누적할 예정이기에 대용량 데이터 처리와 스케일 아웃에 적합
	7. 전문 검색: 초기버전에는 검색 기능이 있었다. 고로 전문검색기능이 필요했었음.
	8. 지리 정보 처리: 현재 제작중인 지역별 가격 정보 기능에 강점 보유.
	9. 시계열 데이터 처리: 시계열 데이터 처리를 위한 특화된 기능과 확장을 제공.
	10. 트랜잭션 관리: 복잡한 트랜잭션을 안정적으로 처리하는 데 강점 보유.
```
- ##### #Python3
```
	BeautifulSoup, Scrapy, Selenium 등 웹크롤러를 만드는데 유리한 라이브러리를
	보유하여 빠른 시간안에 웹크롤러를 제작할 수 있다고 판단.
```

- # **TroubleShooting**

---
**2024-07-09**
```
> 데이터를 올바르게 긁어오지 못하는 현상
	정규표현식 개선 및 예외처리로 해결.
```

**2024-07-10**
```
> 긁어오는 데이터 양에 비해 시간소요가 많아 병렬처리하기로 결정
	개선 후
	
		meat_market_price_scrap.py =
		Completed processing 목심
		Crawling process completed. Saving data to Excel...
		Data saved successfully. Process complete.
		0:00:11.446556
		
		geumcheon_meat_scrap.py =
		Completed crawling 뉴질랜드 - 목심. Total items: 158
		Crawling process completed. Total items collected: 863
		Data saved successfully. Process complete.
		0:00:11.715069
	> 	특히, 금천미트 크롤러 기존엔 1분넘게 걸렸었는데 11초대로 들어온 모습이다.
			병렬처리를 도입한 이유는 당연하게도 속도 향상에 있었다.
			물론 직렬처리는 코드가 더 간결하고 서버 부하가 적지만
			데이터 양이 많을 경우 전체 시간이 크게 증가할 가능성이 있고
			하나의 요청이 지연되면 전체 프로세스가 지연되는 단점이 있다. 
```

**2024-07-15**
```
> 크롤러가 긁어오는 데이터 숫자가 실제데이터에 비해 적은 현상 :
	pagenation 기능이 반응형으로 이루어져있어 스크롤이 필요했고 window.scrollBy(0, distance) 를 비동기적으로 실행하여 해결.
	코드 수정후 데이터를 잘 긁어온다
	Crawling process completed. Total items collected: 26	
						▿
	Crawling process completed. Total items collected: 863
```

**2024-07-30**
```
> 그래프 가독성 개선
	그래프 색상을 원색에서 파스텔톤으로 변경하여 눈에 부담을 줄임
	유동성이 없는 데이터를 필터링하여 단순화함
```

**2024-08-07**
```
> UI 개선
	크롤링에 실패하는 데이터들을 발견 크롤링 재시도 기능 추가
	기존에는 등급별 그래프를 모두 그렸으나 웹페이지 개선으로 그래프를 하나로 줄이고
	등급 버튼을 생성
```

**2024-08-29**
```
> 설정 초기화 이슈
	apt update apt grade 진행시 도커 이미지가 날아가는 현상 발생
	docker-compose 작성으로 해결
```

# Education
---
- #### **방송통신대학교**
	 컴퓨터과학과 2022.03 - 휴학
		부트캠프 경험만으로는 이론에 대한 부족함을 느껴 편입하게 되었습니다.

- #### **NCS 교육훈련** 
	IoT 기반의 웨어러블 응용 SW엔지니어링 에이콘아카데미 2015.09 ~ 2016.01 