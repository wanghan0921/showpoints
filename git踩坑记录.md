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
    
    
    
    
    
    
    
    
    
    
