# Pintos (KAIST) — OS Kernel Extensions

KRAFTON Jungle 팀 프로젝트로 진행한 **Pintos 커널 확장 구현**입니다.  
스레드 스케줄링, 사용자 프로세스/시스템 콜, 가상 메모리(프로젝트 1~3) 중심으로 구현했습니다.

## 핵심 구현

### Threads & Scheduler
- 알람 기반 sleep 큐와 타이머 인터럽트 기반 wake-up
- 우선순위 스케줄링 + 우선순위 기부(priority donation)
- MLFQS(Load Avg / Recent CPU / Nice) 지원

### User Programs
- 시스템 콜 핸들러와 사용자 포인터/버퍼 검증
- `exec/fork/wait/exit` 프로세스 생명주기 구현
- 인자 파싱 및 유저 스택 빌드
- 파일 디스크립터 테이블 관리 + `dup2` 지원

### Virtual Memory
- Supplemental Page Table (hash 기반)
- ELF 세그먼트 lazy loading
- 스택 자동 확장
- `mmap/munmap` 및 write-back 처리

## 디렉터리 구조
- `pintos/threads`: 스케줄러, 동기화, 타이머
- `pintos/userprog`: 시스템 콜, 프로세스 관리, 유저 스택
- `pintos/vm`: 가상 메모리, SPT, mmap
- `pintos/filesys`: 파일 시스템 스켈레톤

## 참고
- 기본 코드베이스는 KAIST CS330 Pintos를 사용했습니다.
- 상세 매뉴얼: https://casys-kaist.github.io/pintos-kaist/
