---
title: "如何用Hugo搭建个人博客"
date: 2019-11-10T12:55:30+08:00
draft: false
---

# 安装
1. 在Mac上
   在Mac上安装hugo非常方便，仅需要两个命令就可以完成
   ```
   brew install hugo
   ```
   验证hugo的安装是否成功
   ```
   hugo version
   ```
2. 在Windows上
   * 去[Hugo release页面](https://github.com/gohugoio/hugo/releases)下载hugo_xxx_Windows-64bit.zip
   * 解压，把hugo.exe放到D:\Software\hugo\hugo.exe
   * 把D:\Software\hugo\加到PATH中
   * 重启终端，运行hugo version查看版本
  

# 快速搭建博客
1. 进入[Hugo](https://gohugo.io/)官网，点击Quick Start
2. 从Step 2到Step 7按照网页上的内容依次操作
3. 操作完毕后会得到一个public目录，这就是我们的博客站点
4. 创建.gitignore文件，在文件内写入/public/           
   (注：讲public与hugo的内容分离，上传到两个分支)
5. 进入目录操作 (注：将public上传到本地的git仓库)
   * cd public(进入public目录中) 
   * git init 
   * git add .
   * git commit
   
   


6. 在GitHub中创建一个仓库，名为(用户名).github.io
   
   * 例如：Gy-coder.github.io

7. 远程提交: (注：确保cd的是public，因为只上传public到.github,io仓库中)
  
  * git remote add origin (你的SSH地址)
   
  * git push -u origin master

   

8. 点击 setting，找到GitHub Pages，然后点击链接就可以看到blog的内容了
   
  ![](/static/images/1.png)

# 备份 
1. 在GitHub中创建名为(你的用户名)。github.io-creator的仓库


2. cd进入你的hugo目录中
   

3. * git add
   * git commit
   * git remote add origin (你的SSH地址)
   * git push -u origin master
4. 如果出现
   
     warning: adding embedded git repository
   
     则说明在hugo的子目录中也存在一个.git

     解决方法 :删除提示的路径中的.git 再次提交即可。


以上就是用Hugo搭建个人博客的方法，小伙伴们可以大胆去尝试一下喔。


   





