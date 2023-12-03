## django Restframework와 git 전략에 대해서

### git 전략
![image](https://github.com/chahyeonuk/django-restframework/assets/90748800/619c6eeb-1f50-4870-86bd-db8eafda961c)

### 예시(게시판)
### 각 branch에 대해서 설명

#### 1. master
#####   현재 배포되어 있는 프로덕트를 의미한다.
#####   실제로 사용자가 사용하고 있는 앱에 대한 최종본이라고 볼수있다.
#####   일반적으로 개발자들이 여기에 들어가서 git에서 push를 할 수 없게끔 lock을 걸어놔야 한다.
#####   settting > 
#### . feature branches 
#####   feature branches 같은 경우에는 각 개발자들이 맡은 기능에 대한 branch라고 이해하면 된다.
#####   django restfamework API를 개발하는데 있어 게시물을 개발한다고 하면 뉴스, 공지사항 등등 각 기능들을 의미한다. 
#####   feature branches는 개발 중에 있는
#####   현재 본인은 각 개발하고 있는 기능들에 대해서는 branch 이름을 feat/{기능 이름}
#####   ex) feat/news, feat/notice etc... 이런식으로 작성하고 있다.

#####
