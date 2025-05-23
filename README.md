# saedori-api-server

### 실행 방법
```bash
// install golang (v.1.24.2)
cd cmd
go run .
```

### 폴더 구조
```
saedori-api-server/
├── cmd/                 # 애플리케이션 entrypoint (main.go)
│   └── main.go
├── internal/            # 핵심 애플리케이션 코드 (외부에서 import 불가)
│   ├── config/          # 설정 (환경변수, DB 설정 등)
│   ├── handler/         # HTTP 핸들러 (controller 역할)
│   ├── service/         # 비즈니스 로직 (usecase)
│   ├── repository/      # DB, 외부 API 접근
│   ├── model/           # 구조체 정의 (DTO, Entity)
│   ├── router/          # Gin 라우터 정의
│   └── middleware/      # 공통 미들웨어
├── pkg/                 # 공통 유틸/라이브러리 (다른 프로젝트에서 재사용 가능)
├── go.mod
└── go.sum

```

### 구조 설명
- `cmd`: 애플리케이션의 진입점이 되는 파일들로 구성합니다.
- `internal`: 캡슐화를 보장하여, 외부에서 접근할 수 없습니다. 즉 같은 모듈 내에서만 import할 수 있습니다. 프로젝트의 핵심 비즈니스 로직 등을 작성하기 좋습니다.
- `pkg`: 외부에서 재사용 가능한 코드들로 구성합니다.
- `main.go`: 실행 진입점이며, `cmd.go`에 실행 로직을 위임하였습니다.
