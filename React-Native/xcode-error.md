<!-- # Iterm에서 react-native 빌드 중 Xcode Build Error 발생

![image](https://user-images.githubusercontent.com/57402711/123085272-ffe1cd00-d45c-11eb-8cb1-f9a279e86311.png)
![image](https://user-images.githubusercontent.com/57402711/123085571-59e29280-d45d-11eb-87da-5affb7413fa7.png)
![image](https://user-images.githubusercontent.com/57402711/123086604-9236a080-d45e-11eb-91ac-872ef625355f.png)
![image](https://user-images.githubusercontent.com/57402711/123087525-9f07c400-d45f-11eb-9614-028b7aea6724.png)
![image](https://user-images.githubusercontent.com/57402711/123087901-0cb3f000-d460-11eb-85fa-2df2195165f2.png) -->

# Iterm에서 react-native 빌드 중 Xcode Build Error 발생

<br />

## Build Error

![image](https://user-images.githubusercontent.com/57402711/123085272-ffe1cd00-d45c-11eb-8cb1-f9a279e86311.png)
![image](https://user-images.githubusercontent.com/57402711/123085571-59e29280-d45d-11eb-87da-5affb7413fa7.png)

터미널에서 빌드 (npm run ios) 후 Xcode에 error: The sandbox is not in sync with the Podfile.lock. Run 'pod install' or update your CocoaPods installation. Error 문구가 보입니다.

<br />

## 해결책

### 1단계

```
npm pod-install ios // 터미널에 npm pod-install 실행
```

![image](https://user-images.githubusercontent.com/57402711/123086604-9236a080-d45e-11eb-91ac-872ef625355f.png)

[프로젝트명] 파일이 존재하지 않는다는 Error 문구가 보입니다.

### 2단계

1. [파일명].jsbundle 파일 또는 폴더가 존재하지 않기때문에 발생한 에러입니다.
2. Xocde를 직접 실행시킵니다.
   - Open a project or file을 클릭
   - ios 폴더 안의 [프로젝트명] 폴더 선택

<img src="https://user-images.githubusercontent.com/57402711/123087525-9f07c400-d45f-11eb-9614-028b7aea6724.png" alt="image" style="zoom:33%;" />

3. [프로젝트명] 폴더에 빨간색으로 표시된 파일을 찾습니다.

   <img src="https://user-images.githubusercontent.com/57402711/123087901-0cb3f000-d460-11eb-85fa-2df2195165f2.png" alt="image" style="zoom:67%;" />

4. 찾은 파일을 delete 하고 Xcode를 종료합니다.

5. 다시 npm run ios를 실행하면 정상적으로 react-native가 build를 진행합니다.

### 문제 발생 원인

- Xcode 10 Version 이상에서는 사용하지 않는 파일을 일부 삭제 시키면서 기존에 사용하는 파일에 손상이 발생해서 생기는 문제입니다.

<br />

## 참고자료

[stack overflow](https://stackoverflow.com/questions/21366549/error-the-sandbox-is-not-in-sync-with-the-podfile-lock-after-installing-re)

[stack overflow](https://stackoverflow.com/questions/10167442/whats-the-xcode-no-such-file-or-directory-error)
