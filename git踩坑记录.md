#### 首先说一下我们公司的git协作的流程

  1. develop , testing , master三条分支 
  2. 但是实际的情况是 : develop修改后, 提到自己派生的origin-develop, 然后再把origin-develop合并到root-develop
  3. 其实develop有很多人共同开发嘛, 然后大家都是开发前先拉去root-develop , 然后开发
  4. 最后提测, 就会有一个前端把root-develop合并到root-testing
  5. 然后呢, 产品或者测试会测root-testing的版本
  6. 当测试完毕, 会把root-testing合并到root-master
  
  
#### 这个时候, 是不是会发现 派生的testing和master都没有用上, 而且还会存在一个问题: 
      比如我们四个前端都在testing有提交a,b,c,d四个commit , 但是产品只需要其中一个commit 那么这个时候我们公司就会懵逼
      
      
      
#### 其次呢, 我们目前公司解决修复紧急bug的流程是 :
  
  1. 从origin-master拉去一条分支origin-bugfix的分支
  2. 然后只修改当前bug, 改好之后呢, 把origin-bugfix分支合并到root-master
  3. 最后呢, 不嫌麻烦的在把master分支向下合并到 testing , develop( 为什么我这里要说 `不嫌麻烦呢` ,因为我已经不止一次遇到同事嫌麻烦的没有向下合并, 从而导致代码冲突)
  4. 其实这个流程是非常麻烦的, 我一次也没有这样改过, 甚至同事也很少, 以为太容易冲突了, 谁愿意改完bug还去合几次代码呢
  

#### 那我这次碰到的问题是 :

  前言 : 首先是一个项目, 我已经有半年没有维护了, 但是产品找到我, 需要我协助改bug , 因为只改了1行代码, 所以我教同事修改后, 让同事提交到了root-testing分支, 
        此时root-testing分支上大概有4.5个提交, 产品突然只要我这一个提交上线
  
  接下来是我的操作: 
  
    1. 我先从root-develop 拉去代码到 origin-develop
    2. 从root-testing 拉去代码到 origin-testing / origin-master (骚操作, 拉完就后悔了)
    3. 所以现在我的origin-master就是最新的
    4. 接着, 我把需要改的那句代码从我的本地提交到我派生的仓库里面, 但是其他的没有上
    5. 此时我觉得我的仓库的origin-master的代码就是多了一句新代码
    6. 我合并origin-master到root-master, 我发现虽然文件修改只有1个, 但是代码提交有14条
    
    问题: 
    
    1. 当然我这次提交没有问题 , 但是如果下次又要上线, 同事去合并, 就会发现 没有代码需要更新, 因为我把`代码提交`合并了, 但是文件只合并了1个
    2. 回滚此次提交出现了问题
    
    
#### 问题2是怎么出现的？？
 
  1. 我把origin-root合并到origin-master上了， 那么我master上就有许多待合并的commit，这里可以理解成几个commit组成一个父级
  2. 我把父级中的某一个commit合并到root-master上， 所以这个一个大的commit，那么最后我自然不能回滚这次提交中的某一个提交了
  
  
 #### 那么，在我看来相对正确的git协作流程是
 
  1. root和origin都有develop , testing , master三条分支
  2. 开发在develop修改， 每一次commit都有一个版本号，用`git cherry-pick qwe12iheio12ex1`的方法合并到test， 依次上master
  3. 其次修复bug也是在develop的环境修改（可以新拉一个基于develop的分支），这样逐级合并到主线上，因为规范是从develop -> master
  4. 这样的好处是a.避免了不必要的代码冲突， b.不用从上至下的合并代码 ， c. 可以提交某一次代码到主线上
  
  
 #### git使用的几个小妙招
 
  1. 当我们的某一个分支实在乱到我们无从下手时， 我们可以基于root的某一条分支拉取下来， 然后再强推到origin上， 这样保证主线和我们自己的仓库是一致的
  
    ```
    // 本地新建一个分支develop，并切换到新建的分支develop，并且建立develop与远程分支root/develop的跟踪关系。
    git checkout -b develop root/develop 
    
    // 用本地分支覆盖仓库的分支
    git push -f origin develop
    ```
  
    
    
    
    
    
    
    
    
    
