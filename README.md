<details>
<summary>서울시 지역단위 '소득', '지출', '금융자산' 정보</summary>
<div markdown="1">       
<br>- 데이터 수집 경로 : [2021 금융 데이터 경진대회] 참가자 제공용 데이터 (출처: 신한은행)<br><br>
- 데이터 설명 및 항목 : 보안 상 공개 불가<br><br>
- 전처리 방법 : 보안 상 공개 불가
</div>
</details>


# 1. 배경 & 목적

---

- 분석 주제명 : 상업용 부동산 가치 창출을 위한 소상공인 매출등급 예측모형 제작 및 활용 방안 제시
- 분석 배경 : 2023년 초 코로나 사태 종료 후 고물가, 고금리, 고환율 등으로 인해 소상공인 위기감은 계속 증가하여 상업용 부동산 시장이 침체되었습니다. 특히, 창업/폐업 비율이 상대적으로 높은 요식업의 정확한 매출 진단을 통해 폐업 예방 및 상권 활성화 방안 모색 등 상업용 부동산의 가치 창출을 도모하고자 합니다.
- 분석 목적 : 서울특별시 지역상권의 특성 및 세부적인 (소상공인) 물건지의 입지조건을 분석하여 지역상권 경제에 영향을 미치는 소상공인 매출규모를 예측하고자 합니다. 이는 지역경제에 필요한 정보를 제공할 수 있는 기회가 될 것이라고 사료됩니다.

# 2. 주최 & 참가 대상 & 성과

---

- 주최: 과학기술정보통신부, 한국지능정보사회진흥원
- 참가 자격 및 팀 인원 제한 사항: 데이터에 관심있는 누구나, 개인 또는 팀(팀장 포함 최대 4명)
- 성과: ~ING

# 3. 프로젝트 기간(대회 기간)

---

- 사전 분석계획서 제출 마감: 2023년 9월 15일
- 결과보고서 제출 마감: 2023년 9월 27일
- 1차 서류심사: 2023년 10월 7일 ~ 11월 7일(심사 중)

# 4. 담당 역할

---

### 강수연

- **역할과 책임**
    
    SQL 쿼리문을 통한 서울특별시 소상공인 KCD 신용 데이터∙상권특성 공공 데이터의 추출과 병합, Python을 활용한 결측값 대체와 2단계 머신러닝 모형 클래스 구현을 맡았습니다. 
    
- **성장한 경험**
    
    소호 신용 데이터의 익명정보 처리와 분기 데이터를 계절성 지수를 생성하고 결합함으로써 월별로 확장하여 시계열 패턴을 반영하는 전처리를 수행하였습니다. 
    

### 정가연

- **역할과 책임**
    
    서울특별시 상권 분석 서비스 데이터와 SQL 쿼리문을 통해서 신용 데이터 수집 후 병합을 진행하였습니다.  결측값의 50%는 유사도 기준으로 근접한 변수 간 그룹화해서 처리했습니다. 
    
    분기로 이뤄진 상권 데이터를 월별 데이터로 확장해서 이종 데이터의 시계열을 일치시켰습니다. 이를 위해 신용거래정보 기반의 월별 계절성 지수를 파생하여 상관관계가 있는 변수와 1차원 축소된 값을 곱하는 방식으로 확장해보았습니다.
    
    시계열적인 패턴을 고려해서 23년 1월, 2월 매출등급 예측 회귀 모델을 구축한 후 모델링을 진행하였습니다.
    
- **성장한 경험**
    
    SQL 쿼리문을 통해서 데이터 수집해보았고 칼럼의 수가 200개 가 넘는 다량의 데이터를 결합해보았습니다.
    
    데이터들의 시계열을 일치시키기 위해서 PCA 기반의 계절성 지수를 만들어서 데이터에 시계열적인 특성을 포함시키는 방법론을 적용해보았습니다.
    
    22년 데이터를 사용해서 23년 1월을 예측하였고, 23년 1월을 포함해서 23년 2월 예측을 진행해보며 시계열 데이터 기반의 회귀분석 예측을 진행해볼 수 있었습니다.
    

### 최민

- **역할과 책임**
    
    KCD 신용데이터, 공공데이터를 분석한 결과를 Tableau를 활용해 상권특성 시각화를 진행하였습니다.
    
    <상권의 특징>
    
    1. 카드 / 배달 매출액 변동계수와 매출등급 간의 관계
    2. 객단가와 매출등급 간의 관계
    3. 손익분기점과 매출등급 간의 관계
    4. 부가세 차감 전 영업이익과 매출등급 간의 관계
    
    를 라인차트와 막대그래프를 이용하여 시각화 하고 의미있는 인사이트를 도출하였습니다. 
    
- **성장한 경험**
    
    SQL문을 사용하여 데이터를 수집 및 정제하였습니다. 시각화를 진행하는 과정에서 도메인지식과 분석결과를 연결하여 설명하였습니다. 
    

# 5. 데이터 분석 Process

---

