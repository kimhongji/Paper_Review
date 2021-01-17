# CWL-Airflow: a lightweight pipeline manager supporting Common Workflow Languag
link: https://academic.oup.com/gigascience/article/8/7/giz084/5535758?login=true

2021/1/17 ~ 

------------------

1. 요약  
방대한 양으로 생성되는 데이터를 처리하고 분석하고 관리하기 위한 파이프라인의 사용이 의학 연구에서 많이 발전되고 있다. 하지만 각각 100개 이상의 매니저를 이용하여 파이프라이닝 하고 각기 다른 워크플로우를 관리하는 것이 굉장히 어려웠다. 이러한 이유를 통해 Common Workflow Language(CWL)이 최근 소개가 되었고, 기존의 파이프라인과 워크플로우 매니저들에 변화를 가져왔다. 본 논문에서는 CWL-Airflow를 제안한다. 이는 아파치 Airflow에 CWL을 지원하도록 발전시킨 모델이다. 본 논문에서는 CWL 1.0을 사용하며, linux/macOS 에서 stand-alone, 클러스터, 클라우드 환경에서 동작 가능하다. 실험에서 사용된 CWL 파이프라인을 위한 데이터는 염색질 면역(?) 순서(chromatin immunoprecipitation sequencing) 데이터를 이용한다. 결론적으로, CWL-Airflow는 사용자로 하여금 전체적인 파이프라인의 특징을 제공할 것이며 노트북, 클러스터, 클라우드 어떤 환경에서도 Airflow가 동작할 수 있도록 CWL을 실행할 수 있다. 

2. 배경  



