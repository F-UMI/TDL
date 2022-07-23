# GitHub 사용법 <small> edit by Yun</small>

## 1. GitHub?
***
> 소스코드의 효과적 관리를 위해 개발된 **'분산형 버전 관리 시스템'**

#### Why Use?

코드를 버전 관리함으로써 **배포후 발생한 버그가 발생시 빠르게 rollback 하거나 수정된 코드만을 파악하여   
버그를 빠르 게 찾거나, 한프로젝트의 코드를 여러사람이 함께 작업 할 수 있도록 도와주는** 다양한 이점을 얻을 수 있다.

* ### Git Repositories <small>(저장소)</small>

> `개발자가 개발한 코드 / 파일 / 디렉토리를 저장하는 장소`
>
> 변경이력을 관리하고자하는 디렉토리등을 저장소에 관리할수 있도록 함으로서 해당 디렉토리의 파일등의 변경내용의 기록이 가능해진다.
> 1. #### 원격 저장소(Remote Repository)
> 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
>
>  ```gitignore
>      원격 저장소에 연결 : $ git remote add origin (원격 저장소 github URL)
> ```
>
>
>
>2. #### 로컬 저장소(Local Repository)
    >   내 PC 파일에 저장되는 개인 저장소
    >
    >   ```gitignore
>      폴더 생성 - $ mkdir "폴더 이름"
>      폴더 들어가기 - $ cd "폴더 이름"
>      Repository 생성 - $ git init  (.git 파일 생성)
>   ```


* ### Commit<small> (가지)</small>

> `파일의 및 폴더의 추가/ 변경 사항을 기록하는 메세지`
>
> 각 Commit 에는 각각의 40자 고유 이름이 붙는다.   
> 이를 이용하여 버그 수정 | 기능 추가 등 소스코드와 프로젝트에 특별한 의미가 있는 업데이트를     
> 작업별로 구분해서 Commit 작성시 이력을 통하여 특정 변경 이력을 찾기 쉽다.
>> *  #### Commit Message의 규칙
>>1. 제목과 본문을 빈 행으로 구분한다
>>2. 제목을 50글자 내로 제한
>>3. 제목 첫글자는 대문자로 작성
>>4. 제목 끝에 마침표 넣지 않기
>>5. 제목은 명령문으로 사용하며 과거형을 사용하지 않는다
>>6. 본문의 각 행은 72글자 내로 제한
>>7. 어떻게 보다는 무엇과 왜를 설명한다
>>
>>
>>`feat : 새로운 기능에 대한 커밋`   
>> ` fix : 버그 수정에 대한 커밋`  
>> ` build : 빌드 관련 파일 수정에 대한 커밋`  
>> ` chore : 그 외 자잘한 수정에 대한 커밋`  
>> ` ci : CI관련 설정 수정에 대한 커밋`  
>> ` docs : 문서 수정에 대한 커밋`  
>> ` style : 코드 스타일 혹은 포맷 등에 관한 커밋`  
>> ` refactor :  코드 리팩토링에 대한 커밋`  
>> ` test : 테스트 코드 수정에 대한 커밋`
>   ```gitignore
> git commit -m "commit 할 내용"
>   ```



* ### 작업트리(Work Tree) & 인덱스(index)
>`작업트리 : 생성한 폴더  / 인덱스 : 커밋을 실행하기 전에 저장소와 작업 트리 사이에 존재하는 공간`
>
> 커밋은 인덱스에 파일 상태를 **기록<small>**(staging)</small> 하여야 한다.  
> ex) IntelliJ 에서 왼쪽 바에서 commit 시 PUSH할 파일을 선택하게 되는데 이것이 **스테이징**이라 볼 수 있다.
>   ```gitignore
> git add  .(현재 디렉토리에 있는 업데이트된 파일) || git add -A (수정된 파일 모두)
>   ```


* ### PUSH
>`내 PC의 로컬 저장소에서 변경된 이력을 원격 저장소에 공유하기 위하여 로컬 저장소의 변경 이력을 원격 저장소에 업로드 하는것`
>
> 이작업을 통해 원격 저장소(Remote Repository)와 로컬 저장소(Local Repository)가 동기화 되어 동일한 상태가 된다.
>   ```gitignore
>       $ git push origin master
>   ```


* ### CLONE
>`누군가 의 변경이력이 저장된 원격 저장소(Remote Repository)를 로컬 저장소(Local Repository)에 복제해놓는 것.`
>
> <small>변경이력 또한 clone 되어 넘어온다.</small>
>   ```gitignore
>       $ git clone <git 저장소의 URL>
>   ```
>

* ### PULL
>`공유된 Remote Repository 에 다른 사람들이 PUSH 해놓은 변경 사항을 Local Repository 에도 적용 시키는 것`
>
>    ```gitignore
>       $ git pull 
>   ```

* ### Branch
>`Commit 사이를 가볍게 이동할 수 있는 어떤 포인터 같은 것 || 하나의 작업 흐름에서 작업을 분기하는 기능`
>
> 기술적으로든 업무적으로든 실험적이거나 불확실한 작업을, 안정적인 오리지날 소스에서 따로 진행하고자 할 때 사용
> * #### 원리
    >  `$ git init` 시 생성되는 HEAD 파일이 생성되는데 refs/heads 디렉토리에 있는 branch 주소를 가지고 있는 파일을 참조한다.
    >
    >    ```gitignore
>      branch 확인 : $ git branch
>      branch 생성 : $ git branch "branch 이름"
>      branch 변경 : $ git checkout "branch 이름"
>      branch push : $ git push origin "branch 이름"
> 

* ### Merge
>
>`작업이 완료된 여러개의 commit을 하나로 모으는 것`
>
>>* #### fast-forward
>> 뿌리가 되는 branch가 변화가 주어지지 않을 채 다른 변화가 생긴 branch로 merge를 하게 되는것
>>* #### fast-forward가 아닌것
>> 새로운 commit 을 생성해 그곳으로 merge하게 된다.
>* #### 충돌?
   > 각 branch에서 같은 파일의 이름으로 그 내용이 상이한데 merge 를 시도 할 경우   
   > -->  3way merge<sup>[1](#footnote_1)</sup> 실행   
   > <small><a name="footnote_1">1</a>:
  > base의 내용을 참고 / 2. 한 branch 파일만 바뀐경우 바뀐쪽으로 변경 / 3. 두개다 변경이 없을 경우 base 의 내용을 따름</small>
   >    ```gitignore
>      merge: $ git merge "합병을 원하는 브랜치 이름" (실행 branch를 병합될 브랜치(main..) 으로 설정해야한다.)
>   ```

* ### PULL REQUEST
>`프로젝트 관리자에게 사용자가 작업한 코드를 담은 Branch를 검토후 병합(Merge) 해달라고 요청하는 것`
>
>* #### 순서
>1. Fork : Upstream Repository를 자신의 저장소로 Fork(Origin Repository)한다.
>2. Clone
>3. Local Repository 에  Upstream Repository 을 추가한다.   
    >   `$git remote add post(별명) (URL)`
>4. branch 생성 : $git checkout -b "branch이름"
>5. 수정 작업후 add / commit / push (origin)  
    `$ git push origin develop *(push 할때 수정내역을 origin으로 push)`
>6. Pull Request 생성 : github 저장소에서 Compare & pull request 버튼 선택및 생성  
    >7.Merge Pull Request : 관리자의 Merge여부 결정   
    >8.Merge 이후 동기화 및 branch 삭제 : Merge 완료시 로컬과 원본코드 병합, 동기화 실시   
    ` $ git remote -v (upstream 확인)`

