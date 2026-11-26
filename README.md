# Manga Trans Studio

일본어 만화 이미지를 **원문을 지우지 않고 검수**한 뒤, 승인한 번역만 말풍선에 넣어(식자) 한국어 만화 이미지로
내보내는 Windows 프로그램입니다.

- 일본어 OCR(manga-ocr)과 말풍선·글자 자동 찾기
- ANIS Trans(로컬 번역 서버) 연결 — 앞뒤 대사를 문맥으로 함께 보냄
- 원문 옆에 번역을 띄워 검수하고, **승인한 대사만** 최종본에 반영
- 일본어 지우기(흰 말풍선은 말풍선 색, 그림 위 글자는 AI 복원) + 한국어 자동 식자
- JPG/PNG/ZIP/PDF 출력, 검수본 PDF, 자동 저장과 복구 백업
- 원본 이미지는 절대 바꾸지 않습니다 (읽기 전용 백업 + 해시 검사)

## 다운로드

오른쪽(또는 위쪽)의 **[Releases](../../releases)**에서 최신 버전의 ZIP을 **모두** 받으세요.
0.1.5부터 Microsoft Store판과 **같은 프로그램**(NVIDIA GPU용 PyTorch 포함)이라 크기가 커서,
GitHub의 파일 한도(2GB) 때문에 `MangaTransStudio-<버전>-win64-part1of3.zip`, `…part2of3.zip`, `…part3of3.zip`처럼 나뉘어 있어요.

## 설치와 실행

