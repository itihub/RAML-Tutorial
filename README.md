# RAML-Tutorial
RestFul API 统一建模语言 （RESTful API Modeling Language）教程  

## 前言  
经历过一些没有文档的项目，前后端开发者坐到一起口口相传，或者有些团队用 word、pdf 来编写 API 文档。API 文档的缺乏给前后端协作带来困难，在缺乏专门工具的情况下，编写和维护文档是一件工作量巨大的事，人工处理也非常容易出错。  

## 前后端协作的方式  
### 基于注释的 API 文档

这是一种通过代码中注释生成 API 文档的轻量级方案，它的好处是简单易用，基本与编程语言无关。因为基于注释，非常适合动态语言的文档输出，例如 Nodejs、PHP、Python。由于NPM包容易安装和使用，这里推荐 nodejs 平台下的 apidocjs。

### 基于反射的 API 文档  

使用 swagger 这类通过反射来解析代码，只需要定义好 Model，可以实现自动输出 API 文档。这种方案适合强类型语言例如 Java、.Net，尤其是生成一份稳定、能在团队外使用的 API 文档。

### 使用契约进行前后端协作  

在团队内部，前后端协作本质上需要的不是一份 API 文档，而是一个可以供前后端共同遵守的契约。前后端可以一起制定一份契约，使用这份契约共同开发，前端使用这份契约 mock API，后端则可以通过它简单的验证API是否正确输出。

### 中心文档服务器  

使用一个集中地服务来存放这些文档，这个中心文档可以是文档在线编辑器也可以将构建出 HTML 文档然后每一次输出部署到一台静态服务器。  

## 契约  
## Design 设计
#### Atom 编辑器 + API Workbench插件
Atom安装  
```shell
# 使用包管理器安装
choco install -y atom
```
插件安装 
打开atom编辑器 File -> Settings -> Install   
搜索"api-workbench"安装  


#### API Designer (Web工具)  
API Designer是使用 Angular.JS 和 JavaScript 编写的RAML （RESTful API 建模语言）的独立/嵌入式编辑器。默认情况下，编辑器使用存储在 HTML5 Localstorage 中的浏览器内文件系统。  
安装及运行 
```shell
# 安装
npm install -g api-designer
# 运行
api-designer
```

  

## Build 构建  

## Test 测试  

## Document 文档
#### RAML2HTML  
简单的 RAML 到 HTML 文档生成器，为 Node.js 编写，具有主题支持  
安装   
    ```npm i -g raml2html```    
主题安装   
    ```npm i -g raml2html-markdown-theme```  
    ```npm i -g raml2html-slate-theme```  
    在 NPM 中搜索“raml2html-theme”关键字（或使用[此链接](https://www.npmjs.com/browse/keyword/raml2html-theme)）以查找更多主题。  
使用  
```shell
raml2html --help
# 使用默认主题
raml2html example.raml > example.html
# 指定主题
raml2html --theme raml2html-markdown-theme example.raml > example_markdown.html
raml2html --theme raml2html-slate-theme example.raml > example_slate.html
# 使用模板
raml2html --template my-custom-template.nunjucks -i example.raml -o example_template.html
```

## Share 共享  

## 契约文件的管理  

单独增加了一个管理契约文件的 git仓库，并使用 git 的submodule 来引用到各个涉及到了的代码仓库中(可以是提供者或者消费者)。

## 参考
- 教程：https://raml.org/developers/raml-100-tutorial
- 教程：https://raml.org/developers/raml-200-tutorial
- RAML1.0：https://github.com/raml-org/raml-spec/blob/master/versions/raml-10/raml-10.md
- RAML示例：https://github.com/raml-org/raml-examples/tree/master/others