> ### 1. React 파일 생성

1. 터미널을 연다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/41a04fca-fe5d-4a2a-b06e-530d404e890d/image.png)

2. `'cd'`명령으로 작업할 폴더로 이동한다. 필자는 Documents 폴더 안에서 작업할 것이기 때문에 `'cd Documents'` 명령으로 Documents 폴더로 이동하였다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/5d5d2cbd-3a38-4d15-b866-ae3e117f9992/image.png)

3. `'yarn create react-app {폴더명}'` 명령으로 React 기본 템플릿이 담겨있는 폴더를 생성해준다. 필자는 폴더명을 `deploy-test`로 하였다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/d5fc2999-6742-4bcc-9bb6-ace55561131c/image.png)

![](https://velog.velcdn.com/images/fkstndnjs/post/0c3651c2-49bc-4d8f-9312-806cb16ae60d/image.png)

4. `'cd deploy-test'` 명령으로 방금 생성한 폴더로 이동한다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/cda8619d-1088-4fbe-8148-ccf97194dc15/image.png)

---

> ### 2. Git 설정

1. 이제 Git에 `deploy-test`폴더를 올리면 되지만, 이 폴더는 아직 Git과 연결이 되어있지 않은 상태이다. `remote -v` 명령을 통해 Git과 연결된 repository가 있는지 확인할 수 있다. 현재 `deploy-test`는 Git의 어느 repository와도 연결되어있지 않으므로 명령을 입력해도 터미널에 아무것도 출력되지 않는다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/f5562264-95cf-41b1-b9b1-638030278af3/image.png)

2. Git의 repository와 연결이 되려면 당연히 `deploy-test`를 저장할 repository가 필요할 것이다. 자신의 Git에 repository를 하나 생성해주자.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/4849df7d-7d90-4809-adef-5c9948d527e7/image.png)

3. 초록색 Code 버튼을 클릭해서 HTTPS 주소를 복사한다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/595b0df3-1edb-43ac-82ac-611ab2c82404/image.png)

4. 다시 터미널로 돌아와 `'git remote add origin {HTTPS 주소}'` 명령으로 로컬의 `deploy-test` 폴더와 git의 `React-Deploy-Test` repository를 연결시켜준다. 다시 `remote -v` 명령을 실행해보면 아까와는 다르게 연결된 Git의 repository가 출력되는 것을 볼 수 있다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/c7ce24b4-adaa-4f91-a8a3-8a7fd4cf3149/image.png)

5. Git과 연결이 되었으니 이제 `deploy-test` 폴더를 Git에 올릴 차례인데, 필자는 로컬 브랜치의 이름이 master로 되어있어서 `'git branch -M main'`으로 Git의 브랜치와 이름을 맞춰주었다. 자신의 브랜치가 무슨 이름으로 되어있는지 궁금하다면 `'git branch'` 명령으로 확인해보고 master로 되어있으면 `'git branch -M main'` 명령으로 바꿔주자. 그리고 `'git push orign main'` 명령으로 Git에 폴더를 올리면 되지만 필자는 위에서 `React-Deploy-Test`를 생성할 때 README.md 파일을 같이 생성하는 옵션을 선택하는 바람에 `deploy-test`와 `React-Deploy-Test`의 커밋 history가 달라서 `'--force'`옵션을 통해 강제 푸시를 해주었다. README.md 옵션을 선택하지 않았다면 `'--force'` 옵션을 주지 않아도 업로드가 잘 될 것이다. 그럼 다음과 같이 폴더가 Git으로 업로드 된다.

![](https://velog.velcdn.com/images/fkstndnjs/post/806b0e6c-aaee-43de-9cb9-accd46bdb398/image.png)

![](https://velog.velcdn.com/images/fkstndnjs/post/00defd51-ad2a-4649-b596-aaeb4c7cd7d2/image.png)

---

> ### 3. Netlify로 배포하기

1. 먼저 Netlify에 가입을 해준다. Netlify에 가입을 하고나면 다음과 같은 화면이 보일 것이다. 여기서 `Import from Git` 버튼을 클릭한다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/ca10c980-141f-4327-bdbf-72a59b36e5a8/image.png)

2. 그럼 연결할 수 있는 4개의 Git기반 플랫폼이 나오는데, 우리는 GitHub을 사용하므로 GitHub을 클릭한다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/f580de15-c623-45cb-b0c2-01ce1217dbb3/image.png)

3. 여기서 Repositoy를 선택하라고 나올텐데 모든 Repository를 나오게 해도 되고 몇 개를 선택해도 된다. 필자는 `React-Deploy-Test`만 나오게 설정을 했다. 여전히 Repository가 목록에 나오지 않거나 추후에 이 설정을 바꾸고 싶다면 맨 밑의 `'Configure the Netlify app on GitHub'`을 클릭해서 설정해주면 된다. `React-Deploy-Test`가 목록에 나왔다면 클릭해서 다음 과정으로 넘어가자
   ![](https://velog.velcdn.com/images/fkstndnjs/post/56e4f8b4-c8b5-4da5-97e3-220a24c17e74/image.png)

4. 이 화면이 나올텐데 다른 건 건드리지 않아도 되고 `Build command`와 `Publish directory` 입력란을 다음과 같이 작성해준다. `Build command`는 파일을 빌드할 때 사용할 명령어를 작성하는 란이고, `Publish directory`는 빌드가 되어 실행할 준비를 마친 파일이 담겨있는 폴더의 이름을 작성하는 란이다. 처음에 `'yarn create react-app {폴더명}'` 명령으로 생성했던 React 템플릿의 기본 설정은 각각 `'yarn build'`와 `'build'`이다. 작성을 마쳤다면 맨 밑의 `Deploy site` 버튼을 클릭한다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/19132e67-db79-49d0-b541-c93f1f5d143e/image.png)

5. 버튼을 클릭하면 다음과 같은 화면에 `'Site deploy in progress'`라는 메세지와 함께 배포가 진행된다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/f8584cb0-0a7b-4492-ac94-93809d5fc2eb/image.png)

6. 배포가 완료되면 다음과 같이 `'Site deploy in progress'` 메세지가 있었던 곳에 https 주소가 하나 생성된 것을 볼 수 있다. 이 주소가 우리가 만들었던 웹페이지가 배포되어 Netlify가 만들어준 url이다. 이것을 복사해서 주소창에 붙여넣기 해보면 `'yarn create react-app {폴더명}'` 명령으로 만들어진 기본 웹페이지가 나오는 것을 볼 수 있다.
   ![](https://velog.velcdn.com/images/fkstndnjs/post/55ae9768-7c0b-4a27-b23d-6e7734ad60da/image.png)

![](https://velog.velcdn.com/images/fkstndnjs/post/e83a497f-a1f5-4b4d-b599-7b9e70402c6c/image.png)
