# Cursor IDE Configuration

Cursor IDE의 AI 기능을 최적화하기 위한 설정 파일들입니다.

## Files in this Directory

### 1. `.cursorrules`
Cursor의 AI에게 제공할 프로젝트별 규칙
- 프로젝트 컨텍스트와 코딩 스타일
- AI 동작 커스터마이징

### 2. `cursor-settings.json`
Cursor IDE 에디터 설정
- AI 기능 활성화/비활성화
- 단축키 및 동작 설정

### 3. `example-rules/`
다양한 프로젝트 타입별 예제 규칙
- Python/Django
- React/TypeScript
- Node.js/Express
- 기타 프레임워크

## Usage

### Setting up .cursorrules

1. 프로젝트 루트에 `.cursorrules` 파일을 생성하세요
2. 이 디렉토리의 예제를 참고하여 프로젝트 규칙을 작성하세요

```bash
cp .cursorrules /path/to/your/project/
```

### Configuring Cursor Settings

Cursor IDE의 설정은 Preferences에서 직접 수정하거나, 설정 JSON 파일을 편집할 수 있습니다.

## Features

Cursor IDE는 다음과 같은 AI 기능을 제공합니다:
- **Copilot++**: 향상된 코드 자동완성
- **Cursor Chat**: AI와 대화하며 코딩
- **Cmd+K**: 인라인 코드 편집 및 생성
- **@-mentions**: 파일, 폴더, 문서 참조
- **Composer**: 여러 파일을 동시에 편집

## Tips

- `.cursorrules` 파일은 프로젝트 루트에 배치하면 자동으로 인식됩니다
- 명확하고 구체적인 규칙을 제공할수록 더 나은 결과를 얻습니다
- 규칙 파일은 마크다운 형식으로 작성하며, 구조화된 형태로 작성하세요
- `@docs` 기능으로 공식 문서를 참조하여 최신 API를 사용할 수 있습니다
- 복잡한 작업은 Composer 모드를 사용하세요

## Example Workflow

1. **프로젝트 시작**: `.cursorrules`에 프로젝트 컨텍스트 작성
2. **코드 작성**: Copilot++로 빠른 자동완성
3. **리팩토링**: Cmd+K로 코드 개선
4. **다중 파일 작업**: Composer로 여러 파일 동시 편집
5. **디버깅**: Chat에서 @file로 특정 파일 참조하여 질문

## Resources

- [Cursor Documentation](https://cursor.sh/docs)
- [Cursor Community Forum](https://forum.cursor.sh/)
- [Cursor Discord](https://discord.gg/cursor)
