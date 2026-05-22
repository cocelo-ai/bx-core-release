# [Bonsystems](https://bonsystems.com/media-center/press-release/bonsystems-robot-hand-micro-actuators/) B16 Core

---

## 1. 로봇 움직여보기

전원 버튼을 켠 뒤 **두 번째 부저음**이 들릴 때까지 기다립니다. 두 번째 부저음은 부팅이 완료되어 조작 가능한 상태임을 알리는 신호입니다. 부팅 완료 후 조이스틱의 `LT`를 길게 눌러 로봇을 일으켜 봅니다.

#### 조이스틱 조작표

| 입력 | 동작 |
| --- | --- |
| `LT` 길게 누르기 | 일어서기 (Stand up) |
| `RT` 길게 누르기 | 앉기 (Sit down) |
| 왼쪽 조이스틱 | 전진 / 후진 및 좌우 회전 |
| 오른쪽 조이스틱 | 횡이동 |
| `LT` + `RT` 동시에 한 번 | 현재 위치에서 모터 고정 (비상 정지) |
| `LT` + `RT` 동시에 다시 한 번 | 전체 모터 종료 |

---

## 2. SSH 접속

전원을 켜면 Wi-Fi 핫스팟이 자동으로 활성화됩니다. `XXXX`는 각 로봇마다 고유한 4자리 영문/숫자 태그입니다.

```bash
# 1단계: Wi-Fi 연결
#   COCELO_ROBOT_XXXX 네트워크에 연결합니다.

# 2단계: SSH 접속
ssh cocelo@XXXX    # XXXX = Wi-Fi SSID와 동일한 태그
                   # 비밀번호: 1
```

---

## 3. 펌웨어 업그레이드

#### 1 — 다운로드

```bash
rm -rf bx-core-release
git clone -b b16-core_0.1.0-1_arm64 --single-branch https://github.com/cocelo-ai/fx-core-release.git
```

#### 2 — 설치

```bash
sudo apt install ./bx-core-release/b16-core_0.1.0-1_arm64.deb
```

---

## 4. 로그 저장 디렉토리

기본 로그 저장 경로는 아래와 같습니다.

```
cd ~/.local/b16/log
```

---

## 5. 설정 파일 및 정책 파일 위치

| 항목 | 경로 |
| --- | --- |
| ONNX 정책 파일 | `/usr/share/b16-core/onnx/*.onnx` |
| YAML 설정 파일 | `/etc/b16-core/*.yaml` |
| YAML 공장 초기값 | `/usr/share/b16-core/defaults/*.yaml` |

> 설정 변경 후에는 반드시 서비스를 재시작해주세요.
