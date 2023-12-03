## django Restframework와 git 전략에 대해서

### git 전략
### 밑에 있는 이미지의 git 전략은 Vincent Driessen이 A successful Git branching model 이라는 글이 인기를 끌며 대중적으로 사용되게된 브랜치 전략이다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/619c6eeb-1f50-4870-86bd-db8eafda961c)

### 예시(게시판)
### 각 branch에 대해서 설명

#### 1. master
* 현재 배포되어 있는 프로덕트를 의미한다.
##### * 실제로 사용자가 사용하고 있는 앱에 대한 최종본이라고 볼수있다.
##### * 일반적으로 개발자들이 여기에 들어가서 git에서 push를 할 수 없게끔 lock을 걸어놔야 한다.
##### *   (1). settings에 들어간 후
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/e2ca3e4d-0876-46ee-9208-dadb1b48d5f7)
##### *   (2). Code adn automation메뉴에 Branches에 들어간다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/039c619b-6dda-4df1-ab89-ef1e9dd544d0)
##### *   (3). Add branch protection rule을 클릭한다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/e0736a97-959c-4352-854b-1dcbb0ffac22)
##### *   (4). Branch name paattern에 master branch 또는 main branch를 적고, Require a pull request before merging 체크박스를 클릭한다.
##### Require a pull request before merging는 master 또는 main에 merge 하려면 pull request(pr)을 보내야 한다는 의미이다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/95933d09-7497-4e4d-8c16-82111adb168d)
##### *   (5). 스크롤을 내리고 Lock branch를 선택한다. 본인은 일반적으로 pr과 lock branch 이 두가지를 선택하는 편이다. 
#####   마지막으로 Create 버튼을 클릭하게 되면 끝난다.
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/ce9a7533-7364-4f5d-9024-0a87c7d89788)





#### . feature branches 
#####   feature branches 같은 경우에는 각 개발자들이 맡은 기능에 대한 branch라고 이해하면 된다.
#####   django restfamework API를 개발하는데 있어 게시물을 개발한다고 하면 뉴스, 공지사항 등등 각 기능들을 의미한다. 
#####   feature branches는 개발 중에 있는
#####   현재 본인은 각 개발하고 있는 기능들에 대해서는 branch 이름을 feat/{기능 이름}
#####   ex) feat/news, feat/notice etc... 이런식으로 작성하고 있다.

#####
