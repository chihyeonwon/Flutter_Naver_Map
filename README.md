# map
```
flutter_naver_map 라이브러리의 사용법을 정리해보았습니다.
향후 프로젝트에서 네이버 맵에서 제공하는 주변 개방 화장실 찾기, 맛집 찾기 등
위치 기반 앱 프로젝트를 생성할 때 도움이 되는 라이브러리입니다.
```

### flutter_naver_map library 설치
```
pub.dev 에서 제공하는 flutter_naver_map 라이브러리르 설치합니다.
터미널에서 flutter pub add fltter_naver_map 명령어를 치고 패키지를 import합니다.
다른 개발문서의 라이브러리는 영어로 작성되어 있는 것이 일반적인 데 특이하게 한글로 되어있어
쉽게 개발할 수 있었습니다.
```

### 위치 기반 앱 권한 얻기
```
위치 기반 역시 개인정보에 민감한 정보로 개개인의 동의를 얻어야만 위치 정보에 접근할 수 있습니다.
따라서 접근과 관련된 권한을 설정해줍니다.

<manifest>
    <!-- 네이버 맵에서 현 위치 탐색 기능을 사용할 때만, 해당 권한 2개를 선언합니다 -->
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>

    <application>
        <activity> <!-- something --> </activity>
        
        <!-- 플러터 자동 생성. 지우시면 안 됩니다. -->
        <meta-data
            android:name="flutterEmbedding"
            android:value="2"/>
                
        <!-- 네이버 맵 SDK의 Client ID를 넣는 곳입니다. 필수로 넣어야, 지도가 동작합니다. -->        
        <meta-data
            android:name="com.naver.maps.map.CLIENT_ID"
            android:value="여기에 Map Sdk의 Client ID를 넣습니다" />
    </application>
</manifest>

여기서 Map Sdk의 Client ID를 얻는 방법을 알아보겠습니다.
```

### 네이버 클라우드 플랫폼에서 네이버 맵 API 얻기
```
https://www.ncloud.com/product/applicationService/maps에 접속해서 Maps 개발하고자 하는
분야를 모두 체크한뒤 안드로이드 앱의 패키지 이름을 입력하여 추가해주면 됩니다.
```
![image](https://user-images.githubusercontent.com/58906858/212531542-34751677-5231-4e04-a089-3ab0e6825080.png)

### 네이버 맵 API 클라이언트 ID 얻기
```
패키지 이름을 입력하고 Application을 등록하면 인증정보 버튼을 눌러서 클라이언트 ID를 얻을 수 있습니다.
이 클라이언트 ID는 보안상으로 중요한 역할을 하기 때문에 타인에게 노출되지 않도록 조심해야 합니다.
```
![image](https://user-images.githubusercontent.com/58906858/212531661-c593c7fc-aa3d-4304-95a1-f0891152bbba.png)

### 네이버 map 앱 실행하기
```
앱을 실행하면 다음과 같이 위치 정보 접근 권한을 요청합니다.
앱 사용중만 허용을 누르면 네이버 앱이 나옵니다. 하지만 실질적인 처음 위치 정보를 주지 않았기에
맵에는 반영되지 않았습니다. 다음 프로젝트에서 앱 위치 정보를 주고 활용해보겠습니다.
```
![image](https://user-images.githubusercontent.com/58906858/212533901-1e45839b-dd42-488a-bfc3-3a191ba30325.png)

