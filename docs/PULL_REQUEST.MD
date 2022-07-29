# Pull Request

## 1. 프로젝트 폴더 생성
![image](https://user-images.githubusercontent.com/18400730/181305399-eba241e6-af19-4738-90de-cb326fab6ccc.png)
Frontend-interview 프로젝트를 설치할 폴더를 새로 만듭니다.

## 2. 생성한 폴더에서 Git Bash here
![image](https://user-images.githubusercontent.com/18400730/181305773-85550cfe-047e-4421-9937-d692cdc67ad8.png)


## 3. Git bash에서 "code ." 실행
![image](https://user-images.githubusercontent.com/18400730/181305850-46fc780a-fa1d-4c97-9175-a77f5bb45fda.png)

## 4. git clone https://github.com/Nobase-Front-End/Frontend-Interview.git 주소 복사
![image](https://user-images.githubusercontent.com/18400730/181306013-4478d585-591b-4bd1-8302-004c9b9f554f.png)
https://github.com/Nobase-Front-End/Frontend-Interview 사이트에 들어가서 주소복사

## 5. Visual Studio에서 4번에서 Git clone 실행
![image](https://user-images.githubusercontent.com/18400730/181306468-63aced5e-2860-4d95-9391-9de5c6cfbafe.png)

## 6. Visual Studio에서 git 세팅
![image](https://user-images.githubusercontent.com/18400730/181308850-07f36a11-0fb6-48c5-be2f-59fa166e9f13.png)

Terminal을 git bash로 선택
git init으로 git 초기화
git switch -c 이름/문제번호


## 7. N주차/문제번호_주제 (예시 : 1주차/005_CSR_SSR_김연아)로 파일 생성
![image](https://user-images.githubusercontent.com/18400730/181666653-40856410-d354-45bc-9af5-07921d659ee1.png)


## 8. Branch 생성 후 push
![image](https://user-images.githubusercontent.com/18400730/181666936-aa2bb741-0853-4348-9a0c-fe807c146e78.png)
우선 git status로 현재 branch를 확인한다. 만일 On branch main인 경우에는, 
git checkout -b "이름/문제번호" 를 사용하여 브랜치를 생성한다.
git status로 브랜치를 확인하여 맞다면, git add 파일명을 통하여 파일을 스테이지로 올린다
git commit -m "Resolve #문제번호"로 커밋한다. 마무리로 git push origin 브랜치이름을 입력한다.

## 9. Pull request
![image](https://user-images.githubusercontent.com/18400730/181667471-0b442255-cb64-469c-8a26-fd40653f362d.png)
![image](https://user-images.githubusercontent.com/18400730/181667546-33973586-e969-4626-aa38-fea81ec80db8.png)
본인의 branch를 선택한 뒤, 내용을 작성한다
![image](https://user-images.githubusercontent.com/18400730/181667884-b0eea43c-8869-49e1-b954-de1c23bc6be6.png)
마무리로 Create pull request를 하면 끝!
