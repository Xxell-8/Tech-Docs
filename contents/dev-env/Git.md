# Git

> #### INDEX
>
> 1. [로컬 저장소 활용](#1.-로컬-저장소-활용)
> 2. [원격 저장소 활용](#2.-원격-저장소-활용)
> 3. [브랜치 관리](#3.-Branch-관리)
> 4. [Gitflow Workflow](#4.-Gitflow-Workflow)



## 1. 로컬 저장소 활용

#### 1. Git 저장소 만들기
-  Git 저장소를 만드는 법은 크게 2가지로 볼 수 있다. 
① 아직 버전관리를 하지 않는 `로컬 디렉토리` 하나를 선택해서 `Git 저장소를 적용`하는 방법
② 다른 어딘가에서 `Git 저장소를 Clone` 하는 방법



1. 기존 디렉토리를 Git 저장소로 만들기
	- Git으로 관리할 프로젝트 디렉토리로 이동
    - 해당 경로에서 `git init` 명령 실행
    👉 Git 저장소가 되면, `.git` 폴더가 생성되며, 경로 끝에 현재 branch 이름이 표시된다!

	
	
2. 기존 저장소를 Clone 하기
	- `git clone <url>` 명령을 통해 원하는 저장소를 Clone
	
	


#### **2. Git으로 파일 관리 **

- Git이 파일을 관리하게 하려면 저장소에 파일을 추가하고 커밋해야 하는데, `git add` 명령으로 파일을 추가하고 `git commit` 명령으로 커밋할 수 있다.
![Git 상태](https://images.velog.io/images/xxell-8/post/52b49e1a-b401-4384-adae-fb1e7218c6e1/git%20repo.png)



1. `git add`

> `working directory`, 즉 작업 공간에서 변경된 사항을 저장하기 위해 해당 파일을 `staging area`에 추가할 수 있다.
```bash
# 1. 현재 경로의 모든 파일을 add
$ git add .
# 2. 특정 파일 or 경로를 지정해서 add
$ git add <해당 경로>
```

	cf. `git status`를 통해 현재 Git 상태 파악 가능 



2. `git commit`

> `staged` 상태의 파일들에 대한 이력을 커밋하려 해당 시점의 스냅샷을 기록할 수 있다.
> 👉 커밋 메시지는 변경사항을 명확히 알 수 있도록 작성!

```bash
# 1. staged 상태의 파일 커밋
$ git commit -m '<message>'

# 2. 모든 변경 사항 자동 추가 후 커밋
$ git commit -a -m '<message>'
```

- 저장소 히스토리는 `git log`를 통해 확인할 수 있다. (log를 그만 보려면 `q` 입력)
```bash
# 각 라인을 한 줄로 보고 싶을 경우
$ git log --oneline
```



#### **3. 파일 관리 조작 **

1. 특정 파일 무시하기
- `.gitignore` 파일을 만들어 Git으로 관리할 필요가 없는 파일 패턴을 등록할 수 있다.
cf. [gitignore.io](https://www.toptal.com/developers/gitignore)를 활용해 git으로 관리하지 않을 파일 패턴을 편하게 만들 수 있다!



2. `git add` 취소하기
- Staging Area에 추가된 특정 파일을 다시 unstaged 상태로 되돌리기 위해 `git restore` 명령을 사용할 수 있다.
```bash
$ git restore --staged <파일 이름>
```



3. `git commit` 수정하기

- `--amend` 옵션을 통해 커밋 메시지를 수정하거나 최신 커밋에 파일을 추가할 수 있다.
```bash
# 1. 특정 파일을 빠뜨리고 커밋을 남겼을 경우,
$ git commit -m '<message>'
$ git add <forgotten file> # 해당 파일을 다시 add 하고
$ git commit --amend # 최근 커밋에 함께 커밋하기

# 2. 커밋 메시지를 수정해야 하는 경우
$ git commit -m '<old message>'
$ git commit --amend -m '<new message>'
```



4. `git commit` 취소하기

- `git reset [--option] [commit]` 명령을 통해 해당 commit 시점으로 돌아갈 수 있다.

  - 해당 commit 시점으로 돌아가며, 이후 변경 이력에 대해서는 `option`을 통해 조정할 수 있다.

    - `hard`: 해당 commit 시점 이후 변경 이력을 Working Directory에서 삭제
    - `mixed` (default): 해당 commit 시점 이후 변경 이력은 unstaged된 상태로 Working Directory에 보존
    - `soft`: 해당 commit 시점 이후 변경 이력을 staged 상태로 Working Directory에 보존
    ```bash
    # 1. 최근 커밋 취소
    $ git reset HEAD^
    # 2. 최근 2개 커밋 취소
    $ git reset HEAD~2
    # 3. 특정 커밋 시점으로 돌아가기
    $ git log # 커밋 기록을 통해 특정 커밋 ID 확인
    $ git reset <commit ID>
    ```

- `git revert <commit>`

  - 원하는 commit 시점으로 되돌리는 이력을 남기고, 돌아간다.

  - 바로 커밋하지 않고 변경사항을 staging만 시키고 싶다면 `--no-edit` 옵션을 붙이면 됩니다.

    cf. `reset`의 경우, 원하는 commit 시점으로 아예 시간을 되돌리는데, `revert`의 경우 돌아간다는 이력을 새로운 commit으로 남긴다.



## 2. 원격 저장소 활용

> 원격 저장소(Remote Repository)란, 인터넷이나 네트워크 어딘가에 있는 저장소를 말한다. 흔히 `github`이나 `gitlab`에 원격 저장소를 만들어 사용하며, 저장소를 관리하고 데이터를 Push&Pull 하는 작업을 통해 협업이 진행된다. 리모트 저장소를 관리한다는 것은 저장소를 추가, 삭제하는 것뿐만 아니라 브랜치 관리와 데이터 추적 여부 등을 관리하는 것을 말한다.



#### 1. 원격 저장소 연결

- `git remote` 연결을 통해 현재 프로젝트에 등록된 원격 저장소를 확인하거나 추가할 수 있다.
1. 원격 저장소 가져오기

  💡 저장소를 Clone할 경우, 원격 저장소의 단축 이름은 `origin`으로 표시된다._
```bash
$ git clone <http url>
```
2. 로컬 저장소를 원격 저장소에 연결하기
💡 원격 저장소를 추가할 때에는 origin 대신 다른 단축 이름을 설정할 수 있다._
```bash
$ git remote add origin <http url>
$ git remote add <단축 이름> <http url>
```
3. 연결된 원격 저장소 확인하기
```bash
$ git remote -v
```



#### 2. pull & push

1. 원격 저장소에서 데이터 가져오기
- 데이터를 가져오는 방식은 `pull`과 `fetch`로 볼 수 있다.
‣ `pull`: 원격 저장소에서 데이터를 가져와 **자동**으로 Merge
‣ `fetch`: 원격 저장소에서 데이터를 가져와 **수동**으로 Merge

2. 원격 저장소에 데이터 추가하기
- 로컬 저장소에 변경 이력을 commit한 뒤, `git push` 명령을 통해 원격 저장소에 해당 commit을 저장할 수 있다.

```bash
$ git pull origin <branch>
$ git push origin <branch>
```



#### 3. 원격 저장소 관리

1. 원격 저장소 정보 확인하기
- `git remote show <저장소 이름>` 명령으로 원격 저장소에 구체적인 정보를 확인할 수 있다. 
  - 출력 정보에는 원격 저장소의 `URL`과 추적하는 `브랜치`, git pull 명령을 실행할 때 master 브랜치와 Merge 할 브랜치가 무엇인지 등이 포함된다.

2. 저장소 이름 수정/삭제
- `git remote rename <old> <new>`를 통해 저장소 이름을 변경할 수 있다.
- `git remote remove <name>`을 통해 해당 저장소 이름을 삭제할 수 있다.



## 3. Branch 관리

> 브랜치(branch)란, **독립적인 개발**을 위한 기능으로 볼 수 있다. 개발 과정에서 여러 사람이 동시에 다양한 작업을 진행하게 되는데, 필요에 따라 브랜치를 생성하여 다른 브랜치의 영향을 받지 않고 각자 개발을 진행할 수 있으며 이후 다른 브랜치에 병합하는 과정을 통해 작업을 합칠 수 있다.



#### 1. `git branch`

- `git branch` 명령은 브랜치와 관련한 다양한 기능을 지원한다.
- 새로운 작업을 위해 브랜치를 생성할 경우, 새로 생성된 브랜치는 현재 작업 중인 브랜치로부터 분기되어 해당 브랜치의 마지막 커밋을 가리킨다.

```bash
# 1-1. 브랜치 목록 확인
$ git branch 
# 1-2. 브랜치 목록과 각각의 마지막 커밋 확인
$ git branch -v

# 2. 브랜치 생성
$ git branch <branch_name>

# 3. 브랜치 삭제
$ git branch -d <branch_name>

```



#### 2. `git switch`

- `git switch` 명령을 통해 원하는 브랜치로 이동할 수 있다.

> 💡 Git 2.23 버전에서 기존에 사용하던 `checkout`이 `switch`와 `restore`로 분리되었다. `switch`는 브랜치를 변경하는 부분을 담당하며, `restore`는 작업 파일을 복원해주는 역할을 담당한다.

```bash
# 1. 브랜치 이동
$ git switch <branch_name>

# 2. 새로운 브랜치를 생성해 이동
$ git switch -c <branch_name>
```



#### 3. `git merge` & `git rebase`

> - 서로 다른 브랜치에서 작업한 기록을 합치기 위해 2가지의 방법을 사용할 수 있다.
>   - `git merge`
>   - `git rebase`

1. `git merge`

   - 서로 다른 브랜치의 작업 기록을 하나로 합치고, 그 기록을 커밋으로 남기는 방식

     - 각 브랜치의 최종 결과만을 가지고 합친다

     ```bash
     $ git switch master # C3에 위치한 master 브랜치에서
     $ git merge experiment # experiment 브랜치의 커밋 기록을 합친다!
     ```

   ![스크린샷 2022-03-03 오후 2.19.36](../assets/Git.assets/스크린샷 2022-03-03 오후 2.19.36.png)



2. `git rebase`

   - rebase할 브랜치의 작업 기록을 임시로 저장해두고 합칠 브랜치에 차례대로 적용하는 방식

     - 브랜치의 변경사항을 순서대로 다른 브랜치에 적용하면서 합친다

       ⚠️ 단, <u>로컬 브랜치에서 작업할 때는 히스토리를 정리하기 위해</u>서 Rebase 할 수도 있지만, 리모트 등 어딘가에 **Push로 내보낸 커밋에 대해서는 절대 Rebase 하지 말 것!**

     ```bash
     $ git switch experiment # experiment 브랜치를
     $ git rebase master # master에 rebase
     ```

   ![스크린샷 2022-03-03 오후 2.20.24](../assets/Git.assets/스크린샷 2022-03-03 오후 2.20.24.png)

   

   - `git rebase --onto <newbase> <upstream> <branch>`

     - 다른 토픽 브랜치(upstream)에서 갈라져 나온 토픽 브랜치(branch)를 반영할 수 있는데, `--onto` 옵션을 사용해서 **branch의 변경사항을 upstream이 아닌 newbase에 반영**할 수 있다

     - [example] `server`에서 분기된  `client` 브랜치의 변경 사항만  `master`에 옮기고 싶다면?

       ![스크린샷 2022-03-04 오후 12.30.47](../assets/Git.assets/스크린샷 2022-03-04 오후 12.30.47.png)

       ```bash
       # onto 옵션을 이용해 upstream인 server가 아니라 master에 rebase하도록 설정
       $ git rebase --onto master server client
       ```

       ![스크린샷 2022-03-04 오후 12.28.03](../assets/Git.assets/스크린샷 2022-03-04 오후 12.28.03.png)

       - `client` 브랜치의 변경 사항이 master 브랜치로 옮겨진다!

       

   - **인터랙티브** 리베이스 `git rebase -i <수정 직전 커밋>`

     - rebase를 대화형으로 실행해 커밋한 히스토리를 변경, 삭제, 병합 등을 할 수 있다

       ```bash
       # 현재 위치로부터 4개의 커밋을 rebase한다고 하면,
       git rebase -i HEAD~4
       
       # 아래와 같은 vim이 실행
       pick hash1 commit1
       pick hash2 commit2
       pick hash3 commit3
       pick hash4 commit4
       
       # Rebase hash0..hash4 onto hash0 (4 commands)
       #
       # Commands:
       # p, pick <commit> = use commit
       # r, reword <commit> = use commit, but edit the commit message
       # e, edit <commit> = use commit, but stop for amending
       # s, squash <commit> = use commit, but meld into previous commit
       # f, fixup <commit> = like "squash", but discard this commit's log message
       # x, exec <command> = run command (the rest of the line) using shell
       # b, break = stop here (continue rebase later with 'git rebase --continue')
       # d, drop <commit> = remove commit
       # l, label <label> = label current HEAD with a name
       # t, reset <label> = reset HEAD to a label
       # m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
       # .       create a merge commit using the original merge commit's
       # .       message (or the oneline, if no original merge commit was
       # .       specified). Use -c <commit> to reword the commit message.
       ```

       

#### 4. `git cherry-pick`

- `cherry-pick` 명령을 이용해 다른 브랜치의 커밋을 선택해 적용할 수 있다.

  ```bash
  # 하나의 커밋을 가져올 경우
  git cherry-pick <commit hash>
  
  # 여러 개의 커밋을 가져올 경우
  git cherry-pick <commit hash> <commit hash>
  
  # 범위를 지정해 커밋을 가져올 경우
  git cherry-pick <commit hash(start)>..<commit hash(end)>
  ```

  



## 4. Gitflow Workflow

> [Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)는 nvie의 Vincent Driessen에 의해 제안되었으며, 프로젝트 릴리즈를 중심으로 설계된 엄격한 branching model이다. 지속적 SW개발 및 DevOps 구현에 도움이 되어 대규모 프로젝트 관리에도 적용 가능한 workflow이다.



- Gitflow Workflow는 **5가지의 git branch**를 사용하는데,

  - 항상 유지되는 메인 브랜치인 `main`과 `develop`과 
  - 일정 기간 동안만 유지되는 보조 브랜치인 `feature`, `release`, `hotfix`이다.

  

① `main`
- 공식 릴리스 기록을 저장하는 최상단 브랜치
- 배포 이력을 관리하기 위해 사용하기 때문에 배포 가능한 상태만을 관리하는 역할

② `develop`
- 다음 릴리스 버전을 개발하며, 최신 개발 변경 사항을 기록하는 통합 브랜치
- 기능 개발을 위한 브랜치들을 merge하기 위해 사용하며, 모든 기능이 추가되고 버그가 수정되어 배포 가능한 상태일 때 `main` 브랜치에 merge 
- 개발 단계에서는 `develop` 브랜치를 기준으로 작업 진행

③ `feature`
- 기능을 개발하는 브랜치 (ex. `feature/login`)
- 새로운 기능을 개발하거나 버그 수정이 필요할 때, `develop` 브랜치에서 특정 `feature` 브랜치를 분기하여 개발을 진행
- 개발이 완료되면 다시 `develop` 브랜치로 merge되며, 더이상 필요하지 않은 `feature` 브랜치는 삭제

④ `release`
- 출시 버전을 준비하는 브랜치 (ex. `release-2.1`)
- 배포를 위한 전용 브랜치로 릴리스가 준비되면 `develop` 브랜치로부터 `release` 브랜치를 분기하여 배포에 필요한 최종 버그 수정 및 문서 작업 등을 수행
- `release` 브랜치를 통해 배포를 준비하면, 그 기간 동안에도 `develop` 브랜치에서는 다음 버전을 위한 개발이 진행될 수 있음

⑤ `hotfix`
- 릴리스 버전에서 발생한 버그를 수정하는 브랜치 (ex. `hotfix-2.1.1`)
- 배포된 버전에서 급하게 수정이 필요한 경우, `master` 브랜치에서 `hotfix` 브랜치를 분기하여 작업을 수행
- `master` 브랜치로부터 분기되어 다른 개발 단계를 고려하지 않고, 특정 문제를 빠르게 해결할 수 있음

#### Branch의 전체적인 흐름
![Branch 관리](https://images.velog.io/images/xxell-8/post/5ff90db2-5af2-40ef-b189-2f20ccd9d12a/branches.svg)



