## 🏛️ 무인국사 국사 통합 관리 솔루션 프로젝트
![이미지](https://github.com/kimseongho3077/KT-AI-Project/blob/main/%EC%86%8C%EA%B0%9C%EC%9D%B4%EB%AF%B8%EC%A7%80.jpg?raw=true)

## 💡 제안 배경
`중대재해처벌법` `산업안전보건법` 등 노동자의 안전과 사고에 대한 규칙이 강화되고 지속적인 KT아현 국사, SK C&C화재, 삼성 SDS화재 등  
지속 적인 IDC 화재사고로 인한 피해가 계속되고 있고 2022년 한해 `화재 경보 오작동`으로 인한 손해가 약 `29억`원 규모 이며 이를 `CCTV`와
`AI`의 결합을 통해 비용절감과 화재 및 침입자를 탐지하고 작업자의 안전에 도움을 주고자 시작 되었다.

## ❓ 국사란?
정보통신 서비스를 제공하기 위한 시설의 수용 및 운용, 유지보수, 마케팅 및 영업 활동을 하기 위한 일반 전화국이나 분국의 건물을 말한다.

## ✨ 기대효과
- 인력 최소화
    - 노동 인구 감소
    - 시설 대비 인력부족

- 국사 안전 감지 및 방지
    - 화재로 인한 피해규모 축소
    - 작업자의 안전사고에 대한 빠른 탐지

- 비용 및 에너지 절감
    - 다양한 시스템 제공으로 절감

## 🍀 사용 기술
- ***python***
- ***html5***
- ***css3***
- ***javascript***
- ***SQLite***
- ***Django***
- ***YOLOv8***
- ***FFmpeg***

## 📊 서비스 플로우
<img width="1036" height="545" alt="Image" src="https://github.com/user-attachments/assets/bd72b118-f769-46dd-87b5-60c047304647" />

## 📊 3-티어 아키텍쳐
<img width="1132" height="565" alt="Image" src="https://github.com/user-attachments/assets/8a46d8c1-f15a-456f-9199-ecf58724f6a8" />

## 📺 팀 구성원

 |이길원|김성호|김유민|박준우|이근섭|이현빈|정재훈|
 |:---:|:---:|:---:|:---:|:---:|:---:|:---:|
 |조장,FE|BE|BE|FE|AI|FE|AI|
 |[@ROADwon](https://github.com/ROADwon)|[@kimseongho3077](https://github.com/kimseongho3077)|[@Kymcat](https://github.com/Kymcat)|[@always97](https://github.com/always97)|[@GS0704](https://github.com/GS0704)|[@leehyunbeen](https://github.com/leehyunbeen)|[@op-6160](https://github.com/op-6160)|
  
## 📑 주요 담당 파트
### ✔ 세션 미들웨어 
```python
class CheckSessionExpiryMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        
        # 세션 만료 + 로그인/로그인검사/회원가입/회원가입검사 URL이 아닐 때
        if 'user' not in request.session and \
            request.path not in \
            ['/', '/login/submit/', '/register/', '/register/priv/','/register/submit/', '/register/id_inspection/'] :
            
            return render(request, 'session/sessionAlert.html')  # 세션 만료 시 로그인 화면으로 이동

        response = self.get_response(request)   
        return response
```
- 커스텀 로그인 기능과 연동을 하기위한 세션 미들웨어를 제작
- 뷰마다 세션을 검사할 필요없이 미들웨어로 자동 검사
- setting.py 파일에서 세션 시간과 자동만료 태그를 작성
- 세션 값으로는 최소한의 정보를 삽입

##
### ✔ 작업일지 게시판
<img width="1317" height="562" alt="Image" src="https://github.com/user-attachments/assets/6336bac9-b7c4-49f4-9eb9-787533969ba2" />
  
- 게시글 작성은 어느 회원이든 작성 가능
- "승인"은 오직 관리자 회원만이 할 수 있게 구현
- 기본적인 게시판의 기능인 검색, 삭제, 수정 구현

##
### ✔ 영상 타임스탬프 및 점프 기능
<img width="1248" height="569" alt="Image" src="https://github.com/user-attachments/assets/69692036-f867-41b2-bda7-4785cf0fa151" />
  
- 영상 업로드시, YOLO모델에서 자동으로 이벤트 탐지 및 이벤트 로그 작성
- 해당 파일들을 가져와 화면에 출력하도록 구현
- 이벤트 로그에서 시간을 클릭 시, 영상의 해당 시간으로 점프하도록 구현
