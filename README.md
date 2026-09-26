# EUKK Trading 1.0.0

한국·미국 시장의 데이터 준비, 종목 선별, 백테스트와 자동매매를 한곳에서 관리하는 로컬 데스크톱 프로그램입니다. Python과 PySide6로 만들었으며 별도 서버나 Python 설치 없이 실행할 수 있습니다.

**[1.0.0 다운로드 및 변경 사항](https://github.com/OverDlive/AutoTrading_Local-releases/releases/tag/v1.0.0)** · **[최신 버전](https://github.com/OverDlive/AutoTrading_Local-releases/releases/latest)**

## 다운로드

| 운영체제 | 배포 파일 |
| --- | --- |
| Windows x64 | [EUKK-Trading-1.0.0-windows-x64.zip](https://github.com/OverDlive/AutoTrading_Local-releases/releases/download/v1.0.0/EUKK-Trading-1.0.0-windows-x64.zip) |
| macOS Apple Silicon (M 시리즈) | [EUKK-Trading-1.0.0-macos-arm64.tar.gz](https://github.com/OverDlive/AutoTrading_Local-releases/releases/download/v1.0.0/EUKK-Trading-1.0.0-macos-arm64.tar.gz) |
| macOS Intel | [EUKK-Trading-1.0.0-macos-x64.tar.gz](https://github.com/OverDlive/AutoTrading_Local-releases/releases/download/v1.0.0/EUKK-Trading-1.0.0-macos-x64.tar.gz) |

각 파일에 대응하는 `.sha256` 파일도 릴리스에 제공합니다. GitHub의 **Source code** 파일은 실행 프로그램이 아니므로 위의 운영체제별 파일을 받으세요. Linux 배포 파일은 제공하지 않습니다.

## 주요 기능

| 화면 | 할 수 있는 일 |
| --- | --- |
| Overview | 계좌와 시장별 운영 상태 확인 |
| Account & Data | 한국투자증권·토스증권 연결 설정, KRX 데이터 계정 관리, 종목과 일봉 데이터 준비 |
| Screening | 시장과 기준일에 따른 종목 선별, 선정 사유 확인, 백테스트 연계 |
| Backtest Lab | 선택 종목·자동 구성 포트폴리오 백테스트, 비용·슬리피지 반영, 거래 내역과 수익곡선 분석, 결과 저장 |
| Live Trading | KR/US 세션 관리, 로컬 모의매매 및 지원 증권사 실계좌 연동, 자금 배정과 주문·체결 확인, 대사·복구, 전체 중지 |
| Preferences | 테마와 백그라운드 실행 설정, 백업·복원, 새 버전 확인과 설치 |

- 일목균형표 원전 통합 전략과 기존 전략을 공통 계산 구조로 사용합니다. 전략·시장·자금 배분 정책에 따라 실행 가능한 모드가 다르며, 지원하지 않는 조합은 앱에서 제한합니다.
- 한국·미국의 거래일과 시간대, 세션 상태를 분리합니다.
- SQLite와 Parquet에 설정·실행 결과·시장 데이터를 로컬로 보관합니다.
- 자격증명은 OS 보안 저장소와 암호화 저장소로 보호하며 로그의 민감정보를 가립니다.
- 모든 배포판은 CPU로 실행됩니다. Windows와 Apple Silicon Mac은 Numba 수치 계산 가속을 포함하며 Intel Mac은 기본 Python 계산 경로를 사용합니다. 실험적인 NVIDIA CUDA 가속 패키지는 포함하지 않습니다.

## 설치

### Windows

1. Windows x64 압축 파일을 내려받아 **전체 압축 해제**합니다.
2. 예를 들어 `%LOCALAPPDATA%\Programs\EUKK Trading` 같은 전용 설치 폴더에 둡니다.
3. 폴더 안의 `EUKK Trading.exe`를 실행합니다. `_internal` 폴더도 함께 유지해야 합니다.

### macOS

1. Mac의 칩에 맞는 압축 파일을 내려받아 압축을 풉니다.
2. `EUKK Trading.app`을 응용 프로그램 폴더로 옮깁니다. 자동 업데이트를 사용하려면 설치 폴더의 부모 디렉터리에 쓰기 권한이 있어야 합니다.
3. 앱을 실행합니다.

배포 파일에는 Windows 코드 서명과 Apple 개발자 서명·공증이 포함되지 않습니다. 운영체제가 실행을 제한하면 다운로드 출처를 확인한 뒤 해당 운영체제의 보안 설정 안내를 따르세요.

## 처음 시작하기

1. **Account & Data**에서 필요한 데이터 계정과 증권사 연결을 설정합니다. 다운로드·업데이트에는 GitHub 계정이나 접근 토큰이 필요하지 않습니다.
2. 사용할 시장의 종목과 가격 데이터를 준비하고 조회 기간과 데이터 상태를 확인합니다.
3. **Screening / Backtest Lab**에서 전략, 기간, 종목 범위와 비용 조건을 정해 결과를 확인합니다. 데이터 부족으로 제외된 종목과 사유도 함께 확인하세요.
4. **Live Trading**에서 시장, 계좌, 전략과 자금 배정을 확인하고 먼저 로컬 모의 세션으로 점검합니다.
5. 실계좌 실행 시에는 앱의 위험 확인과 계좌 대사 절차를 완료합니다. 복구가 필요한 세션은 안내된 확인 절차를 마친 뒤 재개합니다.

백테스트 결과는 실제 수익이나 실제 주문 체결을 보장하지 않습니다. 배포 검증은 계좌에 접속하거나 실제 주문을 전송하지 않습니다.

## 업데이트

**환경 설정 → 일반 → 자동 업데이트 확인**을 켜면 시작 시와 6시간마다 새 버전을 확인합니다. **환경 설정 → 업데이트**에서 확인·다운로드·설치를 진행합니다.

다운로드한 파일의 크기와 SHA-256, 버전 및 운영체제 정보를 검증합니다. 설치 전에는 진행 중인 거래 세션을 종료하고 필요한 데이터를 백업하세요. 업데이트 후 앱을 다시 시작합니다. 설치 위치에 쓰기 권한이 없으면 권한이 있는 전용 폴더로 앱을 옮겨야 합니다.

GitHub 접근 토큰 입력 창은 없으며, 공개 릴리스에서 업데이트를 받습니다.

## 사용자 데이터와 백업

| 운영체제 | 기본 데이터 위치 |
| --- | --- |
| Windows | `%LOCALAPPDATA%\EUKK Trading` |
| macOS | `~/Library/Application Support/EUKK Trading` |

설치 폴더와 데이터 폴더를 분리하세요. **환경 설정 → 백업·복원**에서 `.eukkbackup` 백업을 생성하고 복원할 수 있습니다. OS 보안 저장소에 의존하는 자격증명은 다른 컴퓨터로 옮긴 뒤 다시 설정해야 할 수 있습니다.

## 이 저장소의 역할

이 저장소는 공개 배포용 미러입니다. 원본 개발 저장소에서 GitHub Actions로 빌드·검증한 실행 파일과 체크섬, 사용 안내를 게시합니다. 원본 Git 이력, 개발 자료, 사용자 데이터와 계좌 자격증명은 미러링하지 않습니다.

문제를 제보할 때는 앱 버전, 운영체제·칩, 재현 순서와 오류 내용을 알려주세요. 계좌번호, 접근 토큰, API 키 및 개인 데이터가 포함된 원본 로그는 공개 게시하지 마세요.
