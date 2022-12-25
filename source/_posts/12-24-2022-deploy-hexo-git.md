---
title: Deploy Hexo to Github
date: 2022-12-24 01:06:20
tags:
---

Edit file ```_config.yml```

```yml
deploy:
  type: 'git'
  repo: 'https://github.com/jhin1m/jhin1m.github.io'
```

Install plugin **hexo-deployer-git**

```bash
npm install hexo-deployer-git -save
```

Then run command:
```bash
hexo generate

hexo deploy
```