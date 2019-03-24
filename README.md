TIL with Git Study
=========

# 2019.03.23

- NLP 의미역 결정 과정   
서술어에 속하는 논항들 사이의 의미 관계 결정, DB적재를 위해서는 수집되는 자원과 의미 연관관계 생성을 위해서 서술어(=의미 연관관계 명) 및 논항(해당 자원 개체)에 대해서 사전적 정의가 필요  
<pre>
1. Predicate Identification(PI)
2. Predicate Classification(PC)

3. Argument Identification(AI)
4. Argument Classfication(AC) - CTI Entity Recognition(resource)
</pre>

[관련 참조] <https://ratsgo.github.io/korean%20linguistics/2017/06/04/thetarole/>  
[관련 참조] <https://ratsgo.github.io/korean%20linguistics/2017/07/19/valency/>  
[관련 참조] <http://kiise.or.kr/e_journal/2015/2/JOK/pdf/10.pdf>  


# 2019.03.22

- git commit message 수정  
마지막 커밋 메세지 수정
<pre>
$ git commit --amend -m "[FIX] edit commit message"

$ git push -f
</pre>

[관련 참조] <http://tech.javacafe.io/2018/03/01/how-to-change-git-commit-message/>

# 2019.03.21

- Ubuntu alias 명령어 환경변수에 등록하기  
'alias' command로 명령어 등록시 console 창이 꺼지면 등록된 alias가 사라지는것을 bashrc에 등록하여 방지  
'.bashrc'를 편집기로 편집  
<pre>
$ sudo vi ~/.bashrc
</pre> 

'.bashrc'에 하단 라인 추가
<pre>
e.g)  
alias gloga="git log --all --decorate --oneline --graph"
</pre>
'.bashrc' 적용
<pre>
$ sudo source ~/.bashrc
</pre>

# 2019.03.20

- MD 사용하기  
하단 컨텐츠 참조  

[관련 참조]  <https://gist.github.com/ihoneymon/652be052a0727ad59601>  

- Git Config Error  
① git 처음 설정후 커밋시 config 관련 오류 발생하는 경우  

<pre>
(base) D:\PythonEnv\project.git\git_study>git commit -m "[ADD] 첫번째 파일 추가 'README.md'"

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got '*****@*****-HP.(none)')
</pre>  

② 아래와 같이 이메일 및 사용자 이름 설정 추가  

<pre>
(base) D:\PythonEnv\project.git\git_study>git config --global user.email "******@gmail.com"
(base) D:\PythonEnv\project.git\git_study>git config --global user.name "****"
</pre>  

③ config 설정 도중 오류 발생하는 경우, 아래의 파일 삭제필요  
'C:\Users\계정아이디\.gitconfig.lock'  
<pre>
(base) D:\PythonEnv\project.git\git_study>git config --global user.email "*******@gmail.com"
error: could not lock config file C:/Users/*****/.gitconfig: File exists	
</pre>

④ 삭제 커맨드가 안되는 경우 관리자 권한 필요  
<pre>
(base) D:\PythonEnv\project.git\git_study>rm C:/Users/*****/.gitconfig.lock
</pre>  

[관련 참조] <https://stackoverflow.com/questions/25671785/git-fatal-unable-to-auto-detect-email-address>
