# multivariate time-series datasets of Electricity Transformer Temperature Datasets(ETT)


전력 분배 문제는 전기의 순차적 사용에 따라 여러 지역으로 전력을 분배하는 것입니다. 하지만 특정 지역의 수요는 평일, 공휴일, 계절, 날씨, 기온 등에 따라 달라지기 때문에 예측이 어렵습니다. 

따라서 미래의 장기 전기 사용량을 예측하는 효율적인 방법이 없으면 관리자는 실제 수요보다 훨씬 높은 경험적 수치를 기반으로 결정을 내려야하며, 이는 불필요한 전기 낭비를 초래합니다.
해당 데이터는 이러한 장기 전력 분배 문제를 해결하기 위해 수집된 데이터입니다. (전기 사용량을 기반으로 장기 전력 급전을 예측하기 하기 위함)

시간별 데이터(ETTh1, ETTh2)와 15분 간격 데이터(ETTm1, ETTm2)로 구분합니다.
이는 6개의 external power load features와 날짜, ‘oil temperature(오일온도)’ 를 포함한 8가지 feature로 구성되며, 오일 온도는 변압기의 상태를 반영할 수 있습니다. 전기 변압기의 오일 온도를 예측하여 변압기의 안정성 판단에도 사용할 수 있습니다(단변량 시계열 예측). 

<p align="center">
<img src=".\img\dataset_year.png" height = "320" alt="" align=center /> 
<br><br>
<b>Figure 1. </b>The overall view of "OT" in the ETT
</p>
특히 데이터 세트는 단기 주기 패턴, 장기 주기 패턴, 장기 추세 및 다양한 불규칙 패턴을 결합합니다. 먼저 그림 1에서 전체적인 모습을 보여주며,계절적 추세를 보입니다.

<p align="center">
<img src=".\img\auto_correlation.png" height = "320" alt="" align=center />
<br><br>
<b>Figure 2. </b>The autocorrelation graph of all variables.  
</p>

그림 2는 장기 및 단기 반복 패턴의 확인하기 위한 ETTh1 데이터 세트의 모든 변수에 대한 자기 상관을 나타내는 그래프입니다. 위의 파란색 선은 목표 OT (오일 온도)이며, 단기 지역성을 유지합니다. 그러나 다른 변수(전력부하)는 단기 일일 패턴(24시간마다)과 장기 주간 패턴(7일마다)을 나타냅니다.

<p align="center">
<img src=".\img\ETT.png" height = "150" alt="" align=center />
<br><br>
<b>table 1. </b>ETT data.
</p>

이러한 장기 전력 소모량 예측과 같이 긴 길이의 다변량 시계열을 예측하기 위해서는 인풋과 아웃풋 사이의 긴 범위의 의존성을 정확히 포착하는 모델의 높은 예측 용량이 요구됩니다. (Long sequence time-series forecasting)

최근 연구들은 딥러닝 기반의 Transformer 모델이 예측 용량을 증가시킬 수 있는 잠재력을 가지고 있다는 것을 보여줬으며 이를 응용한 모델을 이용하여 문제를 풀고 있습니다.
