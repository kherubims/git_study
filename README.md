GIT Study
=========

# 2019.03.20

## 1. MD 사용하기
하단 컨텐츠 참조
[참조 링크]: https://gist.github.com/ihoneymon/652be052a0727ad59601  
하이픈 테스트

## 2. Git Config Error
- ① git 처음 설정후 커밋시 config 관련 오류 발생하는 경우  
하이픈 테스트
<pre>
(base) D:\PythonEnv\project.git\git_study>git commit -m "[ADD] 첫번째 파일 추가 'README.md'"

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got '*****@*****-HP.(none)')
</pre><br>

② 아래와 같이 이메일 및 사용자 이름 설정 추가
<pre>
(base) D:\PythonEnv\project.git\git_study>git config --global user.email "******@gmail.com"
(base) D:\PythonEnv\project.git\git_study>git config --global user.name "****"
</pre><br>

③ config 설정 도중 오류 발생하는 경우, 아래의 파일 삭제필요
'C:\Users\계정아이디\.gitconfig.lock'  
개행 테스트
<pre>
(base) D:\PythonEnv\project.git\git_study>git config --global user.email "*******@gmail.com"
error: could not lock config file C:/Users/*****/.gitconfig: File exists	
</pre>

삭제 커맨드가 안되는 경우 관리자 권한 필요
<pre>
(base) D:\PythonEnv\project.git\git_study>rm C:/Users/*****/.gitconfig.lock
</pre><br>

[참조 링크]: https://stackoverflow.com/questions/25671785/git-fatal-unable-to-auto-detect-email-address

