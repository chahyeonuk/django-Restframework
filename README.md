## django Restframework와 git 전략에 대해서

### git 전략
### 밑에 있는 이미지의 git 전략은 Vincent Driessen이 A successful Git branching model 이라는 글이 인기를 끌며 대중적으로 사용되게된 브랜치 전략이다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/619c6eeb-1f50-4870-86bd-db8eafda961c)

### 예시(게시판)
### 각 branch에 대해서 설명

#### 1. master
* 현재 배포되어 있는 프로덕트를 의미한다.
* 실제로 사용자가 사용하고 있는 앱에 대한 최종본이라고 볼수있다.
* 일반적으로 개발자들이 여기에 들어가서 git에서 push를 할 수 없게끔 lock을 걸어놔야 한다.
  * (1). settings에 들어간 후
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/e2ca3e4d-0876-46ee-9208-dadb1b48d5f7)
  * (2). Code adn automation메뉴에 Branches에 들어간다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/039c619b-6dda-4df1-ab89-ef1e9dd544d0)
  * (3). Add branch protection rule을 클릭한다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/e0736a97-959c-4352-854b-1dcbb0ffac22)
  * (4). Branch name paattern에 master branch 또는 main branch를 적고, Require a pull request before merging 체크박스를 클릭한다.
  * Require a pull request before merging는 master 또는 main에 merge 하려면 pull request(pr)을 보내야 한다는 의미이다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/95933d09-7497-4e4d-8c16-82111adb168d)
  * (5). 스크롤을 내리고 Lock branch를 선택한다. 필자는 일반적으로 pr과 lock branch 이 두가지를 선택하는 편이다. 
  * 마지막으로 Create 버튼을 클릭하게 되면 끝난다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/ce9a7533-7364-4f5d-9024-0a87c7d89788)

#### 2. develop 
* 다음 버전을 개발하기 위해 각 기능(features) 들을 모아둔 브랜치라고 볼수 있다. 각 기능들이 완료 되면 최종적으로 테스트 한후
* 테스트: 단위 테스트, UI/UX 테스트(사용자 경험 테스트) 등 거치고 난 후 master branch에 merge하게 되면 사용자는 새로운 기능에 대해서
* 바뀐 버전을 업데이트를 할 수 있다.

#### 3. feature branches 
* feature branches 같은 경우에는 각 개발자들이 맡은 기능에 대한 branch라고 이해하면 된다.
* django restfamework API를 개발하는데 있어 게시물을 개발한다고 하면 뉴스, 공지사항 등등 각 기능들을 의미한다.
* feature branches는 개발 중에 있는 현재 필자는 각 개발하고 있는 기능들에 대해서는 branch 이름을 feat/{기능 이름}
* ex) feat/news, feat/notice etc... 이런식으로 작성하고 있다.
* 이 부분은 각 개발자 또는 기능에 대한 각 팀에 대한 branch로 정의해도 괜찮을것 같다.
* 상세 기능에 대한 branch가 있기 때문에 develop에서 pull을 할 때 병합 충돌(merge conflict)를 주의해야 한다.
* 각 개발자들간에 git status를 확인하고 코드를 수정해야 한다.

#### 4. Release
* 프로덕트 배포를 준비하기 위한 브랜치이다. develop 브랜치에서 생성하며, 배포 준비가 완료되었다면 Main과 Develop 브랜치에 둘다 머지한다.
* 이때, Main 브랜치에는 태그를 이용하여 버전을 표시한다.
 * (1) tags를 클릭한다. 
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/8cb4cd64-3457-41ff-a65d-edf21e33aab4)
 * (2) Releases를 클릭하고, Create a new release를 버튼을 클릭한다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/06bf2956-807c-4b0c-be8a-0e3ac69d8323)
 * (3) Choose a tag를 클릭하고 vesion을 tag하게 되면 된다. 오른쪽 tagging suggestions을 보면 v1.0.0 or v2.3.4를 선호한다고 되어있다.
 * 어차피 다른 방식으로 쓰면 publish가 되지도 않는다.
 * 필자는 v0.9.0으로 베타 테스트 버전이라고 describe로 적어 보겠다.
 * 그 후 publish release 버튼을 누르게 되면 버전을 저장하게 된다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/7d8e3a8f-f5ff-4b8a-8d8d-3f13ba2e3446)
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/607bb199-12e8-44f9-bb29-ea372da08d74)
 * (5) release의 배포 방법은 이렇게 끝나게 된다.
 * release 방식은 v1.0.0이든 각 회사 마다의 버전상태나 관리가 다르기 때문에 대표적인 기능에 대해서만 v2.0.0 이런식으로 version up을 하게 되면 될 것 같다.
 * ex) 게시판에서 결제기능이 추가되었을때 등등 한가지의 예시로만 보였지만 여러 가지 이유로 다른 식의 버전업이 가능하다고 생각한다.
  
#### 5. Hotfixes
* 이미 배포된 main branch에서 문제가 발생했을때 Hotfixes 브랜치를 생성하고 이 곳에 수정하게 된다.
* main 또는 master에서 문제가 생긴 것이므로 develop에서도 문제가 없다고 보장 할수 없다.
* 그래서 문제가 해결되면 main branch에만 merge하는 것이 아닌 develop과 main branch에 둘다 merge하면 된다.

## 이렇게 5가지의 git flow 전략에 대해서 알아 봤다. 모든 브랜치에 대해서는 정답은 아니고 main, develop, feature branches 이외에는 필수적인 요소는 아닌 것같다.(개인적인 생각)
## 필자는 main에서 버그가 생길 시 main에서 pull을 진행 한 후 git checkout -b "feat/hotfixes"를 하게 되고 develop에 pull request를 하여 테스트를 진행 후 main에 pull request를 하게 된다.
## 이렇게 되면 hotfixes는 feature branches로 넘어오게 되고 develop에서만 중간에서 관리를 하게 된다.
## git flow 뿐만 아니라 git에서는 다양한 전략이 있다. 사용자에게 최신 버전만 사용하게 하는 전략과 여러 버전을 병렬적으로 관리하는 버전도 있기 때문에 
## 이 또한 어느 프로젝트 또는 버전 관리 방법에 따라서 달라지기도 한다.




