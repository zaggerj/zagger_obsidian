---
tags:
  - 教程/obsidian/清单
  - obsidian
aliases:
  - obsidian指南
---

## ✍ 内容

```dataviewjs
dv.table(
 [ "feild", "value", "path", "url"],
 dv.pages("#教程/obsidian/清单").file.lists
 .where(l => l.type)
 .sort(l => l.type, "desc")
 .map(l =>  {
  const [type, typeValue] = l.type.split("-")
  return [type, typeValue, l.path, l.url]
 })
)
```

# Obsidian 同步仓库

![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108132000.png)

1. [Obsidian 主题常见问题 (pkmer.cn)][https://pkmer.cn/Pkmer-Docs/10-obsidian/obsidian%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E6%B1%87%E6%80%BB/obsidian%E4%B8%BB%E9%A2%98%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98/][url::https://pkmer.cn/Pkmer-Docs/10-obsidian/obsidian%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E6%B1%87%E6%80%BB/obsidian%E4%B8%BB%E9%A2%98%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98/]
[type::blog-pkmer.cn]
2. [zaggerj/zagger_obsidian at 1.0.0 (github.com)][https://github.com/zaggerj/zagger_obsidian/tree/1.0.0][url::https://github.com/zaggerj/zagger_obsidian/tree/1.0.0]
[type::repo-github]
3. [zagger_obsidian: obsidian 个人仓库备份 - Gitee.com](https://gitee.com/zaggerzj/zagger_obsidian/tree/1.0.0/) [url::https://gitee.com/zaggerzj/zagger_obsidian/tree/1.0.0/][type::repo-gitee]
4. 日报，周计划模板[[ Obsidian ] 模板分享：自动化动态创建日程表 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv23768479/][url::https://www.bilibili.com/read/cv23768479/]
[type::blog-bilibili.com]
5. [tp.file - Templater --- tp.file - 模板程序 (silentvoid13.github.io)][https://silentvoid13.github.io/Templater/internal-functions/internal-modules/file-module.html#tpfilefind_tfilefilename-string][url::https://silentvoid13.github.io/Templater/internal-functions/internal-modules/file-module.html#tpfilefind_tfilefilename-string](office:: tp)
6. [blacksmithgu/obsidian-dataview: A high-performance data index and query language over Markdown files, for https://obsidian.md/. (github.com)][https://github.com/blacksmithgu/obsidian-dataview][url::https://github.com/blacksmithgu/obsidian-dataview](office:: dv)
7. [SilentVoid13/Templater: A template plugin for obsidian (github.com)][https://github.com/SilentVoid13/Templater][url::https://github.com/SilentVoid13/Templater](type::offcial- tp github)
8. [Obsidian-Template-DynamicSchedule: Obsidian 动态日程模板 (gitee.com)][https://gitee.com/goblincwl/Obsidian-Template-DynamicSchedule][url::https://gitee.com/goblincwl/Obsidian-Template-DynamicSchedule]
[type::blog-bilibili.com]
9. [Obsidian 极简日记配置教程 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv21481911/][url::https://www.bilibili.com/read/cv21481911/]
[type::blog-bilibili.com]
10. [作为 Ob 玩家，不得不知的 24 个 Obsidian 使用技巧 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv18547773/][url::https://www.bilibili.com/read/cv18547773/]
[type::blog-bilibili.com]
11. [Obsidian 多端同步之 win to ios&ipados - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv18681675/][url::https://www.bilibili.com/read/cv18681675/]
[type::blog-bilibili.com]
12. [不懂 CSS，一样可以 DIY 出自己喜欢的 Obsidian 主题 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv19043175/][url::https://www.bilibili.com/read/cv19043175/]
[type::blog-bilibili.com]
13. [Obsidian | Ob 中真正的 Notion Database 功能，配置极简，体验极佳 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv19518130/][url::https://www.bilibili.com/read/cv19518130/]
[type::blog-bilibili.com]
14. [Obsidian | 说好不用 Ob 做日程管理的，这次我又“食言”了 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv19526990/][url::https://www.bilibili.com/read/cv19526990/]
[type::blog-bilibili.com]
15. [Obsidian 白板&一个白板插件 - 哔哩哔哩 (bilibili.com)][https://www.bilibili.com/read/cv20661353/][url::https://www.bilibili.com/read/cv20661353/]
[type::blog-bilibili.com]
16. [维客笔记博客-维客笔记专栏文章-文集-哔哩哔哩视频 (bilibili.com)][https://space.bilibili.com/305034274/article][url::https://space.bilibili.com/305034274/article]
[type::blog-bilibili.com]
17. [PKM-er/Blue-topaz-example: Blue topaz themes example vault for Obsidian (github.com)][https://github.com/PKM-er/Blue-topaz-example][url::https://github.com/PKM-er/Blue-topaz-example]
[type::blog-bilibili.com]
18. [zagger129/Obsidian-Homepage: A dashboard for your obsidian vault. (github.com)][https://github.com/zagger129/Obsidian-Homepage][url::https://github.com/zagger129/Obsidian-Homepage]
[type::repo-github]
19. [大家一直想要的项目、论文状态追踪管理效率模板来了 (qq.com)][https://mp.weixin.qq.com/s?__biz=MzI4NDQ4NjU0MA==&mid=2247751446&idx=1&sn=aa6012807e4744e4ae393a57b91982da&chksm=ebf7e9f5dc8060e3063e6ac403a13e4989ac564f3e0959dc9ba990feae657572deb273323cb6&scene=27][url::https://mp.weixin.qq.com/s?__biz=MzI4NDQ4NjU0MA==&mid=2247751446&idx=1&sn=aa6012807e4744e4ae393a57b91982da&chksm=ebf7e9f5dc8060e3063e6ac403a13e4989ac564f3e0959dc9ba990feae657572deb273323cb6&scene=27]
[type::blog-qq.com]
20. [#科研工具/神器 (qq.com)][https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI4NDQ4NjU0MA==&action=getalbum&album_id=1500675956766736385&scene=173&from_msgid=2247751446&from_itemidx=1&count=3&nolastread=1#wechat_redirect][url::https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI4NDQ4NjU0MA==&action=getalbum&album_id=1500675956766736385&scene=173&from_msgid=2247751446&from_itemidx=1&count=3&nolastread=1#wechat_redirect]
[type::blog-qq.com]
21. [#科研笔记神器 (qq.com)][https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI4NDQ4NjU0MA==&action=getalbum&album_id=2336961249412284416&scene=173&from_msgid=2247751446&from_itemidx=1&count=3&nolastread=1#wechat_redirect][url::https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI4NDQ4NjU0MA==&action=getalbum&album_id=2336961249412284416&scene=173&from_msgid=2247751446&from_itemidx=1&count=3&nolastread=1#wechat_redirect]
[type::blog-qq.com]
22. [用 Obsidian 管理 23 只鸟 - 知乎 (zhihu.com)][https://zhuanlan.zhihu.com/p/486882929][url::https://zhuanlan.zhihu.com/p/486882929]
[type::blog-zhihu.com]
23. [obsidian 插件 文章标注 booknote\_哔哩哔哩\_bilibili][https://www.bilibili.com/video/BV1JW4y1e7Xv/?spm_id_from=pageDriver&vd_source=af94dc11f0a1751ebb3c2090844ad9f6][url::https://www.bilibili.com/video/BV1JW4y1e7Xv/?spm_id_from=pageDriver&vd_source=af94dc11f0a1751ebb3c2090844ad9f6]
[type::blog-bilibili.com]
24. [PKM-er/Blue-topaz-example: Blue topaz themes example vault for Obsidian (github.com)][https://github.com/PKM-er/Blue-topaz-example/tree/main][url::https://github.com/PKM-er/Blue-topaz-example/tree/main]
[type::repo-github]
25. [Obsidian 自动化套用模板与存放笔记 - 知乎 (zhihu.com)][https://zhuanlan.zhihu.com/p/544827131][url::https://zhuanlan.zhihu.com/p/544827131]
[type::blog-zhihu.com]
26. [Dataviewjs 的奇技淫巧 - 经验分享 - Obsidian 中文论坛][https://forum-zh.obsidian.md/t/topic/5954/67][url::https://forum-zh.obsidian.md/t/topic/5954/67]
[type::blog-forum-zh.obsidian.md]
27. [[玩转 Obsidian 01：打造知识循环利器 - 少数派]] [玩转 Obsidian 01：打造知识循环利器 - 少数派][https://sspai.com/post/62414][url::https://sspai.com/post/62414]
[type::blog-少数派]
28. [[玩转 Obsidian 02：基础设置篇 - 少数派]] [玩转 Obsidian 02：基础设置篇 - 少数派][https://sspai.com/post/63481][url::https://sspai.com/post/63481]
[type::blog-少数派]

<mark style="background: #FFF3A3A6;">DEMO: youtube.com/watch?v=UzseaoxaSEM</mark>
Roam-highlighter Shortcut Keys (v2.1.1)

> [ALT + X] - Activate Extension and Show/Hide Side Window
>
> [Ctrl + X] (WIN) or [CMD + X] (MAC) - Highlights selected text - To remove part of a highlight, select text and press [Ctrl + X]
>
> [Alt + Click] - Removes an entire highlight
>
> [ALT + Q] - Remove all highlights on the page
>
> [ALT + A] - Makes selected highlighted a "header"; highlights following will nest until another highlight is selected as a "header"
>
> [Double-Click] a Single Word (has to be highlighted already) - Adds [[Double Brackets]] for Roam "Page Linking"
>
> [ALT + Z] (must already be highlighted) - Adds [[Double Brackets]] around selection for Roam "Page Linking"

[玩转 Obsidian 01：打造知识循环利器 - 少数派](https://sspai.com/post/62414) [[Obsidian-Highlights]]

- 工具推荐：Roam-highlighter
- Roam-highlighter 如何使用
  - `Alt + X` ，显示和隐藏窗体
  - `Ctrl + X or CMD + X` ，对选中的文字进行高亮或取消高亮
  - `Alt + Click` ，移除鼠标点击所在的高亮内容。
  - `Alt + Q` ，移除所有已经高亮内容。

1. install the [picgo](https://github.com/Molunerfinn/PicGo) and config it
2. open the tool and open the setting "设置 server"
3. install the plugin in obsidian
4. open the plugin setting, and set the "picGo server" `http://127.0.0.1:{{port in picgo}}/upload`（example：`http://127.0.0.1:36677/upload`）
5. try paste image
   ![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108112226.png)

![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108112327.png)
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108112353.png)
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108183631.png)
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/pic20231108191707.png)
