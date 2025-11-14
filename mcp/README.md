# Model Context Protocol (MCP) Configuration

MCP 서버 및 클라이언트 설정 파일들입니다.

## What is MCP?

Model Context Protocol (MCP)는 AI 애플리케이션과 외부 데이터 소스 및 도구를 연결하는 오픈 프로토콜입니다. MCP를 통해 AI는 파일 시스템, 데이터베이스, API 등에 안전하게 접근할 수 있습니다.

## Files in this Directory

### 1. `claude-desktop-config.json`
Claude Desktop 앱의 MCP 서버 설정
- 로컬 MCP 서버 연결 설정
- 환경 변수 및 인증 정보

### 2. `mcp-servers/`
다양한 MCP 서버 설정 예제
- Filesystem server
- GitHub server
- Database servers
- Custom servers

### 3. `custom-server-example/`
커스텀 MCP 서버 구현 예제
- Python으로 작성된 예제 서버
- TypeScript로 작성된 예제 서버

## Available MCP Servers

### Official Servers (by Anthropic)
- **filesystem**: 로컬 파일 시스템 접근
- **github**: GitHub 리포지토리 관리
- **git**: Git 저장소 작업
- **postgres**: PostgreSQL 데이터베이스
- **sqlite**: SQLite 데이터베이스
- **puppeteer**: 브라우저 자동화
- **brave-search**: 웹 검색
- **memory**: 대화 간 정보 저장

### Community Servers
- **slack**: Slack 통합
- **google-drive**: Google Drive 접근
- **aws**: AWS 서비스 관리
- **docker**: Docker 컨테이너 관리

## Setup Instructions

### 1. Claude Desktop 설정

#### macOS
```bash
# 설정 파일 위치
~/Library/Application Support/Claude/claude_desktop_config.json
```

#### Windows
```bash
# 설정 파일 위치
%APPDATA%\Claude\claude_desktop_config.json
```

#### Linux
```bash
# 설정 파일 위치
~/.config/Claude/claude_desktop_config.json
```

### 2. MCP 서버 설치

```bash
# Filesystem server
npm install -g @modelcontextprotocol/server-filesystem

# GitHub server
npm install -g @modelcontextprotocol/server-github

# Database servers
npm install -g @modelcontextprotocol/server-postgres
npm install -g @modelcontextprotocol/server-sqlite
```

### 3. 설정 파일 구성

`claude-desktop-config.json`을 편집하여 필요한 서버를 추가하세요:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/workspace"]
    }
  }
}
```

## Usage Examples

### Filesystem Access
```
# Claude에게 요청
"프로젝트의 src 디렉토리에 있는 모든 Python 파일을 나열해줘"
"README.md 파일의 내용을 읽고 요약해줘"
```

### GitHub Integration
```
# Claude에게 요청
"이 리포지토리의 최근 10개 이슈를 보여줘"
"main 브랜치에 새로운 PR을 생성해줘"
```

### Database Access
```
# Claude에게 요청
"users 테이블의 스키마를 보여줘"
"활성 사용자 수를 조회해줘"
```

## Security Considerations

### Best Practices
1. **최소 권한 원칙**: 필요한 최소한의 접근 권한만 부여
2. **경로 제한**: 파일 시스템 접근 시 특정 디렉토리로 제한
3. **환경 변수 사용**: API 키나 비밀번호는 환경 변수로 관리
4. **읽기 전용 모드**: 가능하면 읽기 전용으로 설정
5. **로그 모니터링**: MCP 서버 활동을 정기적으로 확인

### Sensitive Data
- API 키, 토큰, 비밀번호는 설정 파일에 직접 작성하지 마세요
- 환경 변수나 시크릿 관리 도구를 사용하세요
- 설정 파일을 Git에 커밋할 때 주의하세요

## Troubleshooting

### Common Issues

#### 서버가 시작되지 않음
- Node.js가 설치되어 있는지 확인
- npm 패키지가 최신 버전인지 확인
- 설정 파일의 경로가 올바른지 확인

#### 권한 오류
- 파일 시스템 접근 권한 확인
- 환경 변수가 올바르게 설정되었는지 확인
- API 토큰이 유효한지 확인

#### 연결 실패
- Claude Desktop을 재시작
- 설정 파일 JSON 문법 확인
- 로그 파일 확인

### Debug Mode

로그를 확인하려면:
```bash
# macOS/Linux
tail -f ~/Library/Logs/Claude/mcp*.log

# Windows
# Claude Desktop의 Developer Tools에서 확인
```

## Custom MCP Server Development

### Python Example
```python
from mcp.server import Server
from mcp.types import Tool, TextContent

server = Server("my-custom-server")

@server.tool()
async def my_custom_tool(argument: str) -> str:
    """Custom tool implementation."""
    return f"Processed: {argument}"

if __name__ == "__main__":
    server.run()
```

### TypeScript Example
```typescript
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server({
  name: "my-custom-server",
  version: "1.0.0",
});

server.setRequestHandler("tools/list", async () => ({
  tools: [
    {
      name: "my_custom_tool",
      description: "Custom tool implementation",
      inputSchema: {
        type: "object",
        properties: {
          argument: { type: "string" }
        }
      }
    }
  ]
}));

const transport = new StdioServerTransport();
await server.connect(transport);
```

## Resources

- [MCP Specification](https://modelcontextprotocol.io/)
- [MCP GitHub Repository](https://github.com/modelcontextprotocol)
- [Claude Desktop Documentation](https://docs.anthropic.com/claude/docs)
- [MCP Server List](https://github.com/modelcontextprotocol/servers)