## ch0. 데이터 수집 
<details>
<summary>데이터 수집</summary>
<div markdown="1">       
<br>- 2022년~2023년 서울열린데이터 광장의 상권 특성 관련 공개 데이터셋 <br>
<br>유형 : 서울시 행정동별 지하철 총 승차 승객 정보, 서울시 행정동별 버스 총 승차 승객수 정보, 서울시 우리마을가게 상권분석 서비스(행정동별 상권변화지표) <br>
<br>수집 방법 : 서울열린데이터광장 홈페이지에서 다운로드하였습니다.<br><br>

<br>- 2022년~2023년 한국신용데이터 KCD 소상공인 신용데이터셋<br>
<br>유형 : 업장 매출입 정보, 임대 종류, 신규 고객 수, 카드 매출액, 배달 매출액 , 월 임대료 표준 값, 임대보증금 표준 값, 배달 매출액 표준값, 카드 매출액 표준값, 임대종류, 경영위기 FLAG, 매장 면적 등<br>
<br>수집방법 : 디사일로 데이터 클린룸에서 반출하였습니다.<br><br>

<br>-2022년~2023년 (주)오아시스비즈니스의 수익형 부동산 관련 공개 데이터셋<br>
<br>유형 : 상업용 부동산거래량(금액) 대비 유동인구상업용 부동산의 공실률 대비 매매가, 임대료, (이하 ‘매매가 점수’)<br>
<br>수집 방법 : 빅데이터 플랫폼에서 다운로드하였습니다.<br><br>
</div>
</details>

<details>
<summary>활용 데이터</summary>
<div markdown="1">       
<br>- 서울열린데이터광장의 상권특성 관련 공개 데이터셋 <br>
<br>- 한국신용데이터 KCD 소상공인 신용 데이터셋<br>
<br>- (주)오아시스비즈니스의 수익형 부동산 관련 공개 데이터셋<br>
</div>
</details>

## ch1. 데이터 전처리

### 1-1. 이상치 처리 및 결측값 대체
<details>
<summary>분석 의도</summary>
<div markdown="1">       
<br>- 데이터 )<br>
</div>
</details>

<details>
<summary>결과</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>시행착오</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

### 1-2. 파생변수 생성 및 시계열 확장
<details>
<summary>분석 의도</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>결과</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>시행착오</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

### 1-3. 이종 데이터 병합
<details>
<summary>분석 의도</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>결과</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>시행착오</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

## ch2. 데이터 분석 모형 구축
<details>
<summary>분석 의도</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>결과</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>시행착오</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

## ch3. 데이터 시각화
### 3-1. 예측 매출등급 및 상권특성 시각화
<details>
<summary>분석 의도</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>결과</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

<details>
<summary>시행착오</summary>
<div markdown="1">       
<br> <br>
</div>
</details>

## ch4. 한계와 의의

### 4-1. 한계

- **모델링 관점**
    
    회귀 모델을 선택하는데 근거가 부족했다고 생각합니다. 모델을 선택했던 기준은 기본 모델인 Linear Regression, DecisionTreeRegressor, RandomForestRegressor 모델의 성능을 비교해본 후 가장 성능이 좋았던 RandomForest Regressor모델을 선택하였습니다. 모델의 구조를 이해한 후 본 데이터에 가장 적합한 모델을 선택하는 검증 과정이 추가로 필요하다고 사료됩니다.
    
    Scaler 적용, 모델 Ensemble, Hyper Parameter Tuning 등과 같은 모델의 성능을 높이기 위한 다양한 시도를 해보지 못했던 점이 아쉬웠습니다. 이와 같은 방법론을 적용한다면 성능 개선을 가져올 수 있을 것이라 생각합니다.
    
- **시각화 관점**
    
    필지고유번호를 반영하여 맵차트를 만들고 그 안에 매출액 예측등급을 시각화하려는 목표를 가지고 있었으나, 필지고유번호와 매출등급 및 상권특성을 함께 매핑해둔 데이터프레임의 부재로 실행하지 못한점이 아쉽습니다. 또한, 막대그래프와 라인차트 뿐만 아니라 파이차트, 도넛차트, 맵차트, 히트맵 등 변수의 특성에 따라 다양한 시각화 기법을 적용해보는 것도 필요합니다. 
    
- **도메인 관점**
    
    소호 사업장의 입지(세부적인 물건지) 분석에 그치지 않고 광역적인 상권분석을 위한 공간 데이터를 시각화하여 하위 매출등급(평당 고정비용 대비 매출액 백분위수)에 대한 솔루션 제안이 필요합니다. 
    

### 4-2. 의의

- 첫째, 출처 ∙ 수집경로 ∙ 시계열이 다른 소상공인 신용 데이터 ∙ 상권특성 데이터를 모형에 투입할 수 있도록 병합하는 전처리 과정의 중요성을 배웠습니다.
- 둘째, 최적화된 매출등급 예측모형을 적합하고 시각화하는 것을 넘어 상권 ∙ 입지분석 도메인에 따른 결과 활용 방법 제안의 필요성을 깨달았습니다.
- 셋째, 매출등급예측모형을 통해 해당 상권 및 업종에서 앞으로의 매출 경향성을 미리 파악해 볼 수 있었습니다. 또한, 해당 상권의 입지 데이터 시각화를 통해 매출액 예측등급에 미치는 요인들을 분석하고 활용할 수 있습니다.

