# SSuR-2026 과제 제출 가이드

모르는 것은 ChatGPT, Claude 등 AI에게 물어보며 진행한다.  
각 단계의 목적과 순서를 이해하는 것이 중요하다.

---

## 제출 절차

### Step 1. GitHub 계정 만들기

[https://github.com](https://github.com) 에서 계정을 생성한다.

---

### Step 2. 저장소 Fork하기

아래 저장소를 본인 계정으로 Fork한다.

```
https://github.com/ksublee/SSuR2026
```

Fork 후 본인 계정에 `SSuR2026` 저장소가 생성된다.

---

### Step 3. RStudio Server 접속

아래 주소 중 하나에 접속한다.

```
https://ksublee.dev/rstudio7
https://ksublee.dev/rstudio8
```

접속 후 **Terminal** 탭을 연다.

---

### Step 4. Git 사용자 정보 설정

```bash
git config --global user.name "본인이름"
git config --global user.email "GitHub가입이메일"
```

> 이 설정을 하지 않으면 Step 7의 commit 단계에서 아래 오류가 발생한다.
> ```
> Author identity unknown
> *** Please tell me who you are.
> ```
> 오류가 발생하면 이 단계로 돌아와 설정한 뒤 다시 commit한다.

---

### Step 5. 저장소 Clone하기

**본인 계정에 Fork된 저장소**를 clone한다.

```bash
git clone https://github.com/본인Github아이디/SSuR2026.git
cd SSuR2026
```

---

### Step 6. Branch 만들기

branch 이름은 본인 학번으로 한다.

```bash
git checkout -b 2XXXXXXX
```

---

### Step 7. HW1.Rmd 수정

RStudio에서 `HW1.Rmd` 파일을 열고, **파일 맨 아래에** 본인 예제를 추가한다.

- 기존 내용은 수정하지 않는다.
- 강의자료에 이미 있는 예제나 다른 학생이 제출한 예제는 사용할 수 없다. 본인이 새로 만든 예제여야 한다.
- 아래 형식을 따른다.

~~~markdown
### 예제 제목

#### 학번: 2XXXXXXX / 이름: 홍길동

설명

```{r}
# R 코드
```
~~~

---

### Step 8. Commit

```bash
git add HW1.Rmd
git commit -m "Add example 2XXXXXXX"
```

---

### Step 9. Push

```bash
git push origin 2XXXXXXX
```

> 처음 push할 때 GitHub 아이디와 비밀번호 입력을 요구할 수 있다.  
> 이때 비밀번호란에 일반 비밀번호를 입력하면 인증이 실패한다.  
> GitHub는 비밀번호 대신 **Personal Access Token(PAT)** 을 사용해야 한다.
>
> **PAT 발급 순서**
> 1. GitHub 로그인 → 오른쪽 위 프로필 아이콘 → **Settings**
> 2. 왼쪽 메뉴 맨 아래 **Developer settings** → **Personal access tokens** → **Tokens (classic)**
> 3. **Generate new token (classic)** 클릭
> 4. **Note**: 용도 입력 (예: `SSuR2026`)
> 5. **Expiration**: `90 days` 선택
> 6. **Select scopes** 에서 **repo** 항목 체크 (하위 항목 전체 자동 선택됨)
>
>    ```
>    [v] repo  Full control of private repositories
>        [v] repo:status
>        [v] repo_deployment
>        [v] public_repo
>        [v] repo:invite
>        [v] security_events
>    ```
>
> 7. 아래 **Generate token** 버튼 클릭
> 8. 생성된 토큰을 복사해 둔다 (페이지를 벗어나면 다시 볼 수 없다)
>
> 이후 비밀번호 입력란에 복사한 토큰을 붙여넣는다.  
> username은 GitHub 아이디, password는 PAT를 입력한다.

---

### Step 10. Pull Request 생성

[https://github.com/ksublee/SSuR2026](https://github.com/ksublee/SSuR2026) 에 접속하면 본인 branch에 대한 **Compare & pull request** 버튼이 표시된다. 클릭한다.

아래 항목을 확인하고 입력한다.

- **base repository**: `ksublee/SSuR2026` / **base**: `main`
- **head repository**: `본인Github아이디/SSuR2026` / **compare**: `2XXXXXXX`
- **Title**: 학번과 이름을 입력한다 (예: `2XXXXXXX 홍길동`)
- **Description**: 추가한 예제를 간단히 설명한다 (예: `정규분포 난수 생성 예제 추가`)

작성 후 **Create pull request** 버튼을 클릭하면 제출 완료이다.

Pull Request가 승인되면 GitHub에서 아래와 같은 이메일이 발송된다.

```
Merged ~ into main.
```

이 이메일을 강의포털에 제출한다.

---

## 문제가 생긴 경우

충돌이나 오류가 발생하면 아래 명령어로 처음부터 다시 시작한다.

```bash
cd ~
rm -rf SSuR2026
git clone https://github.com/본인Github아이디/SSuR2026.git
cd SSuR2026
```

이후 Step 6부터 다시 진행한다.
