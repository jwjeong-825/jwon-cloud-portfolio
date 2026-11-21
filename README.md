# J.WON — Personal Cloud Portfolio

조선대학교 컴퓨터공학과 정주원의 개인 프로필과 클라우드·DevOps 학습 방향을 소개하는 정적 포트폴리오입니다. AI클라우드 컴퓨팅 수업의 기말 대체 과제로 제작했으며, 과제 제출 이후에도 개인 포트폴리오로 사용할 수 있도록 구성했습니다.

## 주요 기능

- 이름, 소속, 전공, 학력, 취미와 진로 목표를 담은 메인 프로필
- About Me, Tech Stack, Projects 등 8개 상세 화면
- 해시 기반 화면 전환과 브라우저 뒤로·앞으로 가기
- EC2, Security Group, Nginx, `index.html`의 요청 흐름을 설명하는 인터랙티브 아키텍처
- AWS EC2 정적 페이지 배포 절차 정리
- 미리 정의된 명령만 실행하는 JavaScript 기반 인터랙티브 터미널
- 이메일 주소 복사와 `mailto:` 연결
- 데스크톱, 태블릿, 모바일 반응형 레이아웃
- 키보드 포커스, Skip link, 모션 감소 설정 등 접근성 지원

## 디자인 개선

- 이름을 최우선으로 보여 주는 Hero와 클라우드 네트워크형 `JW` 시그니처 비주얼
- 프로필 핵심 정보와 상세 데이터를 분리한 에디토리얼 레이아웃
- 데스크톱에서는 가로, 모바일에서는 세로로 전환되는 학력 타임라인
- 두산 베어스, 맨체스터 유나이티드, 포켓몬 취향을 절제된 개인 아이덴티티로 표현
- 현재 경험과 앞으로의 학습 계획을 구분한 Career Vision
- 실제 저장소로 연결되는 Contact 링크: [jwon-cloud-portfolio](https://github.com/jwjeong-825/jwon-cloud-portfolio)

## 기술 구성

- HTML5
- CSS3
- Vanilla JavaScript
- 외부 프레임워크, API, 패키지 및 빌드 도구 없음

모든 스타일과 스크립트는 `index.html` 안에 포함되어 있습니다.

## 로컬 실행

별도 설치나 빌드가 필요하지 않습니다.

1. 저장소를 내려받습니다.
2. `index.html`을 웹브라우저에서 직접 엽니다.

또는 저장소 폴더에서 간단한 정적 서버를 실행할 수 있습니다.

```bash
python -m http.server 8000
```

이후 브라우저에서 `http://localhost:8000`에 접속합니다.

## AWS EC2 + Nginx 배포

아래 명령은 Ubuntu 계열 EC2를 기준으로 한 예시입니다. 실제 인스턴스의 운영체제와 계정에 맞게 조정해야 합니다.

### 1. EC2와 보안 그룹 준비

- Linux 기반 EC2 인스턴스를 생성합니다.
- SSH 접속용 TCP 22 규칙은 필요한 접속 범위로 제한합니다.
- 웹 접속을 위해 TCP 80 HTTP 인바운드 규칙을 허용합니다.

### 2. 서버 접속과 Nginx 설치

```bash
ssh -i /path/to/key.pem ubuntu@EC2_PUBLIC_IP
sudo apt update
sudo apt install -y nginx
sudo systemctl enable --now nginx
```

### 3. 파일 전송

로컬 컴퓨터에서 SFTP 또는 SCP를 이용해 파일을 전송합니다.

```bash
scp -i /path/to/key.pem index.html ubuntu@EC2_PUBLIC_IP:/tmp/index.html
```

인증 키(`*.pem`)는 저장소에 커밋하지 않습니다.

### 4. 웹 루트에 배치

```bash
sudo install -m 0644 /tmp/index.html /var/www/html/index.html
sudo nginx -t
sudo systemctl reload nginx
```

### 5. 배포 확인

브라우저에서 `http://EC2_PUBLIC_IP`에 접속해 다음을 확인합니다.

- 메인 프로필과 8개 상세 화면
- 브라우저 뒤로 가기
- 아키텍처 설명과 프로젝트 상세 보기
- 인터랙티브 터미널
- 이메일 복사
- 모바일 화면의 가로 넘침 여부

## 프로젝트 파일

```text
.
├── index.html       # 최종 홈페이지 — 단독 실행 가능
├── README.md        # 프로젝트 및 배포 안내
├── TEST_REPORT.md   # 실제 기능 검증 결과
└── .gitignore       # 임시 파일과 민감정보 제외 규칙
```

## 저장소 및 확인되지 않은 정보

- GitHub 저장소: <https://github.com/jwjeong-825/jwon-cloud-portfolio>
- 실제 EC2 공개 주소, 배포 완료 상태, 파일 전송 방식 및 개별 프로젝트 GitHub URL은 검증된 값이 제공되기 전까지 홈페이지에서 임의로 표시하지 않습니다.
