# Hey, Jarvis

📢 2023년 겨울학기 [AIKU](https://github.com/AIKU-Official) 활동으로 진행한 프로젝트입니다. </br>

🎉 2023년 겨울학기 AIKU Conference 우수상 수상!

## 소개

컴퓨터에서 이용 가능한 Virtual assistant를 만들어 보았습니다. </br>
아이언맨의 [J.A.R.V.I.S](https://namu.wiki/w/J.A.R.V.I.S.)에서 영감을 얻었습니다. </br>
그렇기에 J.A.R.V.I.S 목소리의 TTS를 모델을 이용했습니다. </br>


## 방법론

Virtual assistant를 이용하는 과정은 일반적으로 다음과 같습니다.
1. Wakeword로 assistant를 호출한다. (ex. 헤이 빅스비, 시리야)
   - VAD (Voice Activity Detection) task 의 일종으로, 여러 소리 중 특정 사람 목소리를 인식하는 작업입니다.
2. Virtual assistant에게 말을 건다.
   - STT (Speech to Text) task입니다.
3. Virtual assistant가 대답한다.
   - TTS (Text to Speech) 작업입니다.
4. 대답한 내용에 알맞는 행동을 한다. ( ex. 검색, 화면 녹화)
   - Task에 해당하는 작업 구현입니다. 현재 지원하는 기능은 날씨 묻기, gpt에 질문하기. 화면 녹화입니다.

Hey, Jarvis 프로젝트는 위 네 과정을 구현하였고, 각각의 과정에서 이용한 모델이나 세부 구현 과정은 다음과 같습니다.

1. VAD </br>
   Picovoice의 [porcupine](https://picovoice.ai/platform/porcupine/)모델을 이용하였습니다.</br>
   다양한 언어를 대상으로 특정 wakeword를 인식하는 모델을 제공해줍니다.</br>
   월 3회 만들 수 있고, 모델을 다운로드 받아 로컬에서 돌릴 수 있습니다.</br>
   
2. STT</br>
   여러 STT 모델을 이용하게 해 주는 Python의 [Speech Recognition](https://pypi.org/project/SpeechRecognition/) 라이브러리를 이용하였습니다. </br>
   본 프로젝트에서는 인식률이 가장 좋았던 Google cloud 모델을 이용하였습니다.</br>

3. TTS</br>
   [XTTS-v2](https://huggingface.co/coqui/XTTS-v2) 모델을 이용했습니다. </br>  6초의 음성으로 특정 목소리로 TTS 모델을 학습시킵니다. </br>
   API와 모델을 모두 이용할 수 있는데, 여기서는 API를 활용했습니다.

4. 구현</br>
   최대한 속도를 올리는 방향으로 구현했습니다. 구현된 기능은 총 세 가지입니다.</br>
   - 날씨 묻기</br>
     특정 도시의 날씨를 알려줍니다. 기상청 API 허브를 이용하여 구현했습니다.
   - 화면 녹화</br>
     일정 시간동안 화면을 녹화해줍니다. 현재 프레임은 10정도로 제한됩니다.
   - gpt 질의</br>
     gpt로 질의합니다.


## 환경 설정
Python 3.11을 기준으로 만들었습니다.
설치해야 하는 패키지들은 requirements.txt에 기록되어 있습니다.


## 사용 방법
1. 기상청 api 허브의 api키, gpt의 api 키와 picovoice의 api 키를 준비합니다.
2. ```pip install requirements```
3. ```python recognition --weather_api 날씨 api --openai_api gpt api ----porcupine_api picovoice api```


## 예시 결과
GUI 없이 구현했습니다.


## 팀원

- [박수빈](https://github.com/subin9): VAD, TTS, STT, 날씨 구현

- [장지윤](https://github.com/chiefJang): GPT retrieval 코드 작성

- [김정우](https://github.com/kmjnwn): 폴더 이동 구현, IO exception handling
