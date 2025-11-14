# Aider AI Configuration

Aider는 터미널에서 사용하는 AI 페어 프로그래밍 도구입니다.

## What is Aider?

Aider는 커맨드라인에서 AI와 함께 코딩할 수 있는 도구입니다. Git과 통합되어 변경사항을 자동으로 커밋하고, 여러 파일을 동시에 편집할 수 있습니다.

## Files in this Directory

### 1. `.aider.conf.yml`
Aider 설정 파일
- 기본 모델 설정
- Git 자동 커밋 옵션
- 편집기 설정

### 2. `.aider.model.settings.yml`
모델별 상세 설정
- 다양한 AI 모델 설정
- 비용 및 성능 최적화

### 3. `aider-commands.md`
자주 사용하는 Aider 명령어 모음

## Installation

```bash
# pip로 설치
pip install aider-chat

# pipx로 설치 (권장)
pipx install aider-chat

# 또는 homebrew (macOS)
brew install aider
```

## Basic Usage

### 시작하기
```bash
# 기본 실행
aider

# 특정 파일과 함께 시작
aider src/main.py tests/test_main.py

# 특정 모델 사용
aider --model gpt-4

# Claude 사용
aider --model claude-3-opus-20240229
```

### 주요 명령어

#### 파일 관리
```bash
/add filename.py          # 파일 추가
/drop filename.py         # 파일 제거
/ls                       # 추가된 파일 목록
/clear                    # 모든 파일 제거
```

#### Git 작업
```bash
/commit                   # 변경사항 커밋
/diff                     # Git diff 보기
/undo                     # 마지막 변경사항 되돌리기
```

#### 기타
```bash
/help                     # 도움말
/exit                     # 종료
/tokens                   # 토큰 사용량 확인
/model                    # 모델 변경
```

## Configuration

### .aider.conf.yml 위치
- 프로젝트 루트: `./.aider.conf.yml`
- 홈 디렉토리: `~/.aider.conf.yml`

### 환경 변수

```bash
# OpenAI API Key
export OPENAI_API_KEY=your-api-key

# Anthropic API Key
export ANTHROPIC_API_KEY=your-api-key

# Git 자동 커밋 비활성화
export AIDER_AUTO_COMMITS=false
```

## Best Practices

### 1. 작업 시작 전
```bash
# 현재 브랜치 확인
git status

# Aider로 작업할 파일들 추가
aider src/module.py tests/test_module.py
```

### 2. 명확한 지시
- 구체적으로 무엇을 원하는지 설명
- 예제 코드나 예상 결과 제공
- 단계별로 진행

### 3. 검토 및 테스트
- Aider가 만든 변경사항 검토
- 테스트 실행 확인
- 필요시 `/undo`로 되돌리기

### 4. 효율적인 작업
- 관련 파일만 추가 (불필요한 파일은 제거)
- 큰 작업은 작은 단위로 나누기
- Git 커밋은 의미 있는 단위로

## Tips

### 모델 선택
- **GPT-4**: 가장 강력하지만 비용이 높음
- **GPT-3.5-Turbo**: 빠르고 저렴, 간단한 작업에 적합
- **Claude**: 긴 컨텍스트와 코드 이해에 강함

### 비용 절감
```yaml
# .aider.conf.yml
model: gpt-3.5-turbo        # 저렴한 모델 사용
auto-commits: false         # 수동 커밋으로 변경사항 제어
edit-format: whole          # diff 대신 전체 파일 (간단한 경우)
```

### 프로젝트별 설정
```yaml
# Python 프로젝트
model: gpt-4
auto-commits: true
lint-cmd: "black ."
test-cmd: "pytest"

# JavaScript 프로젝트
model: claude-3-opus-20240229
auto-commits: true
lint-cmd: "npm run lint"
test-cmd: "npm test"
```

## Troubleshooting

### API 키 오류
```bash
# API 키 확인
echo $OPENAI_API_KEY

# API 키 설정
export OPENAI_API_KEY=your-key
```

### Git 충돌
```bash
# Aider 종료 후 수동으로 해결
git status
git mergetool
```

### 메모리 문제
```bash
# 적은 파일로 시작
aider --no-auto-commits

# 파일 제거
/drop large_file.py
```

## Advanced Usage

### 커스텀 프롬프트
```bash
# .aider.conf.yml
system-prompt: |
  You are an expert Python developer.
  Follow PEP 8 style guide.
  Write comprehensive docstrings.
  Include type hints for all functions.
```

### 린트 및 테스트 통합
```yaml
# .aider.conf.yml
lint-cmd: "pylint src/"
test-cmd: "pytest -v"
auto-test: true
```

### 여러 모델 사용
```bash
# 복잡한 작업은 GPT-4
aider --model gpt-4 src/complex_algorithm.py

# 간단한 작업은 GPT-3.5
aider --model gpt-3.5-turbo src/utils.py
```

## Example Workflows

### 새 기능 추가
```bash
# 1. 새 브랜치 생성
git checkout -b feature/new-api

# 2. Aider 시작
aider src/api.py tests/test_api.py

# 3. Aider에게 요청
"Add a new endpoint /users/{id} that returns user details"

# 4. 테스트 실행
pytest

# 5. 브랜치 푸시
git push origin feature/new-api
```

### 버그 수정
```bash
# 1. 버그가 있는 파일 추가
aider src/buggy_module.py tests/test_buggy_module.py

# 2. Aider에게 설명
"The function calculate_discount returns wrong values when discount is 0"

# 3. 수정 확인 및 테스트
pytest tests/test_buggy_module.py

# 4. 커밋
/commit "fix: correct discount calculation for zero discount"
```

### 리팩토링
```bash
# 1. 리팩토링할 파일들 추가
aider src/old_module.py src/new_module.py

# 2. Aider에게 요청
"Refactor the UserManager class to use composition instead of inheritance"

# 3. 전체 테스트 실행
pytest

# 4. 커밋
/commit "refactor: improve UserManager design with composition"
```

## Resources

- [Aider Official Website](https://aider.chat/)
- [Aider Documentation](https://aider.chat/docs/)
- [Aider GitHub](https://github.com/paul-gauthier/aider)
- [Discord Community](https://discord.gg/Tv2uQnR5Rk)
