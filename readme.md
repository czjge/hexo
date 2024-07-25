`hexo` 是基于 `node.js` 的博客系统

#### 一般用法
```shell
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

#### 新建文章
```shell
hexo new 这是文章标题
```

#### 重新渲染
```shell
hexo g
```

#### git 部署
```shell
git clone git@github.com:czjge/hexo.git blog.czjge.cn
cd blog.czjge.cn
npm install
hexo g
```

#### nginx 代理
根目录需指向 `/blog.czjge.cn/public`

#### 参考
https://hexo.io/zh-cn/