# 20231229
20231229 프로 디지털 아카데미 git 실습

## 핵심 명령어

git add apt.txt // '스테이징' 

git commit -m ~~~ // '메세지를 남김' 

git add . // '모든 파일을 스테이징' 

git status // '커밋할 파일이 있는지, 어떤 상태인지' 

git log --all// '모든 로그를 보여줌(--oneline은 한번에)' 

(test1에서 이어옴) 한번에 add할수 있을걸? 

## workflow
파일 수정 후 add(이 과정에서 not staged -> changes to be comitted로 변경됨) 

commit 시 다시 'nothing to commit' 상태가 됨(바뀐걸 커밋했으니까) 

변화사항이 있을까요? // git diff를 통해 '직전 commit'과 아직 commit되지 않은 부분에 대해 비교할 수 있음 

// git difftool을 이용하면 직전 커밋과 비교가능, git difftool '커밋아이디'를 이용하면 해당 커밋의 지점으로 돌아가서 비교가능 

// git difftool '아이디1' '아이디2' 를 선택하면 두개의 지점을 비교가능 

// cli가 아닌 gui 환경을 희망한다면 git graph 깔아라~ 

// gitignore 기능: 원하지 않는 파일을 무시하는 기능(각종 조건을 줄 수 있다) 

## from github to local , back to github

// 가장 기억해야 할 내용은, clone - pull - push의 흐름

// 디렉토리 생성 후, git clone 기능으로(혹은 남의 것을 사용한다면 fork가 될수도 있겠네요) 레포지토리를 가져오기. (저 이제 이거 갖고 로컬에서 작업합니다?)

// 로컬에서 작업 후 저장하면, vsc 상에서 'modified' 신호가 뜨게 됨.

// status를 확인하면 로컬-로컬에서의 작업과 똑같이 not staged for commit가 발생함.

// 이제 로컬에서와 같이 add와 commit를 진행하고, git push origin main(브랜치명이 main이 아니라면 브랜치명)을 시행하면 정상적으로 로컬에서 github로 올라감.

// github에서 수정된 내용을 가져오고 싶다면? pull 해주세요. 

## Co-op (branch)

### why?
> 협업 툴이잖아요? 

### head?
> 현재 작업중인 브랜치를 가리키는 포인터 (어디까지의 commit를 사용하고 있는가?)

### how?
> 브랜치 만들고, 각자 작업하고, 공동 작업물에 합치는 일입니다. '원론적으로는'/....
> 내가 보고 있는 branch = 내가 작업하고 있는 폴더. (시점이 다를 수 있음)

### when?
예를 들어, main과 test branch에서 완전 다른 내용을 작업했다면?
그냥 merge 하고 push 하면 됩니다.

하지만, 동일한 파일을 수정했다면?
* test branch 자체적으로 push할 경우:
  -> github에서 merge pull request 발생. 그 뒤로 처리하면 됩니다.
* main과 merge 후 main에서 push하고자 하는 경우?:
  -> conflict를 해결해 주어야 한다.

각각의 수정을 위한 branch의 목적을 달성하고 github에 pull까지 완료했다면?
  -> 지우시면 되죠 뭐. git branch -d (로컬) / git push origin -d (원격 브랜치)

## further

* 폴더를 하나 생성하고 레포를 하나 클론해왔다고 가정.
이전 상위 폴더로 돌아가서 다른 레포를 clone해온다면, 레포 두개에 대한 작업공간을 구축하고, 디렉토리를 이동해가며 각각의 레포에 대한 작업이 가능한 것입니다.
하지만 각각의 레포에 대해 수정한 내용을 저장하고, 상위 폴더로 돌아와 두개의 레포에 대한 add를
git add .으로 한번에 수행할 수 있을까요?
  -> 이건 안 됩니다. 각각의 레포에 대해서만 push가 가능합니다.

* fast-forward 조건에 일치하지 않는 경우?
  -> conflict가 발생하는 이유는, 내가 pull 해온 원격 저장소의 내용을 기반으로 로컬에서 작업하는 중에
  원격 저장소에 commit이 발생하여 원본과의 충돌이 발생하는 경우입니다. (branch가 동일하더라도 발생 가능!!)
    -> 이런 경우엔? rebase를 통해 해결할 수도 있고, 수동으로 수정하는 것도 가능함!

* non-fastforward 상황에서 충돌 원인을 못 찾겠는 경우엔?
  -> '파일을 검토 후 데이터가 유실될 걱정이 없는 상황에 한해' push할 브랜치명 앞에 +를 더해서 forced update도 가능.
  뭘 해도 답이 안나오는경우? rm -rf로 다 밀어버리고 git clone으로 다시 받아와도.. 괜찮을 수도 있어요...

* main 브랜치가 아닌 다른 branch를 push하는 것도 가능한가요?
  -> 네맞아요 그게 목적이라니까요???? 작업중에 다른 버그를 수정해야 하면 해당 branch에서 버그를 수정 후 push 가능.

## question

* Q1: 왜 touch 같은 명령어가 vscode 상에서 동작하지 않나요? 
  -> powershell 말고 bash를 터미널로 활용하세요.

* Q2: 불행하게도 gitignore를 먼저 commit해두지 않고 파일을 수정했다면? 
  -> git의 캐시를 지우고 다시 시도하세요.

* Q3: 깃허브 상에서 readme등을 수정할 때 커밋을 덕지덕지 넣지 않으려면?
  -> preview 기능을 활용하세요.

* Q4: 배운 내용을 어떻게 기록할까요?
  -> 하나의 레포지토리에 하위폴더로 기록하지 말고, 각각의 레포지토리를 만드세요. (파일 관리 관점에서 더 효율적)

* Q5: 왜 master이 아니고 main인가요?
  -> 노예제도 때문이라네요....

* Q6: push해올때 문제가 발생한다면?
  -> 폴더명을 맞추셔야 합니다.
  Ex) 최상위 폴더를 만들고 클론해왔으면 그 아래 레포가 하나 더 깔리겠죠?
  그쪽 레포로 이동하셔서 작업을 하셔야지..

* Q7: 커밋을 잘못했어요...
  -> 아직 원격에 push하지 않은 경우는 git reset --hard '커밋명' 으로 변경하시면 됩니다.