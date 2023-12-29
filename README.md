# 20231229
20231229 프로 디지털 아카데미 git 실습

git add apt.txt // '스테이징' 

git commit -m ~~~ // '메세지를 남김' 

git add . // '모든 파일을 스테이징' 

git status // '커밋할 파일이 있는지, 어떤 상태인지' 

git log --all// '모든 로그를 보여줌(--oneline은 한번에)' 

(test1에서 이어옴) 한번에 add할수 있을걸? 

## workflow
파일 수정 후 add(이 과정에서 not staged -> changes to be comitted로 변경됨) 

commit 시 다시 'nothing to commit' 상태가 됨(바뀐걸 커밋했으니까) 

변화사항이 있을까요? // git diff를 통해 '직전 commit'과 아직 commit되지 않은 부분에 대해 기록할 수 있음 

// git difftool을 이용하면 직전 커밋과 비교가능, git difftool '커밋아이디'를 이용하면 해당 커밋의 지점으로 돌아가서 비교가능 

// git difftool '아이디1' '아이디2' 를 선택하면 두개의 지점을 비교가능 

// cli가 아닌 gui 환경을 희망한다면 git graph 깔아라~ 

// gitignore 기능: 원하지 않는 파일을 무시하는 기능(각종 조건을 줄 수 있다) 

## from github to local , back to github

// 가장 기억해야 할 내용은, clone - pull - push의 흐름

// 디렉토리 생성 후, git clone 기능으로(혹은 남의 것을 사용한다면 fork가 될수도 있겠네요) 레포지토리를 가져오기. (저 이제 이거 갖고 로컬에서 작업합니다?)

// 저장하면, 'modified' 신호가 뜨게 됨.

// status를 확인하면 로컬-로컬에서의 작업과 똑같이 not staged for commit가 발생함.

// 이제 로컬에서와 같이 add와 commit를 진행하고, git push origin main을 시행하면 정상적으로 로컬에서 github로 올라감.

// github에서 수정된 내용을 가져오고 싶다면? pull 해주세요. 

## further

폴더를 하나 생성하고 레포를 하나 클론해왔다고 가정.
이전 상위 폴더로 돌아가서 다른 레포를 clone해온다면, 레포 두개에 대한 작업공간을 구축하고, 디렉토리를 이동해가며 각각의 레포에 대한 작업이 가능한 것입니다.
하지만 각각의 레포에 대해 수정한 내용을 저장하고, 상위 폴더로 돌아와 두개의 레포에 대한 add를
git add .으로 한번에 수행할 수 있을까요?

이건 안 됩니다. 각각의 레포에 대해서만 push가 가능합니다.

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
