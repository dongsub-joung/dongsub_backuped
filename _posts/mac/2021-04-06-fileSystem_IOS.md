Title: About the iOS File System
tag: SE


> 아이폰의 파일 접근 권한 및 접근을 어떻게 해야 얻을 수 있는가? 부터 출발하는 파일 시스템  
> Mac OS에서의 파일은 하나가 완전한 파일로 구축되어 있어서 설치, 삭제가 편하다는 것(원터치?)만 알고 있었기에 궁금하기도 했다.  

## pre-Post
### About BASIC (HFS+, B-Tree)의 간략한 정리
* [Mac OS - DongSub_Joung’s Developer Life](https://dongsub-joung.github.io/2021/02/07/macOS.html)

- - - -

> the persistent storage of data files, apps, and the files associated with the operating system itself.   

영구적인 저장공간

## iOS Standard Directories
보안상의 목적으로 IOS 앱의 상호작용은 앱의 sandbox 디렉토리 내에서 제한되어 져 있다.
새로운 앱을 설치하는 동안에 인스톨러는 새로운 디렉토리 컨테이너를 만들고 각각의 컨테이너는 특별한 룰을 가진다.  아래의 그림을 참고하자.

![An IOS app operating within its own sandbox directory](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/art/ios_app_layout_2x.png)

앱은 일반적으로 accessing or creating files outside its container directories. 하는 것을 금지한다. (the system frameworks가 도움을 주는public system interfaces가 접근할 때는 예외)

- - - -

### bundle의 정의
* (실행가능한 코드를 묶어주는 그리고 자원과 연관되어있는) 파일 시스템 내의 directory이다.
* 예를 들자면 In iOS and OS X, applications, frameworks, plug-ins, and other types of software 등등
* 번들은 유저와 개발자에게 쉬운 설치 혹은 경로 바꾸기 혹은 다른 곳으로 이동시키기의 이점을 제공한다.
* Xcode projects의 대부분의 type들은 bundle을 생성함. 손수 빌드 할 수 도 있음.

![bundle: iPhoneOS, Mac OS X](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Art/bundle_2x.png)
**번들 내 포함 시킬 수 있는 것들** 
* executable code
*  images
* sounds
*  nib files
*  private frameworks and libraries
*  plug-ins
*  loadable bundles, or any other type of code or resource
*  + a runtime-configuration file called the information property list (Info.plist)

#### Accessing Bundle Resources
* a main bundle <= contains the application code
* 앱 실행 시에 코드를 찾고 즉시 필요한 자원을 메모리에 적재함. 그리고 동적으로 코드와 자원들을 로드함.

The  [NSBundle](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSBundle/Description.html#//apple_ref/occ/cl/NSBundle)  class and, for procedural code, the  [CFBundleRef](https://developer.apple.com/documentation/corefoundation/cfbundle)  opaque type of Core Foundation give your application the means to locate resources in a bundle. In Objective-C, you first must obtain an instance of NSBundle that corresponds to the physical bundle. To get an application’s main bundle, call the class method  [mainBundle](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSBundle/Description.html#//apple_ref/occ/clm/NSBundle/mainBundle) . Other NSBundle methods return paths to bundle resources when given a filename, extension, and (optionally) a bundle subdirectory. After you have a path to a resource, you can load it into memory using the appropriate class.

**Loadable Bundles**

- - - -

### subdirectories
#### AppName.app
* An App’s bundle. 수정할 수 없는 디렉토리, 대신 어느 자원에 대해서 읽기 전용으로 접근 가능.  참고 [Resource Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/LoadingResources/Introduction/Introduction.html#//apple_ref/doc/uid/10000051i) 
* iTunes or iCloud.에 백업 안됨.

#### Documents/ 
* User-generated content를 저장하는 디렉토리.
* 접근 가능한 유저를 선택할수 있는 파일을 저장할 수 있음. 

#### Documents/Inbox
* 너의 앱이 외부 속성에 의해서 열릴지를 결정하는 파일.
* 이 디렉토리에서 파일을 읽고, 삭제할 수 있지만 새로운 파일을 만들거나 존재하는 파일들을 수정할 수 없다.  
* iTunes and iCloud에 백업 가능 

#### Library/
* 유저 데이터 파일 이외에 가장 높은 레벨의 디렉토리.
* standard subdirectories의 파일을 추가할 수 있음 ( IOS 앱들은 일반적으로 Application Support and Caches subdirectories를 사용함.)
* iTunes and iCloud 백업 가능
* For additional information about the Library directory and its commonly used subdirectories, see  [The Library Directory Stores App-Specific Files](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html#//apple_ref/doc/uid/TP40010672-CH2-SW1) .

#### tmp/
앱 시작에 필요하지 않는 파일들을 임시적으로 보관하는데 쓰임.

> IOS app은 아마 추가적인 디렉토리를 만들꺼임. (in the Documents, Library, and tmp directories.)   

For information about how to get references to the preceding directories from your iOS app, see  [Locating Items in the Sta](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/AccessingFilesandDirectories/AccessingFilesandDirectories.html#//apple_ref/doc/uid/TP40010672-CH3-SW3) 

- - - -
### Where You Should Put Your App’s Files
* Put user data in Documents/. 
* Put app-created support files in the Library_Application support_ directory.
* Remember that files in Documents/ and Application Support/ are backed up by default.
* Put temporary data in the tmp/ directory. 
* Put data cache files in the Library_Caches_ directory. 


- - - -
## 참고 사이트
[Apple Developer - File System Programming Guide](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html)


## 다음 토픽: About the macOS File System
