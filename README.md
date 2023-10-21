## :raised_hands: 소개
**[ENG]**
CSD Server receives the sound as a request and converts it into a spectrogram image to run the model and output the result value.
<br>
**[KOR]**
소리를 요청으로 받고 스펙트로그램 이미지로 변환해 모델을 돌리고 결과값을 출력해주는 CSDServer 입니다. 
<br><br>

## 💪 주요 기능
**[ENG]**
Take the acoustic byte Array from the client, convert it to an ac file, and convert it to a wav file.
Use the liborasa library to convert the wave file into a spectrogram image in the form of a time-frequency graph.
Apply the converted image to the CSD-Model to extract the alphabetic result value and send a POST response to the client.
<br>
**[KOR]**
client로부터 음향 byteArray를 받아 이를 acc 파일로 변환을 한뒤 wav 파일로 변환을 합니다. 
wav 파일을 liborasa 라이브러리를 사용하여 시간-주파수 그래프 형태의 스펙트로그램 이미지로 변환합니다. 
변환된 이미지를 CSD-Model에 적용시켜 알파벳 결과값을 추출하여 client에게 POST 응답을 보냅니다.
<br><br>

## 🦾 주요 기술
**Server - Django**
* PyCharm IDE
* Django 4.2.5
* Djangorestframework 3.14.0
* Librosa 0.10.1
* Matplotlib 3.7.2
* Numpy 1.25.2
* Pillow 10.0.1
* Pydub 0.25.1
* Torch 1.13.1
* Torchvision 0.14.1
<br><br>

## 🔗 서비스 아키텍처
![Section 2](https://github.com/CAP-JJANG/CSD-Server/assets/100428958/acb1085a-0716-4191-9acf-5e6d17eab4c9)
<br><br>

## 🔗 디렉터리 구조
  ```bash
CSDServer
├── CSDServer
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── development.py
│   │   ├── local.py
│   │   └── production.py
│   ├── urls.py
│   ├── views.py
│   └── wsgi.py
├── __init__.py
├── manage.py
├── requirements
│   ├── base.txt
│   ├── local.txt
│   └── production.txt
└── venv
└── static
    ├── audio
    │   ├── combined.wav
    │   └── silent.wav
    ├── images
    │   └── test.jpg
    └── resnetModel
        └── resnet34.pth
```
<br><br>

## ⭐️ 설치 방법

1. clone [github 리포지토리 주소]
2. cd CSD-Server/CSDServer
3. 가상환경 생성
    1. python -m venv venv 또는 python3 -m venv venv
4. 가상환경 실행
    1. Windows
        1. venv\Scripts\activate
    2. macOS 및 Linux
        1. source venv/bin/activate
5. pip 최신버전으로 업그레이드
   python -m pip install --upgrade pip
    또는
   python3 -m pip install --upgrade pip
6. 패키지 설치
    1. pip install -r requirements.txt
    2. pip3 install -r requirements.txt <br>
7. secrets.json 파일 생성
   ```bash
    ├── CSDServer
    │   ├── __init__.py
    │   ├── __pycache__
    │   ├── asgi.py
    │   ├── settings
    │   ├── urls.py
    │   ├── views.py
    │   └── wsgi.py
    ├── __init__.py
    ├── manage.py
    ├── requirements
    ├── secrets.json
    └── static
    ```
   django 프로젝트를 생성했을 때 settings.py 파일 안에 있는 SECRET_KEY를 가지고 
    {"SECRET_KEY" : ( secret key 입력 )} 형태로 secrets.json 파일에 작성합니다. 
8. migration
    1. python manage.py makemigrations
    2. python manage.py migrate
    또는
    1. python3 manage.py makemigrations
    2. python3 manage.py migrate
10. 로컬 실행
    1. python manage.py runserver 또는 python3 manage.py runserver
<br><br>

## 👏 API ENDPOINT
process_audio
: byteArray 받아서 모델돌리고 숫자 예측값 변환
- URL
    
    /process_audio/
    
- Method
    
    `POST`
    
- URL Params
    
    None
    
- Data Params
    
    
    | key | value |
    | --- | --- |
    | ‘recordData’ | byteArray |
    |  |  |
    
- Success Response:
    
    code : 200
    
    content : 
    
    ```json
    [
    	{
    		"predicted_alphabet": String,
    	}
    ]
    ``` 
<br><br>

## 🤖 라이센스
This project is licensed under the Apache License 2.0 - see the [LICENSE](https://github.com/CAP-JJANG/CSD-Server/blob/main/LICENSE) file for details.  
[OSS Notice](https://github.com/CAP-JJANG/CSD-Server/blob/main/OSS-Notice.md) sets forth attribution notices for third party software that may be contained in this application.

