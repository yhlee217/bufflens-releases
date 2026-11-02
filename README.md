# BuffLens 설치 파일

마비노기 전투 보조 오버레이 **BuffLens**의 설치 파일을 두는 곳입니다. 소스 코드는 비공개이고, 여기에는 **설치 파일과 portable 실행 파일만** 올라옵니다.
넥슨의 공식 프로그램이 아닌 개인 도구입니다.

## 받기

[최신 판 받는 곳](https://github.com/yhlee217/bufflens-releases/releases/latest)에서 `BuffLens-Setup-<판>.exe`를 받습니다.
`BuffLens-<판>-portable.exe`는 설치 없이 아무 폴더에서 바로 실행하는 판입니다.

## 설치

1. `BuffLens-Setup-<판>.exe`를 실행합니다.
2. 처음 실행하면 Windows가 **"PC 보호"(SmartScreen)** 경고를 띄울 수 있습니다 — 설치 파일에 서명 인증서가 없기 때문입니다. **[추가 정보]**를 누른 뒤 **[실행]**을 누릅니다.
3. **설치 옵션 선택**에서 **'나만 사용 - 현재 Windows 계정'** 또는 **'이 컴퓨터를 사용하는 모든 사람(모든 사용자)'**을 고릅니다
   (0.1.85까지의 설치 파일은 앞의 것이 **'전용'**으로만 보입니다). '나만 사용'이면 새 판을 관리자 확인 없이 앱 안에서 설치하도록 되어 있고,
   모든 사용자용은 새 판마다 관리자 권한 확인과 설치 마법사를 거칩니다(아래 '새 판은 앱이 알려 줍니다').
4. 설치 폴더를 고르고, **추가 작업**에서 **'바탕 화면에 바로 가기 만들기'**와 **'Windows를 켤 때 BuffLens 실행 (트레이에만 — 창은 트레이 아이콘을 눌러 연다)'**을 고릅니다.

제거는 Windows [설정] → 앱에서 합니다. 제거해도 설정이 든 데이터 폴더(`%APPDATA%\BuffLens`)는 남습니다.

## 새 판은 앱이 알려 줍니다

설치판 BuffLens는 켠 뒤 5초, 그 뒤 6시간마다 이 저장소에서 새 판이 있는지 확인합니다. 새 판이 있으면 앱의 **홈 화면에 한 줄**이 뜨고,
켠 직후의 확인이 새 판을 찾았으면 앱 창 안에서 "지금 업데이트할까요?"를 한 번 묻습니다([나중에]를 누르면 그 실행에서는 다시 묻지 않습니다) —
게임 위에 팝업이 뜨거나 소리가 나지 않고, 받기와 설치는 **[업데이트]를 누를 때만** 합니다.
받은 뒤의 설치는 설치 방식에 따라 다릅니다.

- **모든 사용자용 설치**('이 컴퓨터를 사용하는 모든 사람'): [설치 마법사 열기]를 누르면 설치 프로그램을 띄운 뒤 앱이 꺼지고, 설치 프로그램이 관리자 권한을 묻습니다. 마법사가 끝나면 앱이 다시 뜹니다.
  이 길(홈 화면의 [업데이트] → [설치 마법사 열기])은 실제 업데이트로 확인했습니다 — 설정 · 바탕 화면 바로 가기 · Windows를 켤 때 실행이 그대로 남았습니다.
- **나만 사용 설치**('나만 사용 - 현재 Windows 계정'): 묻는 창의 [업데이트]는 받고 나서, BuffLens 창을 보고 있고 게임이 앞에 없을 때만 곧 설치 프로그램을 띄우고 설치가 끝나면 앱을 다시 띄웁니다.
  그 밖에는 앱을 끄지 않고 다시 묻습니다. 홈 화면의 [업데이트]로 받았다면 [지금 다시 시작]을 누르거나, 그냥 두면 앱을 끌 때 조용히 설치합니다.
  이 길은 그렇게 하도록 만들어져 있지만 실제 업데이트로는 아직 확인하지 않았습니다.

확인을 끄려면 [설정] → 일반의 '새 판 자동 확인'을 끕니다. portable은 앱이 받지 않고 이 페이지를 엽니다.

## 확인한 파일만 설치합니다

새 판의 정보(`bufflens-update.json`)에는 개발자의 서명(Ed25519)이 들어 있고, 앱은 앱 안에 넣어 둔 공개 키로 그 서명을 **먼저** 확인합니다.
받은 설치 파일은 정보에 적힌 크기와 SHA-256이 같을 때만 설치합니다. 서명이 맞지 않으면 받지 않고, 받은 파일이 정보와 다르면 버립니다 — 그래서 이 저장소의 파일이 바뀌어도 서명이 맞지 않으면 설치되지 않습니다.
앱은 이 저장소에서 파일을 읽기만 하고(GET), https로 GitHub 주소(github.com · githubusercontent.com)로만 갑니다.

## 이 앱이 하는 것

게임 화면을 **읽기만** 합니다 — 게임 메모리를 읽거나, 게임에 키 · 마우스 입력을 보내거나, 패킷을 보지 않습니다.

## 라이선스

BuffLens의 소스 코드는 공개하지 않습니다. 설치 파일에는 아래 오픈 소스 구성 요소와 그 라이선스 원문이 함께 들어 있습니다.
경로는 설치 폴더 기준입니다(portable은 실행할 때 푸는 폴더).

**알림 목소리 모델에는 사용 제한이 있습니다.** 목소리 모델 Supertonic 3(Supertone)은 **OpenRAIL-M** 라이선스를 따릅니다.
라이선스 끝의 Attachment A(Use Restrictions)는 이 모델을 법을 어기는 일, 미성년자를 해치는 일, 남을 해치려고 거짓 정보를 만들거나 퍼뜨리는 일,
남을 동의 없이 사칭하는 일, 괴롭히거나 차별하는 일, 기계가 만든 것임을 밝히지 않고 퍼뜨리는 일 등에 쓰지 못하게 합니다.
이 제한은 BuffLens로 알림 목소리를 쓸 때도, BuffLens를 다른 사람에게 다시 나눠 줄 때도 그대로 따라갑니다 — 원문은 `resources/licenses/Supertonic-3-OpenRAIL-M.txt`.

| 구성 요소 | 라이선스 | 원문 |
|---|---|---|
| 알림 목소리 모델 Supertonic 3 — sherpa-onnx용 int8 판([csukuangfj2/sherpa-onnx-supertonic-3-tts-int8-2026-05-11](https://huggingface.co/csukuangfj2/sherpa-onnx-supertonic-3-tts-int8-2026-05-11)) | OpenRAIL-M (Supertonic 코드는 MIT) | `resources/licenses/Supertonic-3-OpenRAIL-M.txt` · `Supertonic-MIT.txt` |
| 목소리 엔진 sherpa-onnx 1.13.8 | Apache License 2.0 | `resources/licenses/sherpa-onnx-Apache-2.0.txt` |
| sherpa-onnx DLL 안에 함께 든 espeak-ng 등 | espeak-ng은 GPL-3.0 이상 (BuffLens는 espeak-ng을 부르지 않습니다) | `resources/licenses/sherpa-onnx-THIRD-PARTY.txt`(그 판의 소스 위치) · `GPL-3.0.txt` |
| ONNX Runtime | MIT | `resources/licenses/onnxruntime-MIT.txt` |
| 글자 인식 tesseract.js · tesseract.js-core | Apache License 2.0 | `resources/app/node_modules/tesseract.js/LICENSE.md` · `resources/app/node_modules/tesseract.js-core/LICENSE` |
| 글자 인식 언어 자료 kor · eng (npm `@tesseract.js-data`) | MIT (패키지 표기) | 패키지에 원문 파일이 없습니다 |
| 화면 라이브러리 React · React DOM | MIT | 앱 코드(`resources/app/out/renderer/assets/`) 안의 `@license React` 머리글 |
| 글꼴 Pretendard | SIL Open Font License 1.1 | `resources/licenses/Pretendard-OFL.txt` |
| 아이콘 Tabler Icons | MIT | `resources/licenses/Tabler-Icons-MIT.txt` |
| Electron · Chromium | MIT · Chromium 구성 요소마다의 라이선스 | 설치 폴더 맨 위의 `LICENSE.electron.txt` · `LICENSES.chromium.html` |
