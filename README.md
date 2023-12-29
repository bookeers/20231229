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

## from github to local 

// 가장 기억해야 할 내용은, clone - pull - push의 흐름

// 디렉토리 생성 후, git clone 기능으로 레포지토리를 가져오기.

// 저장하면, 'modified' 신호가 뜨게 됨.

// status를 확인하면 로컬-로컬에서의 작업과 똑같이 not staged for commit가 발생함.

// 이제 로컬에서와 같이 add와 commit를 진행하고, git push origin main을 시행하면 정상적으로 동작함.

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
  -> 노예제도 떄문이라네요....
