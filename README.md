# 2018-Yonsei Bigdata Analysis Competition
## 연세대학교 상경대학 빅데이터 분석대회 - Aronamin-ing 팀

**1. 데이터 정보**
>
>동문기업 중 일동제약 측에서 국내 대표 비타민제 브랜드명을 포함한 SNS 게시글을 크롤링한 자료를 제공받았습니다.
>
>크롤링된 자료는 페이스북(Facebook), 인스타그램(Instagram), 네이버 블로그(Naver blog), 네이버 카페(Naver Cafe), 다음 블로그(Daum blog), 다음 카페(Daum cafe), 유투브(Youtube) 였습니다.

	- 아로나민골드 3,238건, 아로나민씨플러스 1,118건, 우루사 12,330건, 임팩타민 3,099건, 센트룸 11,359건
	- 비타민제 29,736건, 영양제 56,959건
	
데이터예시

| SNS | Title | Contents | Address | Date |
| ------------ | ------------- | ------------- | ------------- | ------------- |
|naver_blog | 찬찬약사.. | 아로나민 골드, 아로나민 씨플러스 많이 들어보셨죠?? ... | https://blog.naver.com/... | 2017#### |



**2. 전처리 작업**
>
>Youtube의 경우 주소와 영상 제목 자료만 포함되어 있어, 분석 대상에 포함되기에 충분하지 않다고 판단하여 모든 자료에서 제거하였습니다. - __확인부탁__
>
>분석의 최종 목표를 SNS 고객층의 효과적인 분석으로 두었기에, 소비자의 주관적인 의견이 반영되었는지를 전처리 기준 중 가장 우선시 하였습니다.
>각 SNS 자료별로 필터링할 단계를 여러 개로 나누어 차등을 두었습니다.

	1) 자체 홍보
	   기업이 자사의 제품을 자발적으로 홍보하는 페이스북, 공식 블로그 게시글
	   
	2) 노골적 광고
	   소비자 또는 중간유통자의 광고글
	   자료 중 모호한 자료의 경우 직접 링크 접속 후 원문 참고 후 제거
	   ex) '핫딜', '쿠팡', '공구', '공구판매' 등
	   
	3) 도배, 중복글
	   인스타그램 Repost 및 트위터 Retweet


2-1. **제품별 전처리 작업 후 특징**
>>전처리 작업중 제품별로 다수 등장했던 특징이나 키워드를 중심으로 정리한 파일은 다음 링크에 제공되어 있습니다.
[link keyword][id]
[id]:https://docs.google.com/document/d/1j9fo8MiQO1yc5b-gLkDuwctuijfbbv4xHG0MZNV4y2g/edit?usp=sharing



**3. 분석방법**
>	1) 감성분석
>	2) 연관분석
>	2-1) Apriori Association Rules
>
>	     nims jupyter을 사용하여 전처리된 엑셀 파일을 코모란 분석기를 이용하여 Tokenize한 후 명사만 추출하여 support minimum threshold를 0.05로 잡았습니다. lift값의 minimum threshold는 0.08로 처리 후, 1:1 연관분석 결과를 내림차순으로 정렬하였습니다.
>
>	3) 빈도분석


**4. 주제별 분석**
> 4-1. 경쟁 제품 대비 아로나민 브랜드 이미지와 소비자의 인식 파악
>
>	감성분석 가격점수와 이미지점수를 산출하여 각 브랜드끼리 유사한 경우 Grouping하여 각 그룹간의 차이점 분석
>
> 4-2. 아로나민 광고에 대한 소비자의 반응 파악 (과거 광고의 제고)
>
>	아로나민 제품별로 '광고'와 관련된 감성분석과, 키워드를 중심으로 어떤 연관어들이 있는지를 분석하고, word2vec을 통해 유사도 분석
>
> 4-3. SNS 고객세분화 전략
>
>	- 가장 상위 계층(Human1)은 남성과 여성
>	- 그 다음 하위 계층은 2030, 4050으로 세대별로 구분
>	- 2030(Human2) 키워드 ‘남친 여친 남자친구 여자친구 연인’
>	- 4050은 두 집단으로 분류하였는데, ‘남편 아내 신랑 마누라 와이프’(Human3)
>	- ‘노인 어머니 어머님 아버지 아버님’(Human7)
>	- 마지막으로 특정 계층별 소비자를 구분했습니다.
>	- 우리나라만이 가지고 있는 특정 계층으로 수험생(Human6)을 추가, 키워드 기준은 ‘청소년 수험생 고3 입시’
>	- Human4는 ‘임산부 수유부’
>	- Human5는 유아 (키워드; 유아 아기 어린이 아이들)
>	- Human8은 ‘직장인’을 키워드로 분류
>
> 	분석 결과 각 계층별로 연관성이 높은 영양 성분이 달랐고, 제품을 선택할 때 주로 어떤 경로를 거치는지 확인할 수 있었습니다. 유사한 단어(종합 비타민, 멀티 비타민) 중에서도 어떤 단어가 각 세대에게 더 친숙한지도 파악할 수 있었습니다.

이하 분석결과를 바탕으로 아로나민측에게 아로나민의 마켓팅 전략을 세 가지 제시하였습니다.

