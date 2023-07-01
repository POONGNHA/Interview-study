
 -----------------------------------------------------------------------------------------------------------------------------------
 - 😧:에러 종류 :: 권한 에러
------------------------------------------------------------------------------------------------------------------------------------
 - 에러 내용 :: 
PS C:\Develops\vue3_example> vue create vuedongsan
vue : 이 시스템에서 스크립트를 실행할 수 없으므로 C:\Users\sss96\AppData\Roaming\npm\vue.ps1 파일을 로드할 수 없습니다. 자세한 내용은 about_Execution_Policies(https://go.microsoft.com/fwlink/?LinkID=135170)를 참조하십시
오.
위치 줄:1 문자:1
+ vue create vuedongsan
+ ~~~
    + CategoryInfo          : 보안 오류: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
-------------------------------------------------------------------------------------------------------------------------------------
- 에러 해결 ::
(참조 페이지)[https://hellcoding.tistory.com/entry/VSCode-%EC%98%A4%EB%A5%98-%EC%9D%B4-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%97%90%EC%84%9C-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%A0-%EC%88%98-%EC%97%86%EC%9C%BC%EB%AF%80%EB%A1%9C]
cmd-powershell에서 권한을 Restricted에서 RemoteSighed로 변경해주면 스크립트 허용이 가능하게 된다.
즉 시스템에서 스크립트를 실행할 수 있도록 권한을 부여해주면 된다.

--------------------------------------------------------------------------------------------------------------------------------------


 -----------------------------------------------------------------------------------------------------------------------------------
 - 😧:에러 종류 :: v-for 에러
------------------------------------------------------------------------------------------------------------------------------------
 - 에러 내용 :: 
C:\Develops\vuedongsan\src\App.vue
  5:5  error  Elements in iteration expect to have 'v-bind:key' directives  vue/require-v-for-key
  8:5  error  Elements in iteration expect to have 'v-bind:key' directives  vue/require-v-for-key

 ## Q1. 왜 array를 불러오는데 key값 binding을 안해주면 오류를 뱉는지가 궁금했음
 생각해보면 index만 존재하는 arr형식에 key값 바인딩을 안해주면 안되는 이유가 없을텐데 오류가 뱉어지니 이상해서 찾아봄

-------------------------------------------------------------------------------------------------------------------------------------
- 에러 해결 ::
(참조 페이지)[[https://hellcoding.tistory.com/entry/VSCode-%EC%98%A4%EB%A5%98-%EC%9D%B4-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%97%90%EC%84%9C-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%A0-%EC%88%98-%EC%97%86%EC%9C%BC%EB%AF%80%EB%A1%9C](https://vuejs.org/api/built-in-directives.html#v-for)]
<templet>에서  <h4>{{ roomNames }} 원룸</h4> 코드를 넣고
<script>태그에서 
 data() {
    return {
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      price: [50, 60, 70],
    };
  }
 위 코드와 같이 넣어주었는데 동작이 되지 않았다.
  vue api 문서를 살펴본 결과 alias가 특별하게 설정이 되어있어야 한다고 나와있었다.

  혁준이(개발자친구)에게 물어보니 vue는 rendering을 할 때 (vue가 rendering 특징을 가지고있어 반응형 web을 만들기때문)
  그 key값을 가지고있어야 rendering의 조건을 충족시킨다는 이야기를 전해들었다.
   즉 v-bind:key를 넣어줘야 오류가 없다는 말.

--------------------------------------------------------------------------------------------------------------------------------------
