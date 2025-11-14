# GitHub Copilot Configuration

GitHub Copilot을 더욱 효과적으로 사용하기 위한 설정 파일들입니다.

## Files in this Directory

### 1. `.github/copilot-instructions.md`
GitHub Copilot에게 제공할 프로젝트 지침
- 워크스페이스 레벨에서 적용되는 커스텀 지침
- 프로젝트의 코딩 스타일과 규칙

### 2. `copilot-agent-config.yml`
Copilot Agent 설정 (GitHub Copilot Workspace 및 CLI)
- 커스텀 에이전트 동작 설정
- 자동화된 워크플로우 정의

### 3. `vscode-settings.json`
VS Code에서 GitHub Copilot 최적화 설정
- Copilot 관련 에디터 설정
- 언어별 Copilot 동작 커스터마이징

## Usage

### Setting up Copilot Instructions

1. 프로젝트 루트에 `.github` 디렉토리를 생성하세요
2. `.github/copilot-instructions.md` 파일을 생성하세요
3. 이 디렉토리의 예제를 참고하여 프로젝트 지침을 작성하세요

```bash
mkdir -p .github
cp copilot-instructions.md .github/
```

### Configuring VS Code

1. VS Code 설정 파일(`.vscode/settings.json`)을 열거나 생성하세요
2. 이 디렉토리의 `vscode-settings.json` 내용을 추가하세요
3. 필요에 따라 설정을 커스터마이징하세요

## Tips

- Copilot Instructions는 프로젝트 루트의 `.github/copilot-instructions.md`에 배치하면 자동으로 인식됩니다
- 명확하고 구체적인 지침을 제공할수록 더 나은 코드 제안을 받을 수 있습니다
- 여러 프로젝트에서 공통으로 사용하는 규칙은 글로벌 설정으로 관리하세요
- Copilot Chat에서 `@workspace` 명령을 사용하면 프로젝트 컨텍스트를 활용할 수 있습니다

## Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Copilot Instructions Guide](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)
- [VS Code Copilot Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
