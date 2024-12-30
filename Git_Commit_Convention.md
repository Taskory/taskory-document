## ENG

### Commit Strategy

#### Commit message format

```
<Type>: <Title>

<Body>

<Footer>
```

##### **Type**

**feat**: Add a new feature

**fix**: Fix a bug

**docs**: Modify documentation

**style**: Code formatting (modifications like spaces, colons, without changing logic)

**refactor**: Refactor code (improve code structure without changing functionality)

**perf**: Improve performance

**test**: Add or modify tests

**chore**: Modify build process or auxiliary tools (no production code change)

**revert**: Revert a previous commit

ex)

```
feat: Add user login feature

Added functionality for users to log in with email and password.
Authentication is handled using JWT tokens.
```

### Branch Strategy

#### Branch types

**main branch:** The branch that always contains a deployable state

**feature branch:** Branch for developing new features or improvements (feature/feature-description)

- Example: feature/login

**bugfix branch:** Branch for fixing bugs (bugfix/bug-description)

- Example: bugfix/fix-login-error

**hotfix branch:** Branch for handling urgent bug fixes (hotfix/bug-description)

- Example: hotfix/fix-critical-bug

#### Code style

Use SonarLint for code style enforcement.

## KOR

### 커밋 전략

#### **커밋 메시지 형식**

```
<타입>: <제목>

<본문>

<푸터>
```

##### 타입(type)

**feat**: 새로운 기능 추가

**fix**: 버그 수정

**docs**: 문서 수정

**style**: 코드 포맷팅 (로직 변경 없이 공백, 콜론 등 수정)

**refactor**: 코드 리팩토링 (기능 변화 없이 코드 구조 개선)

**perf**: 성능 개선

**test**: 테스트 추가 또는 수정

**chore**: 빌드 프로세스 또는 보조 도구 수정 (프로덕션 코드 변경 없음)

**revert**: 이전 커밋 되돌리기

ex) 

```
feat: 사용자 로그인 기능 추가

사용자가 이메일과 비밀번호로 로그인할 수 있는 기능을 추가했습니다.
JWT 토큰을 사용하여 인증을 처리합니다.
```

### 브랜치 전략

#### **브랜치 종류**

**main 브랜치:** 배포 가능한 상태를 유지하는 브랜치

**feature 브랜치:** 새로운 기능이나 개선 사항을 개발하는 브랜치 (feature/기능-설명)

- ex: feature/login

**bugfix 브랜치:** 버그를 수정하는 브랜치 (bugfix/버그-설명)

- ex: bugfix/fix-login-error

**hotfix 브랜치:** 긴급하게 수정해야 하는 버그를 다루는 브랜치 (hotfix/버그-설명)

- ex: hotfix/fix-critical-bug

### 코드 스타일

sonarlint 사용







