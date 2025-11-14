# Claude Code Configuration

Claude AI를 코딩 도우미로 활용하기 위한 설정 파일들입니다.

## Files in this Directory

### 1. `system_prompts.md`
Claude에게 제공할 시스템 프롬프트 예제들
- 코드 리뷰 전문가
- 디버깅 도우미
- 문서화 전문가

### 2. `custom_instructions.md`
프로젝트별 맞춤 지침
- 코딩 스타일 가이드
- 프로젝트 컨텍스트
- 특정 프레임워크 지침

### 3. `mcp_config.json`
MCP 서버 연동 설정
- Claude Desktop과 MCP 서버 연결 설정

## Usage

1. Claude Desktop이나 Claude API를 사용할 때 이 설정들을 참고하세요
2. `system_prompts.md`에서 필요한 프롬프트를 선택하여 사용하세요
3. `custom_instructions.md`를 프로젝트에 맞게 커스터마이징하세요

## Tips

- 명확하고 구체적인 지침을 제공할수록 더 좋은 결과를 얻을 수 있습니다
- 프로젝트의 코딩 스타일과 아키텍처를 설명하면 일관성 있는 코드를 생성합니다
- MCP를 통해 파일 시스템, Git, 데이터베이스 등에 접근할 수 있습니다
