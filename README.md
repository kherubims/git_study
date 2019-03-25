TIL with Git Study
=========
# 2019.03.25 (월)
- Git 디렉토리내 파일은 무시하고 디렉토리 구조만 유지하기
<pre>
// 빈 디렉토리로 이동
$ cd log

// '.gitkeep' 빈 파일 생성
$ touch .gitkeep

// git add & commit
$ git add .gitkeep
$ git commit -m "Add direcotry './log'"

// .gitignore에 등록 : "!log/.gitkeep"
$ vi .gitignore
</pre>

<pre>
// git cashe 삭제 (stage에서 제거..?)
$ git rm -r --cached log/.gitkeep
$ git rm -r --cached log/test.log
</pre>

[관련 참조] <https://gusrb.tistory.com/72>  
[관련 참조] <https://ipex.tistory.com/entry/gitlab-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%9E%AC%EC%83%9D%EC%84%B1-%EC%95%88%ED%95%98%EA%B3%A0-%ED%8F%B4%EB%8D%94-%EB%82%A0%EB%A6%AC%EA%B8%B0-no-reply-git-proejct-and-folder-Delete>

# 2019.03.24 (일)
- Ubuntu git 사용시 기본 에디터 변경
<pre>
// vi 또는 vim 사용시
$ git config --global core.editor "vim"

// 추가 설정 필요
$ sudo update-alternatives --config editor
</pre>

- git commit message 수정2(with 'git rebase -i')  

※ 여러사람과 함께 작업하는 공간에서 사용을 권하지 않음
<pre>
// 명령어를 통해 최근 3개의 커밋을 rebase
$ git rebase -i HEAD~3  
  
// 변경할 내용을 'pick' 에서 'edit' 으로 수정 후 저장 & 종료
pick 5367a7d [FIX] MD파일 수정 테스트 'README.md'
edit 33ed978 [FIX] MD파일 수정 테스트2 'README.md'
pick c39737f [FIX] MD파일 수정 테스트3 'README.md'
</pre>

<pre>
// 수정할 내용 변경
$ git commit -amend

// e.g)
[FIX] MD파일 수정 테스트7 'README.md'

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Sun Mar 24 22:42:42 2019 +0900
#
# On branch master
# Your branch is up to date with 'origin/master'.
#
# Changes to be committed:
#       modified:   README.md

</pre>

<pre>
// rebase continue 수행 및 push
$ git rebase --continue
$ git push -f

// 수정할 commit 이력이 추가로 더 있다면 'git commit -amend'로 계속 수정(반복)
$ git commit -amend
</pre>

# 2019.03.23 (토)

- NLP 의미역 결정 과정   
서술어에 속하는 논항들 사이의 의미 관계 결정, DB적재를 위해서는 수집되는 자원과 의미 연관관계 생성을 위해서 서술어(=의미 연관관계 명) 및 논항(해당 자원 개체)에 대해서 사전적 정의가 필요  
<pre>
(Identification - Classification)
1. Predicate Identification(PI)
2. Predicate Classification(PC)

3. Argument Identification(AI)
4. Argument Classfication(AC) - CTI Entity Recognition(resource)
</pre>

[관련 참조: 한국어의 의미역] <https://ratsgo.github.io/korean%20linguistics/2017/06/04/thetarole/>  
[관련 참조: 한국어 서술어의 논항과 자릿수] <https://ratsgo.github.io/korean%20linguistics/2017/07/19/valency/>  
[관련 참조: Structural SVM 기반 한국어 의미역 결정] <http://kiise.or.kr/e_journal/2015/2/JOK/pdf/10.pdf>  


# 2019.03.22 (금)

- git commit message 수정  
<pre>
// 마지막 커밋 메세지 수정
$ git commit --amend -m "[FIX] edit commit message"  
$ git push -f
</pre>

[관련 참조] <http://tech.javacafe.io/2018/03/01/how-to-change-git-commit-message/>

# 2019.03.21 (목)

- Ubuntu alias 명령어 환경변수에 등록하기  
<pre>
// 'alias' 명령어 등록시 console 창이 꺼지면 등록된 alias가 사라지는 것을 위해 bash 환경변수로 등록
// '~/.bashrc' 편집
$ sudo vi ~/.bashrc
</pre>   
  
<pre>
// '~/.bashrc' 하단 라인 추가  
alias gloga="git log --all --decorate --oneline --graph"
</pre>  
  
<pre>
// '~/.bashrc' 적용
$ sudo source ~/.bashrc
</pre>

# 2019.03.20 (수)

- MD 사용하기  
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
'C:\\Users\\계정아이디\\.gitconfig.lock'  
<pre>
(base) D:\PythonEnv\project.git\git_study>git config --global user.email "*******@gmail.com"
error: could not lock config file C:/Users/*****/.gitconfig: File exists	
</pre>

④ 삭제 커맨드가 안되는 경우 관리자 권한 필요  
<pre>
(base) D:\PythonEnv\project.git\git_study>rm C:/Users/*****/.gitconfig.lock
</pre>  

[관련 참조] <https://stackoverflow.com/questions/25671785/git-fatal-unable-to-auto-detect-email-addressu>
