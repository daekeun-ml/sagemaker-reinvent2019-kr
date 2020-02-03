# SageMaker New Features

## Introduction
AWS re:Invent 2019에 소개된 SageMaker의 신규 서비스들에 대한 예제 노트북들을 한글화하였습니다. 또한 re:Invent 2019 이전에 소개된 신규 서비스(Multi-Model Endpoint)에 대한 예제 노트북들도 한글화하였습니다.

## re:Invent 2019 Updates
### SageMaker Processing
- [Scikit-Learn Data Processing and Model Evaluation](sagemaker-processing/scikit_learn_data_processing_and_model_evaluation.ipynb)
- [Feature transformation with Amazon SageMaker Processing and SparkML](sagemaker-processing/feature_transformation_with_sagemaker_processing.ipynb)

### SageMaker Experiments
- [MNIST Handwritten Digits Classification Experiment](sagemaker-experiments/mnist-handwritten-digits-classification-experiment.ipynb)

### SageMaker Debugger
- [Using a built-in rule with TensorFlow](sagemaker-debugger/tensorflow_builtin_rule/tf-mnist-builtin-rule.ipynb)
- [Tensorflow Action On Rule](sagemaker-debugger/tensorflow_builtin_rule/tf-mnist-stop-training-job.ipynb)

### SageMaker Model Monitor
- [Introduction to Amazon SageMaker Model Monitor](sagemaker-model-monitor/SageMaker-ModelMonitoring.ipynb)

### SageMaker Autopilot
- [Direct Marketing with Amazon SageMaker Autopilot](autopilot/sagemaker_autopilot_direct_marketing.ipynb)
    - [Autopilot에서 자동으로 생성한 노트북: Autopilot Candidate Definition Notebook](autopilot/SageMakerAutopilotCandidateDefinitionNotebook.ipynb)
    - [Autopilot에서 자동으로 생성한 노트북: Autopilot Data Exploration Notebook](autopilot/SageMakerAutopilotDataExplorationNotebook.ipynb)

### Deep Grarph Library(DGL)
- [Training Amazon SageMaker models for molecular property prediction by using DGL with PyTorch backend](dgl_gcn_tox21/pytorch-gcn-tox21.ipynb)
- [Hyperparameter tuning with Amazon SageMaker for molecular property prediction](dgl_gcn_tox21/pytorch-gcn-tox21-hypertune.ipynb)

## Pre re:Invent 2019 Updates
### Multi Model Endpoints
#### 특장점
새 모델을 추가할 때 엔드포인트(Endpoint) 중단/수정 없이 실시간으로 곧바로 배포(deployment) 가능합니다.

SageMaker에서 배포용 Model을 생성할 때 `MultiModel` 모드를 설정하고 `ModelDataUrl`에 모델 아티팩트(Model Artifact)들이
저장될 S3 경로를 설정하면, 새로운 모델 아티팩트를 S3에 업로드하고 처음 호출하는 즉시 동적으로 해당 모델 아티팩트를 인스턴스로 다운로드하고 컨테이너의 메모리에 모델을 로드합니다.
(따라서 첫 호출 때는 지연 시간이 많이 발생하기 때문에 실시간 예측이 중요한 경우는 사용하기 어렵습니다.)
 
기존에는 모델 아티팩트명이 `model.tar.gz`로 지정이 되어 있었고 단일 엔드포인트에는 동일 알고리즘 및 동일 모델 내에서 다른 하이퍼파라메터의 설정만 가능했지만.
이 기능으로 인해 동일 알고리즘 내에서는 다양한 변형 모델들을 자유롭게 배포할 수 있게 되었습니다.
대표적인 활용 예시는 지역별 아파트 매매가 예측 모델이나 고객 seg별 상품 추천, 탈회 예측 등입니다.<br>
구체적으로 서울&부산 아파트 매매가를 예측하는 두 개의 모델들이 (`model_seoul.tar.gz`, `model_pusan.tar.gz`)가 S3에 있는 상태에서
대전 아파트 매매가를 예측하는 모델(`model_daejeon.tar.gz`)을 s3에 업로드하면 곧바로 대전 아파트 매매가 예측 모델도 사용 가능합니다.

- [Amazon SageMaker Multi-Model Endpoints using Scikit Learn](multi-model-endpoint/sklearn_multi_model_endpoint_home_value.ipynb)
- [Amazon SageMaker Multi-Model Endpoints using XGBoost](multi-model-endpoint/xgboost_multi_model_endpoint_home_value.ipynb)
- [Amazon SageMaker Multi-Model Endpoints using your own algorithm container](multi-model-endpoint/multi_model_endpoint_bring_your_own.ipynb)

## License Summary
이 샘플 코드는 MIT-0 라이센스에 따라 제공됩니다. LICENSE 파일을 참조하십시오.