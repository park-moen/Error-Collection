# git push 실행시 발생하는 non-fast-forward 해결 방법

## Error 문구

![image](https://user-images.githubusercontent.com/57402711/124116231-ad7e5d00-daa9-11eb-99df-a1ea72816789.png)

- git push origin main 실행시 발생
- github repo를 만들면서 라이센스 및 README.md, .gitignore 파일을 미리 생성하면 발생하는 Error
- 미리 만든 프로젝트에 git remote add origin [GitHub repo 주소] 명령어를 사용하여 GitHub repo와 연동 중 발생 Error

## Error 원인

**깃허브에 생성된 원격 저장소와 로컬에 생성된 저장소 간 공통분모가 없는 상태에서 병합하려는 시도로 인해 발생. 기본적으로 관련 없는 두 저장소를 병합하는 것은 안되도록 설정되어 있습니다.**

- 새로 만든 GitHub repo에 미리 라이센스 및 README.md를 자동 생성 옵션을 선택하고 CRA로 Project를 만들게 되면 GitHub repo에 미리 만들어진 파일들과 CRA로 만든 파일들이 공통 분모가 없기때문에 Error가 발생
- 원인을 알았으니 해결 방법을 알아보겠습니다

## 해결 방법

1. git pull 시에 –allow-unrelated-histories 옵션 추가하여 관련 없었던 두 저장소를 병합하도록 허용
2. git push origin +main (강제적인 방식으로 추천하지 않습니다.)

```
git pull origin master --allow-unrelated-histories
```

## 참고 자료

[non-fast-forward 에러 해결하기](https://www.zehye.kr/git/2019/10/27/11git_push_error/)
