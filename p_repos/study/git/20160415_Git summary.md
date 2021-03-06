Git branch 배우기
=================
__Link:__ [Git Branch 배우기](http://learnbranch.urigit.com/)

#Git 명령어
연습 모드에서 쓸 수 있는 다양한 __git 명령어__
```
- commit
- branch
- checkout
- cherry-pick
- reset
- revert
- rebase
- merge
```

#Git Commit

커밋은 Git 저장소에 여러분의 디렉토리에 있는 모든 파일에 대한 스냅샷을 기록하는 것입니다.
디렉토리 전체에 대한 복사해 붙이기와 비슷하지만 훨씬 유용합니다!
Git은 커밋을 가능한한 가볍게 유지하고자 해서, 커밋할 때마다 디렉토리 전체를 복사하는 일은 하지 않습니다.
각 커밋은 저장소의 이전 버전과 다음 버전의 변경내역("delta"라고도 함)을 저장합니다.
그래서 대부분의 커밋이 그 커밋 위에 부모 커밋을 가리키고 있게 되는 것입니다.
저장소를 복제(clone)하려면, 그 모든 변경분(delta)를 풀어내야하는데,
그 때문에 명령행 결과로 아래와 같이 보게됩니다.

- resolving deltas

알아야할 것이 꽤 많습니다만, 일단은 커밋을 프로젝트의 각각의 스냅샷들로 생각하시는 걸로 충분합니다. 커밋은 매우 가볍고 커밋 사이의 전환도 매우 빠르다는 것을 기억해주세요!

- git commit

#Git 브랜치

깃의 브랜치도 놀랍도록 가볍습니다. 브랜치는 특정 커밋에 대한 참조(reference)에 지나지 않습니다. 이런 사실 때문에 수많은 Git 애찬론자들이 자주 이렇게 말하곤 합니다:
브랜치를 서둘러서, 그리고 자주 만드세요
브랜치를 많이 만들어도 메모리나 디스크 공간에 부담이 되지 않기 때문에, 여러분의 작업을 커다른 브랜치로 만들기 보다, 작은 단위로 잘게 나누는 것이 좋습니다.
브랜치와 커밋을 같이 쓸 때, 어떻게 두 기능이 조화를 이루는지 알아보겠습니다. 하지만 우선은, 단순히 브랜치를 "하나의 커밋과 그 부모 커밋들을 포함하는 작업 내역"이라고 기억하시면 됩니다.

- git branch newImage
- git checkout newImage;
- git commit;

#브랜치와 합치기(Merge)

좋습니다! 지금까지 커밋하고 브랜치를 만드는 방법을 알아봤습니다.
이제 두 별도의 브랜치를 합치는 몇가지 방법을 알아볼 차례입니다.
이제부터 배우는 방법으로 브랜치를 따고, 새 기능을 개발 한 다음 합칠 수 있게 될 것입니다.
처음으로 살펴볼 방법은 git merge입니다.
Git의 합치기(merge)는 두 개의 부모(parent)를 가리키는 특별한 커밋을 만들어 냅니다.
두개의 부모가 있는 커밋이라는 것은 "한 부모의 모든 작업내역과 나머지 부모의 모든 작업,
그리고 그 두 부모의 모든 부모들의 작업내역을 포함한다"라는 의미가 있습니다.
그림으로 보는게 이해하기 쉬워요. 다음 화면을 봅시다.

- git merge bugFix master
- git merge master bugFix


#Git 리베이스(Rebase)

브랜치끼리의 작업을 접목하는 두번째 방법은 리베이스(rebase)입니다.
기본적으로 커밋들을 모아서 복사한 뒤, 다른 곳에 떨궈 놓는 것입니다.
조금 어려게 느껴질 수 있지만, 리베이스를 하면 커밋들의 흐름을 보기 좋게 한 줄로 만들 수 있다는 장점이 있습니다. 리베이스를 쓰면 저장소의 커밋 로그와 이력이 한결 깨끗해집니다.
어떻게 동작하는지 살펴볼까요…

- git rebase master //  master 밑으로 들어감.


#Git에서 작업 되돌리기
Git에는 작업한 것을 되돌리는 여러가지 방법이 있습니다.
변경내역을 되돌리는 것도 커밋과 마찬가지로 낮은 수준의 일(개별 파일이나 묶음을 스테이징 하는 것)과 높은 수준의 일(실제 변경이 복구되는 방법)이 있는데요, 여기서는 후자에 집중해 알려드릴게요.
Git에서 변경한 내용을 되돌리는 방법은 크게 두가지가 있습니다
-- 하나는 git reset을 쓰는거고, 다른 하나는git revert를 사용하는 것입니다.
다음 화면에서 하나씩 알아보겠습니다.

#Git 리셋(reset)
git reset은 브랜치로 하여금 예전의 커밋을 가리키도록 이동시키는 방식으로 변경 내용을 되돌립니다. 이런 관점에서 "히스토리를 고쳐쓴다"라고 말할 수 있습니다.
즉, git reset은 마치 애초에 커밋하지 않은 것처럼 예전 커밋으로 브랜치를 옮기는 것입니다.

- git reset HEAD~1


#Git 리버트(revert)
각자의 컴퓨터에서 작업하는 로컬 브랜치의 경우 리셋(reset)을 잘 쓸 수 있습니다만,
"히스토리를 고쳐쓴다"는 점 때문에 다른 사람이 작업하는 리모트 브랜치에는 쓸 수 없습니다.
변경분을 되돌리고, 이 되돌린 내용을 다른 사람들과공유하기 위해서는,
git revert를 써야합니다. 예제로 살펴볼게요.

```
git revert HEAD
git rebase another master
git cherry-pick c4
git branch -f three c2
git rebase -i
git cherry-pick
```

- 대화형 (-i 옵션) 리베이스(rebase)로는 어떤 커밋을 취하거나 버릴지를 선택할 수 있습니다.
또 커밋의 순서를 바꿀 수도 있습니다. 이 커맨드로 어떤 작업의 일부만 골라내기에 유용합니다.
- 체리픽(cherry-pick)은 개별 커밋을 골라서 HEAD위에 떨어뜨릴 수 있습니다.
- git rebase -i 명령으로 우리가 바꿀 커밋을 가장 최근 순서로 바꾸어 놓습니다
- commit --amend 명령으로 커밋 내용을 정정합니다
- 다시 git rebase -i 명령으로 이 전의 커밋 순서대로 되돌려 놓습니다
