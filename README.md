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

## 환경 설정
Requirements.txt에 기록되어 있습니다.

## 사용 방법

(프로젝트 실행 방법 (명령어 등)을 적어주세요.)

## 예시 결과

(사용 방법을 실행했을 때 나타나는 결과나 시각화 이미지를 보여주세요)

## 팀원

(프로젝트에 참여한 팀원의 이름과 깃헙 프로필 링크, 역할을 작성해주세요)

- [홍길동](홍길동의 github link): (수행한 역할을 나열)
