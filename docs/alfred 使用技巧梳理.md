# alfred 使用技巧梳理

## Workflows
### [super-solution-search](../workflows/super-solution-search.alfredworkflow)
> 一键打开多个搜索解决方案的网址。

![X8OOJt_S72IB2](https://cdn.byai.com/static/images/X8OOJt_S72IB2.png)

### [IP](https://github.com/zenorocha/alfred-workflows/)
> 快速查询本地ip 和公网出口 ip。`ifconfig` `ip a` 等命令还是不够方便。

公网IP地址查询方法，(特别是在服务器查询公网 ip 的时候需要用到)：

- `curl cip.cc`
- `curl ifconfig.me`
- `curl ipinfo.io`
- `curl https://ip.cn/api/index\?ip\=\&type\=0`
- `curl myip.ipip.net`

![Jdw8UC_sL5sQF](https://cdn.byai.com/static/images/Jdw8UC_sL5sQF.png)


### [HTTP](https://www.packal.org/workflow/http-status-codes)
![s04Fvq_ImY210](https://cdn.byai.com/static/images/s04Fvq_ImY210.png)

### [SwitchHosts](https://www.packal.org/workflow/switchhosts)

hosts 环境切换

![gb1A9z_qxJ8g1](https://cdn.byai.com/static/images/gb1A9z_qxJ8g1.png)


- https://www.packal.org/workflow-list


### [alfred-gitlab](https://github.com/lukewaite/alfred-gitlab)

> 输入 gl 一键搜索项目，快速跳转到指定的 gitlab 的 `Issues`、`Merge Request`、`Pipelines`、`Overview` 等。来源 [@双鱼](https://juejin.cn/user/307518985745895) 推荐。

![3f0qZX_fS8bzL](https://cdn.byai.com/static/images/3f0qZX_fS8bzL.png)
![olg85D_JtzYQb](https://cdn.byai.com/static/images/olg85D_JtzYQb.png)

### [CodeVar](https://github.com/xudaolong/CodeVar)
> 生成可用的代码变量，支持大驼峰dt、小驼峰xt、下划线xh、常量cl、中划线zh 等命名自动转换。程序员 👨🏻‍💻 写代码命名的神器。来源 [@双鱼](https://juejin.cn/user/307518985745895) 推荐。

![0K74Ww_BL459K](https://cdn.byai.com/static/images/0K74Ww_BL459K.png)

### [any-rule](https://github.com/cccyb/workflows)
![L6OPxP_lVBeM0](https://cdn.byai.com/static/images/L6OPxP_lVBeM0.jpg)


### [YoudaoTranslate | 有道翻译](https://github.com/wensonsmith/YoudaoTranslator)

> 快速使用有道翻译。

![MV4ZuK_bYAjU0](https://cdn.byai.com/static/images/MV4ZuK_bYAjU0.png)

### 商城
- https://www.alfredworkflows.store/workflows
- https://www.packal.org/workflow-search
- https://www.alfredapp.com/workflows/
- https://github.com/alfred-workflows/awesome-alfred-workflows

### 编写
- https://github.com/giangvo/alfred-workflow-nodejs
- https://github.com/sindresorhus/alfy

## Features
### Web Search
#### [Codelf](https://github.com/unbug/codelf/issues/63)

![kRIFwS_4YAgqR](https://cdn.byai.com/static/images/kRIFwS_4YAgqR.png)


#### 配置 google 搜索英文显示中文内容
> 来源 [@双鱼](https://juejin.cn/user/307518985745895) 推荐。

`https://www.google.co.jp/search?q={query}&hl=zh-CN`


![kVyyk3_9Nrt23](https://cdn.byai.com/static/images/kVyyk3_9Nrt23.png)

![O6r2z2_G4jFLW](https://cdn.byai.com/static/images/O6r2z2_G4jFLW.png)

- How to restrict a Google search to results of a specific language? https://webapps.stackexchange.com/questions/16047/how-to-restrict-a-google-search-to-results-of-a-specific-language


### 剪切板历史
强烈推荐的功能，对工作效率有很非常大的提升。支持图片、文字等历史记录复制。

### 支持终端切换
```bash
on alfred_script(q)
    tell application "iTerm"
        set _length to count window
    if _length = 0 then
        create window with default profile
    end if
    set aa to (get miniaturized of current window)
    if aa then
        set miniaturized of current window to false
    end if
    set bb to (get visible of current window)
    if bb is false then
        set visible of current window to true
    end if
    set cc to frontmost
    if cc is false then
        activate
    end if
        (*if _length = 0 then*)
            set theResult to current tab of current window
        (*else
            set theResult to (create tab with default profile) of current window
        end if*)
        write session of theResult text q
end tell#
end alfred_script
```

## FAQ
### 如何多电脑同步

`~/Library/Application Support/Alfred` 目录下的内容通过网盘或者仓库镜像同步。

### 电脑迁移到 M1 Workflows 出现报错如何处理
> 主要是一些依赖 `php` 的 `Workflows` 出现的报错，找不到 `/usr/local/php`。执行 `brew install php` 会出现报错，需要重新安装 `brew`， M1 对相关的目录进行了调整 `/opt/homebrew for Apple Silicon`。

![oJ77mD_x5ERQC](https://cdn.byai.com/static/images/oJ77mD_x5ERQC.jpg)