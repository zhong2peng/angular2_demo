# 1、搭建开发环境
## node.js的安装
    请在官网下载v6.x版本的安装包，angular2的脚手架工具中有些包在高版本中无法安装，如Karma，且低版本对开发者来说更加友好。虚拟桌面中使用的是v6.11.5版本。
    npm的配置更改，打开cmd命令工具：
    npm config set prefix "P:\Program Files\nodejs\X64\node_global"
    npm config set cache "P:\Program Files\nodejs\X64\node_cache"
    设置完之后，可在C:\Users\系统的登陆用户\下找到.npmrc文件，后期可以直接更改文件内容配置npm的参数
## 开发软件的选择
    vscode、sublime、webstorm等编辑器,推荐使用vscode，比较轻量，微软开发的，对typescript支持较好，有丰富的插件。
    vscode中，做angular2开发必备的插件：
    Angular Files ：在vsc中集成angular-cli工具，可界面华新建component、directove、module、routing、pipe等feature
    Auto Import：&nbsp; 自动引入模块
    Auto Rename Tag ： html的开始和结束标签同时更新
    beautify: 代码格式化工具
    vscode-icons: 图标美化工具
## angular脚手架的安装
    本地电脑上的安装
    npm install -g cnpm --registry=https://registry.npm.taobao.org
    cnpm install -g @angular/cli@latest
    说明：
    1、使用淘宝的镜像源是由于node-sass资源被墙了，且用npm安装node-sass需要编译，这个过程容易出现问题，而cnpm安装不会出现此类问题，它每10分钟会与官方同步一次。
    2、如果使用cnpm安装依然导致node-sass失败，请重新安装一下cnpm，如果cnpm的版本不是最新版本，而@angular/cli做了更新，可能会导致node-sass安装失败。
    虚拟桌面上的安装
    install -g @angular/cli@latest  --registry=http://rdsource.tp-link.net:4873&nbsp; #网络管理课提供的代理服务器
    说明：
    1、在虚拟桌面上使用cnpm，会报错Error: EPERM: operation not permitted, symlink，未解决。
    2、虚拟桌面的网络传输和磁盘写入比本地电脑要慢的多，若直接使用淘宝镜像，可能会卡住，无法看到响应。使用我司代理服务器，网络传输可以得到保障，虽然写入很慢，这个过程中请不要对文件进行操作，电脑可能会卡顿，但最终也能下载完毕，下班后运行命令，第二天就能愉快的使用了。
## rimraf的安装
    npm包管理器下载的依赖库，目录结构比较深，在windows必须借助此工具才能删除一些文件
    npm install -g rimraf 
    rimraf dirname 
# 2、npm包管理器的常用命令
    npm install --save : 产品模式需要使用的第三方库，放置在package.json的dependencies中
    npm install --save-dev：开发模式需要使用的第三方库，放置package.json的devDependencie中，一般安装测试使用的第三方库
    npm config list -l : 查看npm的配置
    npm list -g --depth 0: 查看全局环境下安装第一层级的包，如果有包安装失败，会报错，用命令行卸载重新安装
    npm uninstall : 卸载命令
    npm info @angular/cli: 查看包的发布版本信息，这里查看@angular/cli的版本信息
    npm install @angular/cli@1.4.9: 根据查询的版本信息，可以选择安装某一版本的包
    npm install @angular/cli@latest ： 安装最新的包
    npm cache clean：清除缓存，若报错选择用管理员身份打开cmd工具再执行。
# 3、@angular/cli常用命令
# 4、第三方库的引进 
    angular2底层使用的typescript语法，它会无法识别常见的javascript的语法，如jquery.js，它不会识别$('')操作符。 
    需要安装模块： 
    npm install --save jquery 
    npm install --save @types/jquery 
    有一个叫.d.ts的声明文件，详情请参考官网http://definitelytyped.org/ ，汇集了很多线程的类库的第三方.d.ts的声明文件提供我们下载
    如果官网并未提供.d.ts声明文件的类库，请手动添加：
    interface JQueryStatic{
       trim(str:string):string;
    }
    declare var $:JqueryStatic;
    将变量$定义成类型JQueryStatic，TS编译器在遇到$时会去找该类型，并且只能使用$.trim()，其中只定义了一个接口。Jquery有许多接口，采用declare var $:any;就可以了。 
    引入第三方库的3种方案： 
    1、直接在index.html中引入
    2、直接在style.css中引入 
    3、在脚手架配置中引入
# 5、学习资料汇总 
    ui框架：
# 6、自动化测试与集成测试
