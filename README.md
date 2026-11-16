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

오른쪽(또는 위쪽)의 **[Releases](../../releases)**에서 최신 버전의
`MangaTransStudio-<버전>-win64.zip`을 받으세요.

## 설치와 실행

1. ZIP을 원하는 폴더에 풉니다 (약 1.9GB 공간 필요).
2. `MangaTransStudio\MangaTransStudio.exe`를 실행합니다.
   폴더 안의 다른 파일도 함께 있어야 하니 EXE만 따로 옮기지 마세요.
3. 처음 실행할 때 Windows 보안 경고(SmartScreen)가 뜨면 **추가 정보 → 실행**을 누르세요
   (코드 서명이 없어서 뜨는 경고입니다).
4. 처음 켜면 체험형 튜토리얼을 안내합니다. 사용 설명서는 프로그램의 **도움말 → 사용 설명서(F1)**에 있습니다.

**권장 환경**: Windows 10/11 64비트, 메모리 8GB 이상. AI 기능(OCR·글자 찾기·복원)은 CPU로 동작하며
인터넷 연결 없이 쓸 수 있습니다(모델 포함).

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
