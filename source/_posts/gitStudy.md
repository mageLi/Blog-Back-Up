---
title: gitStudy
date: 2018-10-11 22:25:55
tags:
---

Markdown指南：https://www.jianshu.com/p/q81RER

git windows安装教程：https://segmentfault.com/a/1190000011809698

git windows教程：https://www.youtube.com/watch?v=SWYqp7iY_Tc

git操作流程：https://www.jianshu.com/p/2dac87817d51

git视频教程：https://www.youtube.com/watch?v=LemSseuZB9I&t=15s

hexo搭建博客教程：https://juejin.im/post/5abcd2286fb9a028d66440ba

Typora使用手册： https://blog.csdn.net/sun13921881708/article/details/71159391

# Git Basics

* Git init

* git config -- global user.name "magli"

* git config -- global user.email "ltian5@stevens.edu"

* Git status 

* Git add

* Git commit

* git reset --hard HEAD~版本号 //回退版本 HEAD指向当前版本 //如果不写 HEAD就可以在版本里历史中穿梭（可能会出现退出不了的情况这个时候按q）   

* git reset --hard 版本号     //退回到一个版本（利用版本号）  

* Touch .gitignore (if you not want to include log.txt) input log.txt then save

  ​			(if you not want to include folder dir2) input /dir2 then save

  ​			(if you not want to include .txt) input *.txt then save

# Git Checkout

* Git Log

* Git Checkout

* git checkout -b feature1 //create a new branch

* git checkout master //Switched to branch 'master'

* (master) $ git merge feature1  //merge feature1 into master

* (feature1) $ git merge master

* git branch -d feature //Deleted branch feature1 (was 80f743f).

* git revert --no-commit 0766c053..HEAD

   HEAD
    O -> O -> O -> O
                   Master

# Cloning and Github Intro

* What is Github?
* Cloning an existing repo
* Git pull update the project

# Pushing to Github

* Creating a repo on github
* git remote add origin <% url %> //Adding a remote
* git push -u origin master //Pushing to github
* login in to GitHub