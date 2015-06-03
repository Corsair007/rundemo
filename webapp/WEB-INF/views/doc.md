### 概述

* * *
rundemo是一个基于`GitHub`和`Maven`的在线demo演示平台，您可将自己的demo项目上传至github上，通过仓库地址clone至服务器上，然后系统会自动展示你需要显示的包下的文件列表，点击各个文件可查看、修改和运行，运行结果可直接在页面显示。

### 主要功能

* * *
* **创建应用**  
	为您的demo起一个应用名称(是唯一的)，输入所在GitHub的仓库地址，包括一些可选项，如分支branch(默认为master分支)、pom文件所在目录(默认在主目录下，不在主目录下的需要填入相对路径)、需要显示的package(您可以选择显示指定包下的应用代码文件，默认显示/src/main/java/下所有包文件)以及maven的一些命令参数；例如有个guavaexample的项目在github的地址为：<https://github.com/Corsair007/guavaexample.git>，分支为master，pom文件在主目录下，需要显示`com/yeahmobi/rundemo/guavaexample`包下的代码文件。   
	
* **更新应用**   
	当您的demo代码有所更改并push至github上后，在不改变项目基本结构的前提下，在本系统点击"更新"后可将代码更新至本地。
* **代码文件显示**   
	代码文件以Annotation(`@rundemo_name`)后的功能描述命名并按树形列表层级显示，选中某个文件，右边Code View编辑框内就会显示对应代码。
* **demo运行**   
	代码显示后可以在线修改，并可立即运行，返回结果会显示在Run Result框内。

### 使用约定   

* * *
* **demo项目必须是maven项目，且目录结构如下图所示： **   
![](images/docImgs/project_org_1.jpg)   
* **约定demo项目的样例代码全部放在com.yeahmobi.rundemo.XXXexample包下面: **    
![](images/docImgs/project_org_2.jpg)   
大家可以按上述约定上传自己的demo项目，也可以在github上建立现有demo的分支，在`com.yeahmobi.rundemo.XXXexample`包下修改、添加demo，提交代码后，在rundemo上更新相应的应用。

### 系统入口   

* * *
* **测试环境**  
	<http://localhost:9090/rundemo/>    
	用户进入系统后，首页会展示系统现有的所有应用：
![](images/docImgs/home.jpg)

### 创建应用   

* * *
**1. 用户点击【创建应用】按钮后，会弹出一个如下所示的模态框：**  
![](images/docImgs/createappform.jpg)
* 其中“应用名称”：唯一的，重复会给予提示；
* “Git仓库的URL”：即demo所在github地址，以上两项是必填的；
* “分支”：想查看的demo所在分支，默认为master分支；
* “pom文件所在目录”：根据demo的实际目录结构，填写pom文件所在的相对路径，如果pom文件在项目的根目录下则可不填；
* “显示的package”：只显示你想查看或显示的包下的代码文件，可填写该项为`com/yeahmobi/rundemo/XXXexample`，默认显示`src/mian/java`包下的所有子包和代码文件;
* “maven命令参数”：系统后台会根据pom文件使用mvn命令来生成classpath，也可以在这里加一些控制参数，如-DdownloadSources等;   
 
**2. 点击【创建】后，后台需要一些处理时间，会弹出等待提示框：**   
![](images/docImgs/createwait.jpg)

### 应用主页面   

* * *
* 后台处理完后，会跳转到该应用的主页面：   
![](images/docImgs/apphome1.jpg)  
![](images/docImgs/apphome2.jpg)
* 导航条上会高亮当前所展示的应用名称(这里是guavaexample)，点击【所有应用】将返回首页，右边显示该项目在github上的地址，用户可以建立分支修改和完善demo；  
* 导航条下是三个Tab页，分别显示项目的java文件、resource文件以及pom文件,其中java	Tab页下左边显示的是`com/yeahmobi/rundemo/guavaexample`包下的所有代码文件，如果在创建应用时没有填写“显示的package”这一项，这里将显示`src/main/java`右边Code View部分显示左边选中的代码文件内容，用户可以查看修改代码；   
* 点击【Run】按钮，会运行Code View所显示的代码，并将执行结果显示在Run Result方框里。  
* 左边java文件所显示的名称是根据代码所实现的功能来命名的，从代码中的@rundemo_name处获取。   
   
   
**Pom.xml Tab页：**  
    
![](images/docImgs/pom.jpg)  
  
**Resource Tab页：**   
   
![](images/docImgs/resource.jpg)

### 更新应用   

* * *
![](images/docImgs/nav.jpg)   

* 点击导航条上右边的【更新】，系统会自动从github上更新代码至本地，页面会弹出等待提示框：   
![](images/docImgs/updatewait.jpg)   
* 后台处理完毕后会跳转到该应用的主页面。
