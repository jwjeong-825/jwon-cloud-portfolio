# J.WON Portfolio 테스트 보고서

테스트 일자: 2026-11-21
대상 파일: `index.html`

## 결과 요약

| 항목 | 결과 | 확인 내용 |
|---|---|---|
| 단일 파일 실행 | PASS | Microsoft Edge에서 `file://` 경로로 직접 실행 |
| JavaScript 문법 | PASS | Node.js `new Function()` 구문 검사 통과 |
| 메인 화면 | PASS | 이름, 소속, 진로, 프로필, 학력, 취미, Career Vision 표시 확인 |
| 상세 화면 전환 | PASS | `#page/terminal` 상세 화면 렌더링 확인 |
| 브라우저 뒤로 가기 | PASS | 상세 화면에서 메인 화면으로 정상 복귀 |
| 인터랙티브 터미널 | PASS | `skills` 입력 후 학습 기술과 향후 계획 출력 확인 |
| 반응형 레이아웃 | PASS | 좁은 창에서 모바일 메뉴와 1열 Hero, 넓은 창에서 2열 Hero 확인 |
| 키보드/접근성 구조 | PASS | Skip link, 명시적 label, ARIA 상태, 포커스 스타일 확인 |
| 필수 콘텐츠 | PASS | 이름, 학교, 학력, 프로젝트 4개, 이메일, 인프라 구성 포함 확인 |
| 외부 의존성 | PASS | 외부 CSS, JavaScript, 이미지, API 요청 없음 |
| 미확인 정보 처리 | PASS | GitHub URL, 실제 배포 상태, 전송 방식은 확인 전으로 표기 |

## 구현된 기능

- 메인 프로필과 8개 상세 콘텐츠 사이의 해시 기반 화면 전환
- History API에 의존하지 않는 브라우저 뒤로/앞으로 가기
- 이메일 `mailto:` 링크 및 클립보드 복사
- 정의된 명령만 처리하는 JavaScript 터미널
- 클릭 가능한 클라우드 아키텍처 설명
- 확장형 프로젝트 상세 정보
- 모바일 메뉴와 화면 폭별 반응형 레이아웃
- `prefers-reduced-motion` 지원

## 배포 전 확인 필요

- 실제 GitHub 계정과 공개 저장소 URL
- EC2 배포 완료 여부와 공개 주소
- 실제 파일 전송 방식(FTP 또는 SFTP)
- Nginx 웹 루트의 실제 배포 경로

위 정보는 제공되지 않았으므로 임의로 작성하지 않았습니다. 실제 배포 후 `index.html`의 "배포 확인 전" 문구를 검증된 정보로 변경하면 됩니다.
