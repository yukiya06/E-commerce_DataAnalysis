# 'Instacart' 재주문을 늘리기 위한 마케팅 인사이트 도출

* 데이터 분석 및 발표 : 안나 (Email: naan74532@gmail.com)
* [Presentation PDF](링크예정): 전체 발표 자료는 PDF 로 편히 보실 수 있습니다.  
* [Instacart EDA](https://github.com/yukiya06/E-commerce_DataAnalysis/blob/main/Instacart_EDA.ipynb): EDA 분석자료
* [Recommendation System](https://github.com/yukiya06/E-commerce_DataAnalysis/blob/main/Instacart_recommendation.ipynb): 추천시스템 자료
* [Dashboard](https://datastudio.google.com/reporting/cc65e16c-d117-4770-8211-6046d79d1af4): 데이터 스튜디오 대시보드

## 프로젝트 목차
#### 1. 주제 선정 이유 및 자료 구성  
#### 2. 탐색적 자료 분석 (EDA)  
2.1 사업 현황 파악
* 주문 고객 분석 (누적 주문 횟수)  
* 주문 상품 분석 (상품 수, 매출 순위, 쇼핑 순서)

2.2 가설 검증: 재주문에 패턴이 존재한다. 
* 주문 간격   
* 주문 횟수 (주문 횟수가 많으면 재주문 시점이 빠른가, 주문 상품수가 많은가)  
* 주문 수량 (많은 수량을 주문하면 재주문 상품이 많은가)  
* 주문 상품 구성 (재주문 비율이 높은 상품)  
* 주문 요일 및 시간 (주문 트렌드, 많이 구매하는 시간)    
#### 3. 대시보드 구성  
#### 4. 마케팅 인사이트  
#### 5. 연관상품분석 및 상품 추천시스템  
#### 6. 한계점 및 추후 발전방향  

---
## 1. 주제 선정 이유 및 자료 구성
### 1.1 주제 선정 이유
* 인스타카트는 온라인 식료품 구매 서비스를 제공하는, **성장** 동력을 얻기 시작한 인기 앱입니다. **신규 고객 유치**에 한창이지만, **재주문**을 하는 고객들도 중요하다는 조언을 받았습니다. 
* 신규 고객을 확보하는 데는 기존 고객을 유지하는 것보다 훨씬 많은 비용이 소요됩니다. 많은 연구에 따르면 **재주문 고객이 기업 매출의 40% 이상 창출**<sup>[1]</sup> 할 수 있고, **고객 유지율을 5%증가시킬 때 수익이 25~95% 증가**<sup>[2]</sup> 할 수 있습니다. 따라서 **반복적인 재주문을 장려**하고 **고객을 유지**하는 방법에 대한 분석이 필요합니다.
(참고자료 1. [Adobe Digital Index](https://www.adobe.com/ca/experience-cloud/digital-insights/digital-economy-index.html), 2. [Harvard Business Review](https://hbr.org/2014/10/the-value-of-keeping-the-right-customers))

### 1.2. 분석의 목적
* **목적**: **재주문을 장려하기 위한 마케팅 인사이트 도출**  
* **문제 정의(가설 설정)**: **재주문에는 패턴이 있다.**  
    - 주문 시점, 주문 횟수, 주문하는 상품 수, 주문 상품 구성에 특징이 있다.
    - 해당 패턴을 파악하고, 재주문을 장려하기 위한 마케팅 인사이트를 도출한다.

- **재주문**이란? : **기존 고객의 재구매**를 의미합니다. 이 고객들은 해당 기업을 잘 알고 있으며, 편하기 때문에 같은 곳에서 반복적으로 구매를 하는 편입니다.  신규 고객처럼 다양한 상품을 탐색하고, 비교하지 않고, 원하는 것을 이미 알고 있으니 그 상품을 바로 구매합니다.

### 1.3. 자료구성 
* 선정 데이터: [Instacart Orders 오픈소스 데이터](https://tech.instacart.com/3-million-instacart-orders-open-sourced-d40d29ead6f2)
* 데이터셋 설명: https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b

<img width="750" alt="ERD(White)" src="https://user-images.githubusercontent.com/91524805/166182491-7e1898c4-8e26-4fb1-8a52-dcace5faaece.png">

* Instacart Orders 오픈소스 데이터 (총 20만 명 고객의 340만 건에 대한 주문 정보)
* 크게 주문정보, 상품정보로 구분되며, 하나의 주문시 포함된 상품 목록들이 연결된 데이터 구조 입니다.
* 상품 주문 파일이 prior, train으로 나뉘어 제공되었는데, 이를 합쳐서 분석에 사용하였습니다.

### 1.4 사용 기술 및 구현 내용
* 필요한 데이터를 정의 및 수집하여 이를 분석하는 전체 프로세스를 따라 진행 하였습니다.
* 사용한 기술 및 구현 내용은 아래와 같습니다.

<img width="600" alt="사용기술 및 구현내용" src="https://user-images.githubusercontent.com/91524805/167284050-543e8cdc-f090-4c2c-8540-8c966c4b8657.png">

## 2. 탐색적 자료 분석 (EDA)