1. 받은 ZIP을 **모두 같은 곳**에 풉니다 (약 6.5GB 공간 필요). 예: 각 ZIP을 `D:\`에 [압축 풀기] →
   모두 `D:\MangaTransStudio\` 폴더 하나로 합쳐져요. '같은 이름의 파일' 질문이 나오면 [덮어쓰기]를 고르세요
   (안내 파일 하나만 겹쳐요). **하나라도 빠지면 프로그램이 켜지지 않아요.**
   **`D:\`처럼 짧은 경로에 푸세요.** 압축 안의 경로가 길어서(최대 153자), 깊은 폴더에 풀면
   Windows 경로 길이 제한(260자)에 걸려 일부 파일이 빠질 수 있습니다.
2. `MangaTransStudio\MangaTransStudio.exe`를 실행합니다.
   폴더 안의 다른 파일도 함께 있어야 하니 EXE만 따로 옮기지 마세요.
3. 처음 실행할 때 Windows 보안 경고(SmartScreen)가 뜨면 **추가 정보 → 실행**을 누르세요
   (코드 서명이 없어서 뜨는 경고입니다).
4. 처음 켜면 체험형 튜토리얼을 안내합니다. 사용 설명서는 프로그램의 **도움말 → 사용 설명서(F1)**에 있습니다.

### "스마트 앱 컨트롤이 … 앱을 차단했습니다" 창이 뜨는 경우

Windows 11의 **스마트 앱 컨트롤**이 켜진 PC에서는 위의 SmartScreen 경고 대신 이 창이 뜨고,
**[추가 정보 → 실행]이나 관리자 권한으로 실행해도 열리지 않습니다.**
이 프로그램은 아직 코드 서명이 없어서, 스마트 앱 컨트롤이 켜져 있으면 실행할 수 없습니다.

- 대부분의 PC는 스마트 앱 컨트롤이 꺼져 있어(Windows 10에서 업그레이드했거나, Windows가 평가 후 스스로 끈 경우) 이 창이 뜨지 않습니다.
- 켜져 있는지 확인: **Windows 보안 → 앱 및 브라우저 컨트롤 → 스마트 앱 컨트롤 설정**
- 이 설정을 끄면 실행할 수 있지만, **PC 전체의 보안 기능을 끄는 것**이니 스스로 판단해 주세요.
  Windows 버전에 따라 **한 번 끄면 Windows를 다시 설치해야 다시 켤 수 있습니다.**
- **Microsoft Store판은 스마트 앱 컨트롤이 켜진 PC에서도 실행됩니다** (Microsoft가 서명). 0.1.5부터는 받은 번역 엔진도
  프로그램 안의 Python으로 실행해서, 스마트 앱 컨트롤이 켜진 채로 ANIS Trans·GeTrans(GPU 포함) 번역이 됩니다.
- 이 저장소의 ZIP(GitHub 배포판)은 서명이 없어 스마트 앱 컨트롤이 켜진 PC에서는 실행되지 않습니다.

**권장 환경**: Windows 10/11 64비트, 메모리 8GB 이상. AI 기능(OCR·글자 찾기·복원)은 CPU로 동작하며
인터넷 연결 없이 쓸 수 있습니다(모델 포함). 인터넷이 연결돼 있으면 하루 한 번 번역 엔진의 공식 GitHub에서
버전 번호만 읽어 새 버전이 나왔는지 알려 줘요(개인 정보는 보내지 않고, 자동으로 받지 않음. 설정 → 번역 엔진에서 끌 수 있어요).

여러 컴퓨터에서 같은 프로젝트를 이어서 작업하려면 **파일 → 클라우드 동기화**에서 구글 드라이브나 OneDrive 폴더를 고르세요. 저장할 때마다 사본을 보내고, 다른 컴퓨터에서 열 때 새 버전을 가져올지 물어봐요(두 곳에서 각각 고치면 덮어쓰지 않고 골라요).

### GitHub 배포판과 Microsoft Store판의 차이

| | GitHub 배포판 (이 저장소의 ZIP) | Microsoft Store판 |
|---|---|---|
| 프로그램 | Store판과 같음 (0.1.5부터) | — |
| 받기 | ZIP 여러 개(합쳐 약 4.3GB)를 같은 곳에 풀기 | Store에서 설치 (약 4.5GB) |
| ANIS Trans · GeTrans | CPU·GPU 모두 | CPU·GPU 모두 |
| 스마트 앱 컨트롤이 켜진 PC | 실행되지 않음 (서명 없음) | 실행됨 (Microsoft 서명, 번역 엔진도) |
| 업데이트 | 새 버전 ZIP을 받아 다시 풀기 | Store가 자동으로 |

0.1.4까지의 GitHub판은 크기 때문에 CPU용 PyTorch만 넣었지만, 0.1.5부터는 ZIP을 나눠서 Store판과 같은 프로그램을 올려요.

## 번역 엔진 설정은 도우미가 안내해요

프로그램을 실행하고 **설정 → 번역 엔진 설정 도우미…**를 여세요(엔진이 없으면 처음 켤 때 저절로 열려요).
한 단계씩 깜빡이는 버튼으로 안내하고, 압축 풀기·GeTrans 기본 모델 받기·이 컴퓨터에 맞는 설정·시험 번역을 대신 해 줍니다.
0.1.5부터는 받은 엔진을 프로그램 안의 Python으로 바로 실행해서 **Python 설치·엔진 설치 단계가 없어요.**
GeTrans는 **0.2.0부터 받은 압축 안에 번역 모델(어댑터)이 들어 있어** Hugging Face 로그인도 필요 없어요(옛 0.1.x만 따로 받음).
직접 할 일은 **엔진 받기와 라이선스 동의**뿐이에요.

- **설치 위치**: 처음에 엔진을 둘 곳을 물어요. [알아서 해 주세요]를 고르면 여유 공간이 넉넉한 다른 드라이브(예: D)를
  골라 Windows 드라이브를 비워 두고, 원하면 직접 고를 수 있어요. 엔진·설치 파일·GeTrans 기본 모델(약 9.6GB)이 모두 그 폴더에 모여요.
- **이 컴퓨터에 맞는 설정**: GPU 메모리·RAM·CPU를 보고 추천해요 (GPU 메모리 12GB 이상이면 두 엔진 동시 실행,
  CPU가 느리거나 RAM이 12GB보다 적으면 ANIS Trans만).

번역 엔진은 두 가지를 쓸 수 있어요 (둘 다 이 배포 파일에는 들어 있지 않음, 재배포 금지):
- **ANIS Trans** — 가볍고 빠름 (CPU 또는 NVIDIA GPU)
- **ANIS GeTrans** — 문맥에 강하지만 무거움 (GPU 메모리 12GB 이상이면 GPU, 아니면 CPU · RAM 16GB 권장).
  GeTrans로 번역한 결과물을 공개할 때는 출처 표기가 필요하며, 프로그램이 출처에 자동으로 넣어 줍니다.
  두 엔진의 번역을 함께 보관해 비교할 수 있어요 (번역 → 두 엔진으로 번역).

## 번역 엔진 ANIS Trans (별도 설치)

자동 번역에는 **ANIS Trans**를 씁니다. **이 배포 파일에는 들어 있지 않습니다**
(ANIS Trans 라이선스상 재배포가 금지되어 있습니다).

1. 공식 배포처에서 직접 받으세요: https://krmod.anis.co.kr/ai-lab?section=download
   (라이선스: 개인·비영리 무료, 영리 이용은 별도 상업 라이선스. 라이선스 동의는 직접 하세요.)
2. 받은 압축을 다운로드·문서·바탕화면 폴더 등에 풀면 프로그램이 자동으로 찾습니다.
3. 프로그램의 **설정 → 번역 엔진 → ANIS Trans 서버 관리…**에서 설치 폴더와 GPU/CPU를 확인합니다.

ANIS Trans가 없어도 **수동 번역 모드**로 검수·식자·출력을 모두 할 수 있습니다.

> AI 번역 엔진: ANIS Trans · 개발: jintigers · 출처: https://github.com/jintigers/anis-trans

## 함께 들어 있는 구성요소

| 구성요소 | 라이선스 |
|---|---|
| 일본어 OCR 모델 [kha-white/manga-ocr-base](https://huggingface.co/kha-white/manga-ocr-base) | Apache License 2.0 |
| 글자 찾기 모델 [ogkalu/comic-text-and-bubble-detector](https://huggingface.co/ogkalu/comic-text-and-bubble-detector) | Apache License 2.0 |
| 지운 자리 복원 모델 [JosephCatrambone/big-lama-torchscript](https://huggingface.co/JosephCatrambone/big-lama-torchscript) | Apache License 2.0 |
| 그림 위 글자 픽셀 찾기 모델 [TareHimself/comic-text-mask](https://huggingface.co/TareHimself/comic-text-mask) | MIT |
| 맞춤법 검사 띄어쓰기 [Kiwi (kiwipiepy)](https://github.com/bab2min/kiwipiepy) | Apache License 2.0 |
| Qt / PySide6 | LGPL v3 |
| PyTorch, NumPy | BSD |
| Transformers, OpenCV, manga-ocr | Apache License 2.0 |

각 라이선스 원문은 배포 폴더의 `licenses` 폴더와 `라이선스_및_출처.txt`에 있습니다.

## 무단 수정 및 재배포 금지

Copyright © 2026 changjun7539-maker. All rights reserved.

- 이 프로그램(Manga Trans Studio)과 배포 파일은 저작권자의 허락 없이 **수정, 역설계(디컴파일), 재배포, 판매,
  다른 사이트·저장소에 다시 올리기**를 할 수 없습니다.
- 다른 사람에게 알려 줄 때는 파일을 직접 전달하지 말고 **이 저장소의 Releases 링크**를 공유해 주세요.
  공식 배포처는 이 저장소뿐이며, 다른 곳에서 받은 파일은 변조되었을 수 있습니다.
- 개인적인 사용(번역 작업)은 자유롭게 할 수 있습니다. 프로그램으로 만든 번역 결과물의 이용은
  원작의 저작권과 각 플랫폼의 규칙을 지켜 주세요.
- 위 제한은 프로그램에 함께 들어 있는 제3자 구성요소(위 표)에는 적용되지 않습니다. 그 구성요소들은 각자의
  라이선스를 따르며, 이 안내가 그 라이선스가 주는 권리(예: LGPL에 따라 Qt 라이브러리를 바꿔 쓰는 것)를
  제한하지 않습니다.
- ANIS Trans는 이 배포에 포함되지 않으며, ANIS Trans의 이용은 ANIS Trans 라이선스를 따릅니다.

수정·재배포·협업 문의는 이 저장소의 **Issues**로 남겨 주세요.
