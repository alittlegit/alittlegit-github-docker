# hexo静态博客部署

## github静态博客

* github: https://github.com/alittlegit/alittlegit.github.io

* hexo搭建博客，本地发布文章测试

* hexo+github.io，将静态资源部署到github上，

* 访问: alittlegit.github.io 

* hexo初始及部署设置见:https://alittlegit.github.io/2019/12/13/hexo%E5%85%A5%E9%97%A8/

## hexo静态博客部署到服务器：hexo+express+webhook

* github: https://github.com/alittlegit/alitllegit-github-deploy

* 在服务器项目下克隆hexo的静态资源 git clone git@github.com:alittlegit/alittlegit.github.io.git public，命名文件夹为public，gitclone的目的方便后续直接git pull

* 服务器上需要新建一个server，托管静态资源即可，pm2管理

* 通过webhook持续集成：git上托管的的hexo资源一旦push,服务器自动pull，可以及时更新

* 访问： http://onepiece.suprise.top/

## hexo静态博客部署到服务器：hexo+express（docker）+webhook

* github: https://github.com/alittlegit/alitllegit-github-docker

* git clone静态资源，同上

* 新建一个pm2 docker容器，容器中开启node server

* webhook持续集成：git上托管的的hexo资源一旦push,服务器自动pull，自动重启docker,及时更新

* 访问： http://docker.suprise.top/

## workflow

* 本地hexo更新文章==>hexo deploy上传git，更新静态资源==>alittlegit.github.io 文章更新

* 本地hexo更新文章==>hexo deploy上传git，更新静态资源==>webhook==>服务器git pull==>http://onepiece.suprise.top/ 文章更新

* 本地hexo更新文章==>hexo deploy上传git，更新静态资源==>webhook==>服务器git pull+"resbulid docker"==>http://onepiece.suprise.top/ 文章更新

## 其他

* 服务器/docker/webhook分别使用一个端口，nginx转发，webhook是设置在项目的setting中的

* 注意docker build的路径，可以指定context,ADD/COPY 文件不能超出context