## ch5. 피드백
- **프로젝트 소감**
    
    
    | 이름 | 소감 |
    | --- | --- |
    | 강수연 |  |
    | 정가연 | 상권, 부동산, 신용과 관련한 다양한 데이터를 수집하고 병합하는 과정을 거치면서 함수 생성, 반복문 작성 등 데이터 처리 실력을 향상할 수 있었습니다. 추후 클래스에 대한 공부를 더 진행해서 객체 지향적인 코드를 짜도록 노력할 것입니다. 
    기존 데이터 분석 과제를 수행할 때는 정제되어 있는 데이터를 사용했고 다양한 모델을 구현해보는데 집중하곤 하였습니다. 하지만 실제 데이터 분석에 있어서는 원본 데이터를 도메인에 맞게 처리하는게 중요하다는 것을 알게 되어서 신기했습니다.
    PCA, 계절성지수 생성, 시계열 예측 등 다양한 분석 방법론을 적용해볼 수 있어서 좋았고 팀원들과 함께 즐겁게 프로젝트를 수행0할 수 있었습니다. 이번 프로젝트를 계기로 데이터 분석 분야에 더 흥미를 가지게 된 것 같습니다 :D  |
    | 최민 |  |

- **동료 피드백**
    
    
    | 강수연 | 정가연 | 최민 |
    | --- | --- | --- |
    | 팀원들을 배려하고 잘 이끌어준 좋은 팀장님이셨습니다! 프로젝트를 진행하면서 필요한 테스크가 무엇인지 파악한 후 팀원들의 역량에 맞게 업무를 잘 분배해 주셨습니다. 또한 데이터 수집 및 처리를 꼼꼼하게 진행해주셨고 프로젝트가 원할하게 돌아가도록 전체적인 흐름을 이끌어 가주셨습니다. 데이터 분석 분야에 정말 열정이 있다고 느꼈고 덕분에 많이 배워갈 수 있었습니다.  |  | 항상 열심히 분석을 진행해주시고 프로젝트를 하느라 지칠 때마다 응원의 말을 건내주는 좋은 팀원이셨습니다! 
    SQL쿼리문을 통해서 데이터를 잘 수집해주셨고 시각화를 통해 인사이트를 도출해주셨습니다.  
    데이터 분석부터 시각화까지 진행하시는 모습을 보며 정말 배울점이 많은 팀원분이라고 생각했습니다! |
    |  |  |  |


# 6. 증빙자료

---

### 보고서 및 발표자료

- [결과보고서_로케핀셋_빅데이터플랫폼 활용 분야](https://drive.google.com/file/d/1GOZkAycEKG2fggqb6brEjziE9jmaVPbf/view?usp=sharing)
- [발표자료_로케핀셋_빅데이터플랫폼 활용 분야](https://drive.google.com/file/d/18KjEQR5qd51MkyIp1za3DV3rmYAodOs2/view?usp=sharing)

### 코드

- [0. [KCD_SOHO_PATH] DATA MERGE](https://colab.research.google.com/drive/1nOvkdbe2snR6EnZWVPMNxgYXIIs-YmFF?usp=sharing)
- [1. [KCD_SOHO] DATA MERGE AND DESILO SQL QUERY](https://colab.research.google.com/drive/1C9snZK2s8LfBjc7jf13AfsoHhh3I0EHI?usp=sharing)
- [2. [KCD_MARKET_CONTEST] DATA PREPROCESSING AND FIT DATETIME](https://colab.research.google.com/drive/1_8uIjBZ5-h5gxzDG3YpkfNw7VJZ7FioO?usp=sharing)
- [3. [KCD_MARKET]MERGE AND MAPPING](https://colab.research.google.com/drive/1Us8Ss7FHUsRUJZ5yasONhJ9sALPgpi7E?usp=sharing)
- [4. [KCD_MARKET_CONTEST_JOIN_MON_SEASON]SEASONALl EXPAND PCA AND MERGE LABEL](https://colab.research.google.com/drive/13aD15-1012pp9oJwpqA1uTCm9AolYkP4?usp=sharing)
- [5. [상권,신용,대회] DATA MERGE & Preprocessing](https://colab.research.google.com/drive/1tadAZHSsS8yBLWvcqQM8JXvc531L8KRa?usp=sharing)
- [6. REGRESSION_MODELING](https://colab.research.google.com/drive/1nbl7luGMs6AdwaQUxLXS-WLmkLDsd30b?usp=sharing)
- [7. [KCD_MARKET]_VISUALIZATION](https://drive.google.com/file/d/1vo6ayuONSvQRmPIIZa-cV1NKU3OH9UHG/view?usp=sharing)
