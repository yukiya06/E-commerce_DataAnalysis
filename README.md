# 'Instacart' 판매 데이터 분석
## 재주문을 장려하기 위한 마케팅 인사이트 도출

* 데이터 분석 및 발표 : 안나 (Email: naan74532@gmail.com)
* 대시보드 [Datastudio](https://datastudio.google.com/reporting/cc65e16c-d117-4770-8211-6046d79d1af4) 
* [발표자료 PDF](https://github.com/yukiya06/E-commerce_DataAnalysis/blob/main/DA_%EC%95%88%EB%82%98_%EC%9D%B4%EC%BB%A4%EB%A8%B8%EC%8A%A4_%EB%A7%A4%EC%B6%9C%EB%B6%84%EC%84%9D.pdf)

## 프로젝트 전체 목차
#### 1. 주제 선정 이유 및 자료 구성  
#### 2. 탐색적 자료 분석 (EDA): [Github](https://github.com/yukiya06/E-commerce_DataAnalysis/blob/main/Instacart_EDA.ipynb)  
    2.1 사업 현황 파악
        1. 주문 고객 분석 (누적 주문 횟수)  
        2. 주문 상품 분석 (상품 수, 매출 순위, 쇼핑 순서)

    2.2 가설 검증: 재주문에 패턴이 존재한다. 
        1. 주문 간격   
        2. 주문 횟수 (주문 횟수가 많으면 재주문 시점이 빠른가, 주문 상품수가 많은가)  
        3. 주문 수량 (많은 수량을 주문하면 재주문 상품이 많은가)  
        4. 주문 상품 구성 (재주문 비율이 높은 상품)  
        5. 주문 요일 및 시간 (주문 트렌드, 많이 구매하는 시간)    
#### 3. 대시보드 구성: [Datastudio](https://datastudio.google.com/reporting/cc65e16c-d117-4770-8211-6046d79d1af4)  
#### 4. 마케팅 인사이트  
#### 5. 연관상품분석 및 상품 추천시스템: [Github](https://github.com/yukiya06/E-commerce_DataAnalysis/blob/main/Instacart_recommendation.ipynb)  
#### 6. 한계점 및 추후 발전방향  

---
## 프로젝트 요약
## 1. 주제 선정 이유 및 자료 구성
### 1.1 주제 선정 이유
* 인스타카트는 온라인 식료품 구매 서비스를 제공하는, **성장** 동력을 얻기 시작한 인기 앱입니다. **신규 고객 유치**에 한창이지만, **재주문**을 하는 고객들도 중요하다는 조언을 받았습니다. 
* 신규 고객을 확보하는 데는 기존 고객을 유지하는 것보다 훨씬 많은 비용이 소요됩니다. 많은 연구에 따르면 **재주문 고객이 기업 매출의 40% 이상 창출**<sup>[1]</sup> 할 수 있고, **고객 유지율을 5%증가시킬 때 수익이 25~95% 증가**<sup>[2]</sup> 할 수 있습니다. 따라서 **반복적인 재주문을 장려**하고 **고객을 유지**하는 방법에 대한 분석이 필요합니다.
(참고자료 1. [Adobe Digital Index](https://www.adobe.com/ca/experience-cloud/digital-insights/digital-economy-index.html), 2. [Harvard Business Review](https://hbr.org/2014/10/the-value-of-keeping-the-right-customers))

### 1.2 분석의 목적
* **목적**: **재주문을 장려하기 위한 마케팅 인사이트 도출**  
* **문제 정의(가설 설정)**: **재주문에는 패턴이 있다.**  
    - 주문 시점, 주문 횟수, 주문하는 상품 수, 주문 상품 구성에 특징이 있다.
    - 해당 패턴을 파악하고, 재주문을 장려하기 위한 마케팅 인사이트를 도출한다.

- **재주문**이란? : **기존 고객의 재구매**를 의미합니다. 이 고객들은 해당 기업을 잘 알고 있으며, 편하기 때문에 같은 곳에서 반복적으로 구매를 하는 편입니다.  신규 고객처럼 다양한 상품을 탐색하고, 비교하지 않고, 원하는 것을 이미 알고 있으니 그 상품을 바로 구매합니다.

### 1.3 자료구성 
* 선정 데이터: [Instacart Orders 오픈소스 데이터](https://tech.instacart.com/3-million-instacart-orders-open-sourced-d40d29ead6f2)
* 데이터셋 설명: https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b

<img width="800" alt="ERD(White)" src="https://user-images.githubusercontent.com/91524805/166182491-7e1898c4-8e26-4fb1-8a52-dcace5faaece.png">

* Instacart Orders 오픈소스 데이터 (**총 20만 명 고객의 340만 건에 대한 주문 정보**)
* 크게 **주문정보, 상품정보**로 구분되며, 하나의 주문시 포함된 상품 목록들이 연결된 데이터 구조 입니다.
* 상품 주문 파일이 prior, train으로 나뉘어 제공되었는데, 이를 합쳐서 분석에 사용하였습니다.

### 1.4 사용 기술 및 구현 내용
* 필요한 데이터를 정의 및 수집하여 이를 분석하는 전체 프로세스를 따라 진행 하였습니다.
* 사용한 기술 및 구현 내용은 아래와 같습니다.

<img width="600" alt="사용기술 및 구현내용" src="https://user-images.githubusercontent.com/91524805/167284050-543e8cdc-f090-4c2c-8540-8c966c4b8657.png">

---

## 2. EDA 및 가설검증에서 얻은 마케팅 인사이트
### ▶ 가설 검증 결과: 재주문에 패턴이 존재한다. → Yes!
#### → 어떤 패턴이 있는지? 주문 간격 / 주문 횟수 / 주문 수량 / 주문 상품 구성 / 주문 요일 및 시간
* 분석 결과를 토대로 고객 특성에 맞게 **재주문을 독려**하는 방안을 마련합니다.
* 고객의 **타겟팅을 강화**하여 **마케팅 활동**을 결정 할 수 있습니다.
* 이후 고객별 구매한 상품목록을 추가로 분석하여 **상품추천**을 향상 시키고자 합니다.

### 2.1 주문 간격: **7일** (~10일 이내)  
* 고객 타겟 판촉일정을 맞춥니다. **메일링,문자로 판촉**내용을 알리는 주기를 **7일**, 30일로 합니다.

<img width="750" alt="재주문 소요일자" src="https://user-images.githubusercontent.com/91524805/167291088-d1539b06-c702-47a8-83e2-cbca373e0e6d.png">
        
### 2.2 주문 횟수: 
* **주문 횟수**가 많으면 당연히 재주문 시점이 빠릅니다. 다만, **구매 수량은 비슷**합니다.
* 주문 **빈도**에 따른 고객 관리가 필요합니다.
* 평균적으로 4회 주문이 가장 많고, 5회부터 감소 추세  
    → **4회 이상**과 **이하** 이용 고객을 분리하여 관리합니다. 초기에 지속적인 구매를 독려하는 것이 중요합니다.  
    → 이용 횟수 **10회 단위**로 고객을 구분하여, 구매 적립포인트를 다르게 하는 등 차별화된 이점을 줍니다.  
    → **상위 10% (40회 이상 구매고객)** 을 밀착 관리하고, 이용 후기나 요청 사항에 빠르게 피드백합니다.  
 
<img width="750" alt="재주문소요일자_구매수량차이" src="https://user-images.githubusercontent.com/91524805/167291364-c9234405-62f8-4810-879d-01ff04c3ac65.png">

<img width="750" alt="누적주문 횟수" src="https://user-images.githubusercontent.com/91524805/167291342-6de2e4b3-7905-4918-9d95-4b8217c49da9.png">
  
### 2.3 주문 수량: 
* **많은 수량**을 구매하는 경우 **재주문 상품 비중이 높습니다.**
* 주문 수량에 따라 다른방식으로 추천합니다.  
    → **평균(4~7개)** 보다 적을 때, 장바구니 상품과 연관성 있는 상품을 추천하고 **세트 구매**를 독려합니다.   
    → **많은 수량**을 구매하는 사람에게는 구매했던 상품을 중심으로 추천합니다.    
    → 주문이 많은 인기상품과 재주문 비중이 높은 상품을 중점적으로 추천합니다.  
    
<img width="750" alt="수량많은주문_재주문비율" src="https://user-images.githubusercontent.com/91524805/167291498-32212f86-6202-4b2f-99d8-e06b69c74c2e.png">

<img width="750" alt="주문상품갯수" src="https://user-images.githubusercontent.com/91524805/167291407-66a0571e-03eb-4974-8f6d-8edaa8cc6b92.png">

### 2.4 주문 상품 구성: 
* **유통기간** 짧은 상품의 재주문이 많습니다. (신선 농산물 위주)
* **유통기간**에 따라 한번에 구매하는 양이 다르므로, 별도의 판촉을 적용합니다.  
    → 보관이 편한 상품은 수량을 증가시켜 상품을 구성합니다.  
    → 조금씩 자주 구매 해야 하는 상품은, 기존 구매 상품을 먼저 추천합니다.  

<img width="750" alt="재주문 상품" src="https://user-images.githubusercontent.com/91524805/167291517-8e1d8150-7668-4ba7-bb74-d87a5a1ce078.png">

### 2.5 주문 요일 및 시간: 
* **월,화, 9~17시** 주문이 많습니다. 그리고 구매 **시간**에 따른 구매패턴이 다릅니다.
* 상황에 맞는 판촉을 계획합니다.  
   → 이전 주문한지 오래된 고객에게 판촉하는 경우 사람들이 구매가 많은 **월화, 9~17시** 사이에 합니다.  
   → **밤**에는 구매하는 **수량이 많은편**으로, 총 금액에 따른 할인을 운영하여 수량을 증가시키는 판촉을 합니다.  
   → **새벽**구매는 **냉동식품, 통조림구매**가 많습니다. 시간에 따른 구매패턴에 맞춰 상품을 추천합니다.  

<img width="800" alt="시간_요일_주문트렌드" src="https://user-images.githubusercontent.com/91524805/167291554-5189d196-075c-42dd-9e98-4f8cc2fcf15f.png">

<img width="800" alt="구매하는 상품수가 많은 때는" src="https://user-images.githubusercontent.com/91524805/167291572-8ab40546-aa60-414b-9ada-1b2416e822c2.png">

---
## 3. 연관상품분석 및 상품 추천시스템
* 고객들의 상품 구매 데이터를 이용하여 품목간의 연관성을 분석하고자 합니다.
* 구매한 상품간 연관성이 있는 제품군을 묶어서 살펴보고, 상품 추천에 활용하려고 합니다.

### 3.1 Word2Vec이용한 Product2Vec
* Word2Vec은 구글에서 발표한 자연어 처리 기술로, 대량의 학습 데이터셋을 빠르게 학습할 수 있습니다. 이런 특징은 대량의 컨텐츠 이용 데이터가 발생하는 추천 시스템에서 활용하기에 아주 적합한 방식입니다.
* 추천 시스템에서 주로 Word2Vec은 상품을 벡터화 시킬 때 사용합니다. 이렇게 벡터화 시킨 결과는 유사한 상품 추천, 마이크로 카테고라이징, 의미 벡터로써 활용할 수 있습니다.
* 아프리카 TV(live2vec), Sportify(song2vec), Criteo(meta-pro2vec)등 실제 활용 사례가 많으므로 활용가치가 높습니다.
* 이번 프로젝트에서는 User_id당 구매한 Product 수가 여러가지 인데, 이를 벡터화 시켜 분석합니다.
* 파이썬의 gensim 패키지에 구현된 Word2Vec(클래스) 활용하여 구현하였습니다.  
    * word = product_id  
    * sentence = [product_id1, product_id2, ...]

### 3.2 상품 id에 따라 유사도 측정
* 학습된 Word2Vec을 통해 상품 id를 넣으면 유사한 제품을 추천받을 수 있게 구성했습니다.
* 대표적인 상품 id 3가지(샘플링) 결과를 보면, 입력한 단어와 유사하게 추출함을 알 수 있습니다.

<img width="750" alt="상품id로 추천" src="https://user-images.githubusercontent.com/91524805/167292600-3c2d6d3f-711a-4ea0-a3c1-9685fd5aff02.png">

### 3.3 KMeans clustering
* KMeans clustering은 주어진 데이터를 k개의 클러스터로 묶는 알고리즘입니다.
* Word2Vec 학습된 상품들을 그룹화(293개)하여 추천시스템에 활용하고자 합니다.  
   * 상품수(약 4.9만개)가 매우 많으므로 우선 추가 분석이 가능한 300개 수준으로 구분
    
<img width="800" alt="클러스터링_이미지추출" src="https://user-images.githubusercontent.com/91524805/167292721-46511909-2720-472e-b243-c23bf26e1946.png">

* 같은 클러스터내 상품들(샘플링)의 시간별 구매 패턴이 비슷한지 추가로 검증해보았습니다.  
* 오전, 오후에 따라 그래프 색상이 다릅니다. (오전: 붉은색, 오후: 검은색)  
* 같은 클러스터내에 상품들의 구매가 가장 많은 시간대가 유사하게 잘 묶였습니다.  

<img width="800" alt="클러스터링 검증" src="https://user-images.githubusercontent.com/91524805/167292770-9c451d47-3a2b-4dbc-9a66-883d3e7b69e7.png">

---
## 4. 한계점 및 추후 발전방향
* 제한된 수로 클러스터를 나누었는데 더 세분화 하여 상품이 구분되면 정교한 추천시스템을 구현할 수 있을 것 같습니다.
* 상품 추천 시스템을 구성하는 방식은 여러가지가 있는데, Product2Vec외에 다른 방식으로 진행했을 때 장단점도 더 파악하여 혼합하여 사용하거나, 구매성공률을 높이고 싶습니다.
* 이번 분석데이터에는 상품당 가격 자료나 동일 제품당 구매 수량정보 등이 없습니다. 수량만큼 가격정보가 중요한데, 이후에는 가격 정보가 있는 데이터로 매출 분석도 진행하고 싶습니다.

---
## 5. 참고자료
* [캐글-데이터 분석 및 시각화](https://www.kaggle.com/code/philippsp/exploratory-analysis-instacart)
* [요일 및 시간 분석, 연관상품분석](https://brunch.co.kr/@goodvc78/17)
* [트리맵 시각화](https://data-newbie.tistory.com/731)
* [클러스터링](https://medium.com/codex/creating-a-multifaceted-grocery-recommender-system-c394208f5e0b)
* [데이터스튜디오 대시보드구성](https://medium.com/honeybees-engineering/%EB%9D%B5%EB%8F%99-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%8C%80%EC%8B%9C%EB%B3%B4%EB%93%9C-%EB%A7%8C%EB%93%A4%EA%B8%B0-with-google-data-studio-4c76596000a4)
