# macos

## Command+Shift+.  显示隐藏文件快捷方式

## iterm2

### 快捷方式

- cmd+d: 垂直分屏
- cmd+shfit+d：水平分屏
- cmd+alt+arraw：切换屏幕
- cmd+; ：查看历史命令
- cmd+shift+h：查看剪切板历史
- cmd+enter：全屏切换
- cmd+w：关闭标签
- cmd+t：新建标签
- ctrl+u：清除当前行
- ctrl+l：清屏
- ctrl+a：到行首
- ctrl+e：到行尾
- ctrl+f/b：前进后退
- ctrl+p：上一条命令
- ctrl+r：搜索命令历史

## vscode

### 快捷方式

- cmd+k v：打开markdown预览

## neovim

### pip install neovim
pip3 install neovim

## mac 软件

### mindnote思维导图

### pages写文章

### Photoshop修图

### final cut pro 剪视频

### pr 视频剪辑

### downie4收集素材

## 工具

### awk进行git提交分析

1.文件：5.2.0.awk

BEGIN     {  }
{ismsg = 1 }
/^commit/ { ismsg = 0; flushCommit(); hash = $2 }
/^Author:/ { ismsg = 0; author = $2 }
/^Date:/ { ismsg = 0; date = substr($0, 6) }
/^[ACDMRTUXB]/ {
    if(ismsg == 1) {
        if(index($2, "built/") != 1 && index($2, "resources/") != 1 && index($2, ".data/") != 1 && index($2, "zips/") != 1) {
            files = length(files) == 0 ? $2 : files "; " $2;
            fileCount++;
        }
        ismsg = 0;
    }
    else {
        ismsg = 0;
    }
}
{ if(ismsg == 1) messages = messages $0 }
END  { flushCommit(); printStats();  }


function flushCommit() {
    stats[fileCount] += 1
    print hash, "|", author, "|" fileCount, "|" files, "|", messages
    author = ""
    date = ""
    fileCount = 0
    hash = ""
    files = ""
    messages = ""
}

function printStats() {
    for(key in stats) {
        print key, ":", stats[key]
    }
}

2. git中切换到5.2.0-uos分支
命令行：git log 5.2.0-vpc HEAD --name-status
git log 5.2.0-vpc.. --name-status > diff.log

3.命令行：gawk -f ~/Downloads/5.2.0\(1\).awk diff.log > diff.gawk.log

4. mac上awk输出不一致，使用gawk，brew install gawk
linux 上直接使用awk

输出文件https://www.kdocs.cn/p/110942009149?from=docs&source=docsWeb


输出的源代码：


 |  | | | 
3d966e95de78342f65f9b7249da8ab42a738368c | wangchuan |0 | |     build
96362aa70ebcf6d66938bc7341f7f6374fc6ebc4 | wangchuan |1 |personal_login/js/webLogin.js |     合并vpc代码，密码登录：全局enter提交
c59a604beca3eabb9d5303188096b9b18ecf28e3 | wangchuan |0 | |     国产化包：个人桌面，全局enter登录
d7c01aaa0cc355277566c094f46598f73fe7ca95 | zhangyao |0 | |     build
94102845952871882b853feea8257c9e6cb04d1a | 魏聪 |2 |views/idv/dialog/desktop/modify_scene.html; views/voi/dialog/desktop/edit_sence.html |     解决编辑场景时挂载的数据盘可以为空的问题
2aa0ce39c527b155eb02036e713c6f9d65292f6d | tianyiwen |1 |views/vdi/help/deploy.html |     快速部署自定义模板样式调整
fdf489d636e38658240c6fc1e0394a01db46c722 | tianyiwen |2 |views/idv/template/teach.html; views/voi/template/teach.html |     去掉公共模板voi，vdi的绝对定位
e63130b6765d2e2fd06d703bfa39a9f7173a6d15 | tianyiwen |1 |780093d9c |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
780093d9cf707a5e93ccd2d551f302ad270d2b5a | tianyiwen |3 |views/vdi/plan/host_switch.html; views/vdi/plan/snapshot.html; views/vdi/plan/switch.html |     修改计划任务模块的表单描述溢出隐藏
4fd35c0ad0e21741e01b66ddd985b52df6dc470a | wangchuan |0 | |     build
bbc97bac2512a739544d0b40ea4a74343ee0d46e | wangchuan |0 | |     国产化包
25a63197e8fa0a8a546524b5899df5b50d93701b | tianyiwen |1 |views/vdi/template/teach.html |     去掉公共模板瓦片checkbox绝对定位
eb05b5b5a921fbafe973bb6c187aa9111d244854 | wangchuan |0 | |     国产化包
e8b1ec058bc9b172b283793824830aa723e66f50 | tianyiwen |1 |views/vdi/desktop/teach.html |     去掉teach中的用户名
1e16d13f4f74dfd9244a53a0cefadf95695ac3c1 | tianyiwen |1 |9ae0a6930 |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
9ae0a6930cfcd4ff5924d6d71c0dbf6445632af5 | tianyiwen |4 |views/vdi/desktop/teach.html; views/vdi/dialog/desktop/personal_alter.html; views/vdi/dialog/system/system_deploy_advance_options.html; views/voi/dialog/desktop/edit_roam_desktop.html |     根据需求5869和bug18122屏蔽掉部分计算机名
50f02fa58df37e637e5343ffaf77634a2412a654 | wangchuan |0 | |     国产化包
c75621736edf3907a170b151128e2b48f9d67f03 | tianyiwen |1 |js/vdi/desktop/scene.js |     修改新增公共桌面时无论什么情况，usb_version都为3.0
48c39ba299d74d6cd3ac6bf9ae20296beaaaf26c | tianyiwen |1 |views/vdi/desktop/teach.html |     去掉公共桌面中场景列表的计算机名
8c1c7f966fc745e6b8fc3aa8ae0c61f5e2626425 | wangchuan |0 | |     国产化VDI包
fa8706435f68c72139798d15abd989a799d98e06 | zagger |0 | |     build
b04aa257b339d9322456302d75725266252c48f6 | zagger |1 |js/voi/system/controller.system.js |     VOI默认设置项-默认值设置
6c12fc2394b791902d9a1eba5456ae43068f3d85 | tianyiwen |4 |js/vdi/desktop/personal-desktop-pool.js; js/vdi/desktop/personal.js; js/vdi/desktop/scene.js; js/voi/desktop/controller.roam.js |     新增个人桌面、公共桌面、个人桌面池、漫游桌面USB默认改成3.0
214565e1df16e1a68a82c86208d90a29c54888f8 | zagger |0 | |     '    build
072a3ffdddc80dd4a8d348c462577c9c05a1c822 | zagger |2 |js/voi/system/controller.system.js; views/voi/system/set-voi.html |     bug# 15311 国产化服务器（ARM）【管理台/网络/DHCP】增加选择底层包的功能 - 前端
2a760dc24d008264b35238022036318e762065fd | zagger |0 | |     build for uos
b6c22377224a6200a4cad48e9f136ba440bd7b65 | zagger |1 |js/vdi/user/admin-user.js |     改变分页信息,调用接口两次问题
0ef59e39dc68269ba2c60d986ae4534a6d917f27 | wangchuan |0 | |     国产化包：设置客户端桌面问题
24805c5d89ee40b62ba0e336d7f3db38b4d3f6b9 | wangchuan |0 | |     build
e174f44c2b3ca6fcc13a8a90d0d0cdbddf35b6f9 | wangchuan |0 | |     国产化VDI包
2f39b0a4be43bb23d24bd365cee117662a6afad2 | wangchuan |1 |e016164d1 |     Merge branch '5.1.4-vpc' into 5.2.0-uos
e016164d16dcef1d5d4db69d035eb04969d19ab0 | zagger |0 | |     build for uos
d2b74f080f7137150164d885f88136e28a8e136b | zagger |1 |spice.html |     bug#【国产化-web端】-web端登录个人桌面后，界面存在“移出安装介质”功能按钮，应该只在模板编辑界面存在此功能 17911
1074fe6483e63410e42b6c9dce9884b7d6e860a4 | zagger |1 |views/vdi/dialog/desktop/scene_new2.html |     bug# 17906 【国产化-公共桌面】-新增公共桌面时仍然可以配置修改计算机名，与需求不符
5e4852cb751d6e2826450df56d1c86d7cd3803bc | wangchuan |0 | |     build
92b18f6a396615502d29831046169b9257ab4429 | wangchuan |0 | |     国产化VDI包
2f3235afd14ee2e8d33072cb33d911758290bdf9 | tianyiwen |1 |img/logo/vpc-fusion_zh-hans.png |     管理台的logo换了一张旁边空白部分少的
2f201043a9af76dd614441daa142aff608d7132c | zagger |2 |js/vdi/security/shared.js; views/vdi/dialog/security/manage_desktops_for_strategy.html |     bug# 17835 【国产化-桌面安全】-国产化操作系统启用屏幕水印后，详情信息中显示屏幕水印策略不生效，实际是生效的
bc41c09ba5e5913499e171ffe96fbe28ff365f1c | zagger |0 | |     build for uos
1097ba542f21097eceebb117d6a08605595f3183 | wangchuan |0 | |     build
0d0832cb2e0a358cd16089b4983f24af9324f5e2 | wangchuan |0 | |     国产化VDI包
a6a68efaf65b81e43a854af0899981b0f4e16254 | 魏聪 |1 |views/voi/dialog/terminal/terminal_config.html |     voi终端屏蔽静默更新
6c8b1b183a48f0b1547c51cf6787a5e0ec557bdb | 魏聪 |3 |js/vdi/utils/ui.js; views/idv/dialog/terminal/terminal_move_groups.html; views/voi/dialog/terminal/terminal_move_groups.html |     修改voi与idv终端移动下拉框无法收起问题,修改uiTreePicker支持自动收起
b359a971366e68a392e815126c01e936a1687c70 | 魏聪 |1 |views/idv/dialog/terminal/terminal_move_groups.html |     解决idv终端移动下拉框不自动收起问题
0aa54db309a4ba5a536ee65b315806f9adb24065 | 魏聪 |3 |js/vdi/utils/ui.js; package-lock.json; views/voi/dialog/terminal/terminal_move_groups.html |     voi终端移动树结构没收起，修改uiTreePicker支持自动收起
df76adc48711ccbd27cc096840e8c0f03baae727 | tianyiwen |1 |views/vdi/dialog/security/watermark_preview.html |     修改水印预览
4da08db495443a59a0759a8f73da7f95f355daa9 | tianyiwen |2 |init.html; views/vdi/dialog/resource/pool/new_host.html |     去掉硬件虚拟化检测提示
1927fa759018a1c40a8ff0abea4c85d1d0f9869d | zagger |1 |views/vdi/dialog/desktop/newDeskPool.html |     国产化-17755 【国产化-个人桌面池】新增个人桌面池时，USB3.0重定向选项不可选
7c6b04fa317a4e10499a9ea4c0cc4675bcc5899b | zagger |3 |img/clientLogo/vpc-fusion_zh-hans.png; img/client_voi_logo/vpc-fusion_zh-hans.bmp; img/logo/vpc-fusion_zh-hans.png |     姣姐三种logo图替换,vdilogo,vdi端logo,voi端logo
5b0e100e9c7f38626ef79f7cb74b3625ec4713f3 | zagger |0 | |     build for uos
25d29fcc1f53e124d90e420163310af8a407f722 | zagger |1 |css/your_style.css |     系统桌面瓦片样式修改
5742c25e643ba500bae357ef776a2f38d09dff24 | zagger |2 |js/vdi/spice.js; spice.html |     移除安装介质
da3ba4cb03a5625c6f4376d44de247111d46cc22 | zagger |1 |package.json |     xterm low edition
ae12cedb755f2b19c75593b428798987902e0281 | zagger |1 |package.json |     xterm low edition
8fbb2ff6768970035ce8c7c53d76305c72d14d4c | wangchuan |0 | |     国产化包
b397f48501c1ad125f4d85c47725023dc114c771 | zhangyao |0 | |     build
07dca05cf8bab0414b6ee0c7c68e2914c4f50f63 | zhangyao |1 |b1e7ada50 |     Merge branch '5.1.4-vpc' into 5.2.0-uos
b1e7ada50417331071ff9a3f97a203d137e5717a | zagger |0 | |     build for uos
b84e9f2f07aed8f52066b8664c10bf16b4ef19cf | zagger |1 |views/vdi/dialog/desktop/scene_new2.html |     袁阳需求编号:5869 新增公共桌面设置用户名功能屏蔽需求说明
e4ab919b63305787fdef48180c5e0d5fd19e2b53 | wangchuan |1 |views/vdi/terminal/client.html |     国产化：去掉动态密码功能
31f88f09995e2401e8929c3fa1e8723328d2e0c3 | tianyiwen |1 |init.html |     虚拟化检测已通过
b5842463b4338ffb40364e02eddd211d1b325d5d | wangchuan |0 | |     国产化VDI客户端包
e10828fa3737440b17206ffcc03f3d4c213a8231 | zagger |0 | |     build for uos
e35444329f0faaccc12e10d05d05592a4b7677b5 | zagger |1 |js/vdi/vdi.js |     阻止鼠标右键的默认事件
b8b109bcf90681c8957ef88c994f91141b119110 | zagger |1 |package-lock.json |     build for uos
c09abe241be1b0be79de151294ebd47cd7b8e252 | zagger |1 |js/vdi/os-types.js |     国产化os-type添加_64
6d61cf8041e220bff5089a0fe21fa9b0baf11a32 | 魏聪 |1 |js/voi/desktop/controller.scene.js |     解决voi场景下桌面轮训判断hash错误
e059c82e7178f93881b130ac6c565462f6695103 | wangchuan |0 | |     build
b62c464f38cc825af5b8c643e2e9133b9b118d4c | wangchuan |1 |64b359ecd |     合并5.1.4-vpc代码
ad0bdb62a41146df3b87bd9ed9254a8e93e9d8ad | 魏聪 |1 |js/idv/terminal/controller.terminal.js |     idv终端移动区时放开isLoading
64b359ecd761d09fc3e2fb7f486e3b5f778fa6b5 | 魏聪 |7 |css/your_style.css; js/idv/terminal/controller.terminal.js; js/voi/terminal/controller.terminal.js; views/idv/dialog/desktop/add_scene.html; views/idv/dialog/terminal/terminal_move_groups.html; views/voi/dialog/desktop/add_scene.html; views/voi/dialog/terminal/terminal_move_groups.html |     解决voi,idv创建场景区域选择，voi,idv终端移动到区域下拉树的一些问题
761e6bfb338e5b5f68a5d7fc1c0ba965ae37b455 | 魏聪 |9 |css/your_style.css; js/idv/terminal/controller.terminal.js; js/voi/terminal/controller.terminal.js; package-lock.json; package.json; views/idv/dialog/desktop/add_scene.html; views/idv/dialog/terminal/terminal_move_groups.html; views/voi/dialog/desktop/add_scene.html; views/voi/dialog/terminal/terminal_move_groups.html |     解决voi,idv创建场景时下拉树可以输入的问题，解决voi,idv终端移动区域时，允许取消选择的问题，同时也统一了 创建场景和移动教室2个组件
0fc77edc6fb6ae3f0c24bfd3ec163cf0fffa2d0b | zagger |0 | |     build for vpc
a9e881a591ce909ecf1347f85c72719855cb63d1 | zagger |1 |js/vdi/user/admin-user.js |     loading 问题
fe03639d669c2165e380bc5ec2a6479d65dae0a6 | zagger |1 |js/vdi/user/admin-user.js |     destroy=>
3a699e8437f5cc8fd2e3910e4db803c941b001c1 | zagger |3 |js/vdi/user/admin-user.js; js/vdi/vdi.js; views/vdi/common/account-config-info.html |     1. bug for header部分按钮的帐号设置,确定接口成功之后,当时处于/user/admin路径时,获取一次管理帐号列表接口.    2. !!!未完成,管理帐号这里,需要重新更改接口,不需要传递所有数据.
ebc657ea8f7393656076200c661da6ba3c07736b | wangchuan |2 |js/vdi/terminal/controller.terminal.js; views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     产品要求：设置终端去掉一个配置
2a05118b4bcbbd849da4b694da687f473b0d3517 | wangchuan |0 | |     国产化VDI客户端包
2fb2b6fe49af5a9dbba222a45a694f8438edaa15 | wangchuan |0 | |     VDI客户端包
baee29d61eb1f25dae23768971b36c0edc66b709 | zagger |1 |js/vdi/user/admin-user.js |     destroy=>
cc53d4766e067a89cdf067e575a32feb246c14ec | zagger |3 |js/vdi/user/admin-user.js; js/vdi/vdi.js; views/vdi/common/account-config-info.html |     1. bug for header部分按钮的帐号设置,确定接口成功之后,当时处于/user/admin路径时,获取一次管理帐号列表接口.    2. !!!未完成,管理帐号这里,需要重新更改接口,不需要传递所有数据.
dbdfdf135889dd87a0e0436135cd848185745708 | zagger |0 | |     build for vpc 5.28 backend login
adf5a1f3994d7d344fd554aa3e4b5f2921ca13e4 | zagger |0 | |     build for uos
4185fc9edbc7666362746f369105d275e5603cea | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储：监控图表bug
8de76bef2bf08faebdce2ef42b76819a3b3e99bd | 魏聪 |1 |views/voi/dialog/desktop/desktop_detail.html |     说是voi的个人桌面要取列表里的域信息，已改
042aa33cdf2faac05a0e7790f1d787a8f41809c1 | zhangyao |1 |ngconsole-webpack-plugin.js |     修复 middleware 顺序
791828f673ef1f7711e64001995b4ba201026e1e | zhangyao |1 |9a8df7d76 |     Merge branch '5.1.4-vpc' into 5.2.0-uos
9a8df7d7680853d97baca38170715742463c400d | wangchuan |0 | |     国产化VDI客户端包
12bb6a4f8ed57f3f82f5cebd41c156d23e44b8c7 | wangchuan |0 | |     国产化VDI客户端包
2d0870d763e8c95c3b6abab5938363e6a6d508a5 | zagger |0 | |     build for 投影仪
2d51417e393b41a00ba58a42bdd69690716aa438 | zagger |1 |css/your_style.css |     vpc投影仪样式修改-bug2
442cdd0f764e059d263761cb6b51aae12141cddb | zagger |1 |css/your_style.css |     vpc投影仪样式修改-bug
83934259411e5a4f71ab4bc4e23c4f5d6fdb3f55 | zagger |2 |css/your_style.css; img/new_login_icon/header_bg.png |     vpc投影仪样式修改
6ee2af62a1ec8cf6d5a0fca1aa3883c423462857 | wangchuan |3 |css/smartadmin-production.min.css; js/vdi/summary/controllers.js; js/vdi/summary/summary.css |     投影仪版概要
ac6576cc772cca682968e9468b1193a275dd296e | 魏聪 |0 | |     voi桌面水印提示信息去掉 windows 字样
bc2bfa5e5a21098e39c3996663b13e4ae9e4c84d | 魏聪 |1 |views/idv/dialog/template/register_tpl.html |     修改idv注册模板下拉范围影响确定问题
f497ad5a3598325b634f759d1add761bbc6cd535 | 魏聪 |1 |ce2abb187 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ce2abb187f7c85f10d121835979d7c91ab33689f | 魏聪 |1 |views/idv/dialog/template/register_tpl.html |     'idv模板注册模板下拉范围选择无法确定bug'
3c10981af494d242295fa5f087a1d3e5b51f1b30 | wangchuan |0 | |     build
6158b3d376e3b05c18211a76d09db282ea14a3b7 | wangchuan |0 | |     VDI客户端包
50b1da3135e36308ef22e0a149c9b064612f4ccc | tianyiwen |1 |5977ed6ff |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
5977ed6ff232111f0e2c172daae6429718613d08 | tianyiwen |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     修改设置运行参数table下边距
04ff45e361a15446e63fbe9d19a710e6d244ff75 | 魏聪 |1 |package-lock.json |     voi自测打包
b1902a8bf46670b31fb1ebbef44587f316395c20 | 魏聪 |3 |js/idv/terminal/controller.classes.js; js/voi/hardware/controller.printer.js; js/voi/terminal/controller.schoolroom.js |     修改voiidv区域下有默认区域时的提示
c0c6f7721798df631850a40808d18f29c9da5618 | 魏聪 |1 |3a363e021 |     'voi_idv区域子下存在默认情况进行判断'
3a363e021f7c2cfd108f8ace05938b20878ccbd0 | 魏聪 |2 |js/idv/terminal/controller.classes.js; js/voi/terminal/controller.schoolroom.js |     'voi_idv区域子下存在默认情况进行判断'
eda3e5c4af716e52e93bd000706ec63999bffbdb | zagger |1 |views/vdi/system/set-general.html |     去掉影响样式代码
9e83e3ba9d67aef5c504c5552edc8937813a4ed1 | tianyiwen |2 |views/vdi/help/activeAuth.html; views/vdi/system/set-vdi.html |     fixBugs:17245,17043-去除共享磁盘、去除激活授权idv
1186683f849f7adee654541b27d7281958661352 | zagger |0 | |     build for uos
551d76d4f608c5717d2df50ca73028f965d752bb | zagger |0 | |     build for vpc
d9a2486f386f35845a9bce8c7fb63574b1df8c05 | wangchuan |0 | |     国产化端
2ab22fa50672d14edd2d7a7efce78431a5c1aa66 | wangchuan |0 | |     VDI客户端包
4d86da0e9ae176186269e356be49e35029173b2a | wangchuan |2 |personal_login/js/components/user-form.js; personal_login/views/user-form.html |     解决bug#17249
ec65fee73140f35ed1f597510f5e4b3301d5a5c2 | wangchuan |0 | |     VDI客户端包
bba600179a710359898c43e668563d1e93c4fd0c | tianyiwen |2 |views/vdi/dialog/system/template_add.html; views/vdi/dialog/system/template_register.html |     fixBug:17238-修改系统桌面类型选项初始值
906d2b2c60ca593093dbe6dbdf44195372572e56 | tianyiwen |1 |94ee16982 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
94ee16982f55d6a5ec1ede7bb599e157b421b310 | tianyiwen |2 |css/your_style.css; views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     fixBug:17140-修改设置终端快捷键
d2c53fc0ab4c94d737e78f2aa32f26d12b0542dc | wangchuan |0 | |     build
a121d85407bdcf7057d04603e4930c2d92199650 | tianyiwen |1 |js/vdi/help/controllers.js |     nothing
430d86e9a029d7620f2651eb2e1dfdadcc88a093 | tianyiwen |1 |js/vdi/help/controllers.js |     fixBug:17229-修改激活授权中已用点数逻辑
e4b52a15858f7cfd7cc36e3d3ba00dfc98815394 | zagger |0 | |     build for vpc
263f9a0a3ff479b83f778e30b49159be70609a76 | zagger |1 |48617e601 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
48617e6015e4bb3c1c8df44e862815d2a925a5c1 | zagger |0 | |     build for vpc
a72bf10e3a62e95bc465ca6628f355ee6284130c | wangchuan |3 |js/vdi/security/system/controller.security.system.css; js/vdi/security/system/controller.security.system.js; views/vdi/security/system/security_system.html |     tip
c18478b181cd8aa7dcb573c6024453a49feda0d1 | wangchuan |3 |css/your_style.css; js/vdi/vdi.js; views/vdi/resource/storage/disk.html |     loading加背景色
338fb5662260cbf3ec3f0423d5971bc57ceed502 | wangchuan |0 | |     VDI客户端资源包
2336d494562e881d57d75172b8624111cc96b54f | zhangyao |1 |ngconsole-webpack-plugin.js |     修改合并资源的时机
455d63a01815024382e25177ee47e76a045fe19e | zhangyao |1 |ngconsole-webpack-plugin.js |     修改合并资源的时机
19e900e509bd09d8d5234364b4574747aeedf47b | wangchuan |0 | |     国产化端
cd37a6f5bb7790501a72e8d0839f7a2608a0fa7e | zagger |1 |package-lock.json |     国产化前端build
116b56266855049c399d92b921e5a646c710ca77 | zhangyao |3 |ngconsole-webpack-plugin.js; package.json; yarn.lock |     优化开发服务器
4a317ff15d5a529aed13b6a6d0f1aae74c9b265b | zhangyao |3 |ngconsole-webpack-plugin.js; package.json; yarn.lock |     优化开发服务器
060bd368a6dafd2eb43e97251bbad141546c3c47 | 魏聪 |1 |139b620d2 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
139b620d2dc8439f26429e79e4588653f24c395e | 魏聪 |2 |js/voi/hardware/controller.printer.js; views/voi/dialog/hardware/edit_printer.html |     '将文件名上传限制到60字符长'
8fd149f3b3a68db854128e426e95ffa72292d675 | zhangyao |1 |50aa4d3cb |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
50aa4d3cb148ec5bee6ea1cf1803c24fa38c17c9 | zhangyao |1 |js/vdi/system/system-log.js |     修复日志备份下载问题
37fc375cf7d11ea9f436da45de170ea902167839 | 魏聪 |1 |a8eb44c66 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a8eb44c669004d7f62eec5a7c9c18cde94974ee3 | 魏聪 |1 |views/voi/dialog/desktop/add_roam_desktop.html |     '去掉漫游桌面上的注解'
baff6b228442b04d7dffe5903df1cd7c987ddaa8 | tianyiwen |1 |views/vdi/system/set-general.html |     修改自定义logo界面两个btn位置
ac5c681e50779b5d495d850fead28b51c563b833 | tianyiwen |1 |views/vdi/system/set-general.html |     fixBug：17200-修改自定义logo界面btn位置
24c9ae2ad640dbbaac6d1dc633050d1dc61f379c | zagger |1 |8a22302d9 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
8a22302d953c901da113ffd40495ecfefd5fc803 | zagger |1 |views/voi/help/deploy.html |     voi部署按钮样式类添加
7da4f533caf3822161af1014fb4121284369b17f | zagger |1 |views/voi/help/deploy.html |     voi部署按钮样式类添加
5a9c3d7085d4c85deb4e5ed6d74c39e92d0f7ffb | wangchuan |1 |views/vdi/system/recycle/system_recycle.html |     产品要求改个表头
f155c818de4ce085bd9b00b16f6e152c5588b453 | 魏聪 |1 |js/voi/terminal/controller.schoolroom.js |     'voi修改区域下存在默认区域的删除提示'
2f5a57ac09aa08e011b6db369a18b2ce7dee5ac3 | 魏聪 |0 | |     voi打包
2b683a361fbf71cd30ea7e9ce186a5035b71b34b | 魏聪 |1 |js/voi/terminal/controller.schoolroom.js |     解决子下存在默认区域问题的删除
f6454fa065530d5040022bc1197db637b7b86751 | wangchuan |0 | |     VDI客户端
d741ac91e893efe5babc719385215e0ddec2ec95 | 魏聪 |1 |74f0165d5 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
74f0165d5394f38a15063d6423192214b02ae68f | 魏聪 |1 |js/voi/terminal/controller.schoolroom.js |     '区域删除判断'
138073fdf66702b74a0a06cca6daf510f59ce3e0 | wangchuan |0 | |     VDI客户端包
6f6def755282fb2a278c9028e46521025174b351 | zagger |2 |views/vdi/dialog/desktop/personal_alter.html; views/vdi/dialog/desktop/personal_new.html |     vdi隐藏镜像分层代码
1c929714bb9bef8569769fddfd39f25ee2df8a17 | tianyiwen |1 |views/vdi/dialog/security/new_desktop_strategy.html |     fixBug:17165-处理桌面安全编辑的问号换行
e22fc50bb2e8e9f52c0725bc69d3433dcb31739d | tianyiwen |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     删除写错的代码
97bf0363a1d37b86aa02cc65abbd89ab1ec53be6 | tianyiwen |1 |76c523ea9 |     Merge branch '5.1.4-vpc' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.1.4-vpc
76c523ea9f3e9c5307c690e74116fe5daf688daa | tianyiwen |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     fixBug:17140
120a5f94e4fdaecbfbd4d4545404fbd0e1ad6d04 | 魏聪 |2 |views/voi/dialog/desktop/add_personal.html; views/voi/dialog/desktop/edit_personal.html |     'voi去掉镜像分层功能'
64291107e0912117c665877adba4e1689b9f884f | tianyiwen |1 |views/vdi/resource/storage/storage.html |     fixBug:17169-去除设置网盘存储
e0a0bee3fca454a97f6d014f600044a1a6e15851 | 魏聪 |1 |views/voi/dialog/desktop/add_scene.html |     去掉异构
59bc95bf3b9a2f03b8d44851491c7291ef333886 | tianyiwen |1 |views/vdi/desktop/personal.html |     fixBug:17125-修改录屏管理菜单的位置
949b541b9395704cd218ca5f0965271caae5bed4 | tianyiwen |1 |fb979c190 |     Merge branch '5.1.4-vpc' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.1.4-vpc
fb979c1900c82200dc373e89c132a0cfc695da1c | tianyiwen |1 |views/vdi/desktop/personal.html |     fixBug:17125-修改个人桌面设置菜单
8b2c9c28a41bd92eb8a5715a8107c028be2678c3 | tianyiwen |1 |js/vdi/help/controllers.js |     fixBug：17133-去掉帮助/关于里的win，an，vdi
dd2698a3a6315caff48b5c9d56ece8dd7dfbfbf8 | 魏聪 |1 |js/voi/voi.js |     '添加一个scheduling状态翻译'
2f5cb01af04bab93f30ce02e1cf7889520c8403f | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/security/client/security_client.html |     终端安全列表：文件传输列只显示开启关闭
3ec1ed8bbeecb46637053adb558455680caee874 | wangchuan |0 | |     假数据
e66d5ac3334485b8df9214163e41b544fded264b | wangchuan |1 |views/vdi/dialog/security/client/add_edit_security_client.html |     新增终端安全：图标修改
16e4698d5c6f33c3ac046b0b6b51d9d304a8a226 | wangchuan |2 |js/vdi/template/system-iso.js; js/vdi/vdi.js |     去掉MessageBox
849bc446378feaab2291a14bfbb9791cefce5faa | tianyiwen |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     fixBug：17140
ccdf35e34500a4345b7752034210922074223dff | tianyiwen |1 |0aff96626 |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
0aff966267729488d6934d731698dcfb27a69bb8 | tianyiwen |1 |spice.html |     fixBug:17114
209b7977e982c04ffcd4e0c90276668e9c0f1658 | wangchuan |0 | |     VDI客户端包
98bc6405e68608e80c19e29492cad13526779c7e | zhangyao |0 | |     build
babb09366263ff5053287746aec8920199904cc7 | 魏聪 |0 | |     voi打印机联调中
df445029de9998d4a031e5257e15f677f2ecc99f | 魏聪 |1 |views/voi/dialog/terminal/printer_bind_detail.html |     打印机失败详细中字段修改
71192fc7df5c59c9a0e4fe844bdf69449385f0e6 | zhangyao |0 | |     build
193ce75014de731770f07e1db4678516dac16e29 | zhangyao |1 |js/vdi/desktop/api.js |     fix: 17081
90bf44e4ffb0fe19f005988cbe135398982af981 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储列表轮询bug
5ace8d4371f74c73370f7020012e70c7051e72b6 | zagger |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     bug#17026 【国产化-终端管理】设置终端运行参数的快捷键里出现了Linux，Windows信息
33d9a71715c90c86adb10c2f7cb530ab8a65b5a6 | 魏聪 |1 |views/voi/dialog/terminal/printer_bind.html |     'voi个人桌面重置'
b40b76b11f28e0f12c054dd2d6ebabc1ba0f1e65 | tianyiwen |5 |views/vdi/desktop/teach.html; views/vdi/dialog/desktop/newDeskPool.html; views/vdi/dialog/desktop/scene_new.html; views/vdi/dialog/system/system_deploy_advance_options.html; views/vdi/system/set-general.html |     fixBugs:17031,17037,17039,17042,17046
b6a8bc3cb288a96d943586a53846fb5274005d1e | zhangyao |2 |js/vdi/i18n/index.js; js/vdi/resource/console/controllers.js |     修复禅道bugs
2e77ba3c7c26a6323d68aa0b9cf9bc5b238437cd | 魏聪 |1 |img/uos.png |     替换uoslogo
96873e7d60890ed97e5124bbbe5dc04a5b1d6bf8 | zagger |1 |views/vdi/dialog/desktop/personal_detail.html |     17032 【国产化-个人桌面】个人桌面详情有域相关信息
f78d0400d856ffa99e020512b9afb21276e393e9 | wangchuan |1 |views/vdi/dialog/template/template_imgManage.html |     分发镜像bug
d55b4c92c0bb093be92ab62760cb5bbb372a313d | zagger |3 |js/vdi/desktop/personal-desktop-pool.js; views/vdi/dialog/desktop/newDeskPool.html; views/vdi/dialog/desktop/personal_new.html |     vpc-新增资源池-更换新接口-conflict
d8f6af327f6763540eb17f53a44d320eee01bcdb | wangchuan |1 |d6976131b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d6976131b57ab65510a67c5807827b7ba8207775 | wangchuan |3 |js/vdi/template/controller.person.js; js/vdi/template/controller.teach.js; views/vdi/dialog/template/template_imgManage.html |     分布式存储：个人、教学模板，分发
5cbdc7270e96919c323dfbc40e5b12351386d276 | zagger |1 |e43618d8d |     QMerge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
e43618d8d6e528647c6cdaf41bbc0990a495f640 | zagger |3 |js/vdi/desktop/personal-desktop-pool.js; views/vdi/dialog/desktop/newDeskPool.html; views/vdi/dialog/desktop/personal_new.html |     vpc-新增资源池-更换新接口
3334cbc7f04057ef61acc1fe982d8d189cb30b38 | 魏聪 |1 |views/voi/dialog/terminal/printer_bind.html |     voi打印机功能优化
117d68a5b4f185dfe1526ac4a5d6788712ef05ec | 魏聪 |2 |views/voi/dialog/terminal/printer_bind.html; views/voi/dialog/terminal/printer_bind_detail.html |     '在打印界面添加了提示'
64c5d90d8f43aaff017ab3d1e76ae76b92e4bcec | 魏聪 |1 |views/voi/dialog/terminal/printer_bind.html |     '打印机绑定窗口添加tip'
0696838db6e81f3b84c91d268b981a15bb9fcf6f | 魏聪 |3 |js/voi/desktop/controller.scene.js; views/voi/dialog/desktop/add_roam_desktop.html; views/voi/dialog/desktop/add_scene.html |     去掉新增漫桌镜像分层的提示，去掉新增场景中3个镜像类型的tab
6923a0be457f6b6bfe7b3dae752bf5b1c6f9ded7 | 魏聪 |3 |js/voi/desktop/controller.personal.js; js/voi/voi.js; views/voi/desktop/personal.html |     'voi个人桌面重置功能'
9b80962269393f5fc980b111fc26377a4018ff26 | zagger |3 |views/vdi/dialog/system/template_add.html; views/vdi/dialog/system/template_config.html; views/vdi/dialog/system/template_register.html |     国产化-新增系统桌面去掉-新增，配置，注册等界面，系统桌面类型中去掉共享服务选项
4b9e69184b9a59aedb84199d0a21daa485ac83b8 | tianyiwen |1 |cf40b360f |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
cf40b360f20af244ea43e14e25fb5414484b73b4 | tianyiwen |1 |views/vdi/resource/storage/storage.html |     bugFix:17022
cbe1e5b042ed887b67ffe3db1dea002ecd06e935 | zagger |1 |views/vdi/template/teach.html |     共享模板不能删除，只有是owner才可以删除
d574b0ac2b9a94c3be0c86a32d8e1563b41b3921 | zagger |1 |views/vdi/template/teach.html |     共享模板不能删除，只有是owner才可以删除
ce851aea743838bff65096459b27542df0af8e95 | zhangyao |1 |b4cf958b3 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
b4cf958b36a16d02dcb2147ac5e9f046f12a9fd5 | zhangyao |1 |js/vdi/config/http.js |     web端界面过期后跳转到web端登录界面
ab81caa994316aa2be9a7697ffc4b179afa85733 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     代码优化
acbf946aac94b7f4b7aefb3f39b6af201a6abe78 | 魏聪 |1 |views/voi/hardware/printer.html |     修改打印机列表中显示字段name
39f8087f1372cdbd373c2019a32237edc5481808 | 魏聪 |1 |views/voi/hardware/printer.html |     '修改打印机列表显示字段name'
17c9ab93fb9622a4705623d763fccc66dfdab841 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     数据平衡bug
3ec121bdaf9ece6ddebaf2c2e082d15ae86a2291 | zagger |5 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js; js/vdi/utils/ui.js; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     confilct+cherry-pick
51aefcd8d2360856a90064faa14d94be55c16d93 | zagger |2 |views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     confilct
3a72ee47b87bd4c5e631e6076ffd4cd5dc1d8f18 | zagger |2 |views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     checPackAll ==>checkPackAll 单词拼写错误
1829445e6a50472d70746577fb03dc4c10985eda | zagger |0 | |     build for verify allSelect
117945c7e5129c7a7c199091ecd65bdb7586c127 | zagger |5 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js; js/vdi/utils/ui.js; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     bug for allSelect
04142fac9120ce5f2340678a8624309ea476754f | zagger |0 | |     build for verify allSelect
d61eecc87845147821e516a834395492a6b7409c | zagger |1 |78246f3a6 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
78246f3a6401fd3de5e29f49a91603aa9abeb2da | root |1 |js/vdi/utils/ui.js |     bug 全选
9b44da5011308e44370b97cd2dee03f01716f7a9 | zhangyao |0 | |     build
d4140e085d1d64dc5f3b14d90185c3812b7a62db | zhangyao |1 |c8d1567df |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
c8d1567df10a087945f5d4b53f1c72eb85355170 | zhangyao |2 |js/vdi/desktop/personal.js; js/vdi/utils/ui.js |     修复bugs
16e4321b9abf04276889968ac590b30d6bcbb29e | wangchuan |0 | |     idv客户端包
14835178be84e6c1b8e099bef971d8fb6ec46e67 | zhangyao |1 |87d83ef84 |     fix conflicts & build
4f49f0794a4efff967d31b855092ad52111ce634 | zagger |1 |js/vdi/spice.js |     定时更新-模板文字修改
87d83ef84657aab31d96dc0dd04244134ae47b6e | 魏聪 |8 |js/idv/template/controller.template.js; js/idv/terminal/controller.terminal.js; js/voi/hardware/controller.printer.js; js/voi/template/controller.template.js; views/voi/dialog/hardware/edit_printer.html; views/voi/dialog/hardware/upload_printer.html; views/voi/dialog/terminal/terminal_edit_order.html; views/voi/hardware/printer.html |     解决公共模板iso筛选问题
36a4a43f497999a539bfa7ea26d995c3a7074b8e | 魏聪 |0 | |     'voi打印机打包'
cb339e1fe4f7dc8a3f7212290fcf8e67a4f9a9e7 | 魏聪 |6 |js/idv/template/controller.template.js; js/voi/hardware/controller.printer.js; js/voi/template/controller.template.js; views/voi/dialog/hardware/edit_printer.html; views/voi/dialog/terminal/terminal_edit_order.html; views/voi/hardware/printer.html |     '打印机修改验证名称'
df0b0941f3fbacaa895122f3f8c27f7c2df6a2a8 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：修改文本
034c40e317c6a5e33fb34a11e6b047f22112e2f9 | tianyiwen |1 |927fe2dac |     Merge branch '5.2.0-uos' of 172.16.203.254:hanxiaoxiang/ngconsole into 5.2.0-uos
927fe2dac9943751527894ad4ef71bcf2cb80980 | tianyiwen |1 |js/vdi/help/system-upgrade.js |     过滤win、an、gue-需求5746
90cf4be5bcba9c7221de0f4e1b3a5e7a22b14bf8 | zagger |1 |js/vdi/scheduler/disk.controller.js |     添加注释bug#16861 【网盘】解绑网盘服务器成功后界面弹出网盘服务尚未启用
b5c0fd149e58401eb743a687c92a45a0a98edecb | zagger |1 |js/vdi/scheduler/disk.controller.js |     网盘界面，绑定和解绑网盘服务器期间，暂停前端轮询，成功了之后或者失败之后，调用check_used接口决定是否需求获取list接口
8c32f860bac66c40c3a827eef2eccf53d2298076 | zagger |1 |css/your_style.css |     loading 背景颜色补上
beaf330820ba6c1d5ad2f846ffc9aceccf94002f | zagger |1 |css/your_style.css |     loading 背景颜色补上
b7471aaff521ff19dc72c88329a78c43f8cdfd1d | zhangyao |1 |js/vdi/split.js |     临时打包
6859b65371c1b714594dfbd2746b705442c9a48a | 魏聪 |1 |views/voi/hardware/printer.html |     'voi解决打印机列表字段没显示问题'
be74ed8b3f36e582a00ff727b7ba86313d1ede09 | 魏聪 |1 |views/voi/dialog/hardware/edit_printer.html |     'voi打包'
e0361c8d5641192f819c8b6c20f8b7bdd9f92750 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：存储监控图例横排居右
99326e715bfd8b2829f1e9d91fba4772aaa11163 | wangchuan |0 | |     .data/8081
29002d73f8bdef4e149979a2a81f86349d4375b0 | zhangyao |1 |js/vdi/resource/console/controllers.js |     fix: 16893
09ed7fc70300271bef0eef6d65cec01b60ec732b | zagger |1 |js/vdi/scheduler/disk.controller.js |     添加注释bug#16861 【网盘】解绑网盘服务器成功后界面弹出网盘服务尚未启用
40d60913ae98554ee139371c779d923474076512 | zagger |1 |ae713a088 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
ae713a088c463c3a340ac9962ecc2e9e7af9c76b | zagger |1 |js/vdi/scheduler/disk.controller.js |     网盘界面，绑定和解绑网盘服务器期间，暂停前端轮询，成功了之后或者失败之后，调用check_used接口决定是否需求获取list接口
35dd35e1e8346a20ed6b7c100954722b8e21b449 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：分布式存储列表加轮询
951e4d489b6509bcf433c2c258a6a0cd28f1fe84 | 魏聪 |1 |views/voi/dialog/hardware/upload_printer.html |     修改上传打印机配置时的提示
3a7a7cf38fcd29ad64e8d1dd586e43ee8155de1d | tianyiwen |0 | |     去掉VDI终端升级需求5746
74db66d09520c4dbd81c8a21cc0077d8de2f0741 | zagger |1 |img/new_login_icon/login_3v.png |     2v图片更新
fcdaec8fc93f042bef4abbc9b7f67ee4e8494cd3 | wangchuan |0 | |     build
8012a40f86f5f0ae592e36126704cbddcd0d468f | 魏聪 |1 |de96ce8f0 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
de96ce8f099ce516898b7947caf6103684d2337a | 魏聪 |1 |js/idv/terminal/controller.terminal.js |     voi打包
47899e652c6f802c75e4b87068d5d605b90dacc6 | wangchuan |0 | |     IDV客户端包
84d7ae1351eef7e1268a4180bc0af901b8df9b46 | zagger |0 | |     build
2a499325bf63c2b62cdb2c4e59948c483c9c2a79 | wangchuan |0 | |     VDI客户端包
cc6adb432be00000c44cbbfc899e0c2262a37d2d | zagger |0 | |     假数据
abc1918afb9fcd9e3d5dc11ad91b0c99daddf509 | zhangyao |1 |js/vdi/desktop/personal.js |     fix: 16815
db318a672ec96d3c0c316173533349384550b2ac | zhangyao |1 |a439a5d1b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a439a5d1b8bb601420b214efff557f4f171910b5 | zhangyao |2 |js/vdi/bootstrap.js; js/vdi/split.js |     修改裂脑问题
9fa8a1ecced87066c9480d03d3b7dd2e0df0605b | 魏聪 |1 |js/idv/terminal/controller.terminal.js |     '修改idv重命名终端的提示'
b0d8554634bbd1bda1911cf6cbb4c363e876cb79 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：存储监控添加轮询
63f10792c6f08f701a502bc2f1f123ead418c15f | zhangyao |1 |93e30e987 |     合并 5.1.4 后来的改动
f47e7c45cbc95b652bcc947108ae0a47365c90e5 | zagger |0 | |     build
6cf26a5dad4c8dbbaf7594c9c65203477aa9313e | zagger |1 |a41224175 |     Merge branch '5.2.0-uos' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.2.0-uos
4d9fe70e79a818a7dfed6a73605e16d03c860a7b | zhangyao |1 |73c58a1dc |     fix conflicts
a41224175b302aa6afdb4e963eb7db27b5461313 | zagger |1 |f947721b2 |     Merge branch '5.2.0-uos' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.2.0-uos
73c58a1dcc315edb7fa1a83fe4ec85753f53ddf9 | wangchuan |0 | |     客户端包
f947721b249c72fd736d8926c75ab72b20a2f95c | zagger |1 |8b6b5d66c |     Merge branch '5.2.0-uos' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.2.0-uos
93e30e9871a1eb4ac5953e35da1f4a0be700525e | zhangyao |1 |f68707227 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
f68707227b1477f60f6eec01561c23d9f139f07c | zhangyao |1 |ngconsole-webpack-plugin.js |     适配 5.2.0 打包
33bfe729136fdc640cf9064a93f66b3f151bc963 | 魏聪 |1 |views/voi/terminal/client.html |     '终端打印机显示条件修改'
2486be4ad872d2b97a8ff4d58d9aea0c1806d586 | 魏聪 |1 |img/client_voi_logo/vpc-fusion_zh-hans.bmp |     添加了voi终端logo
2825e4357015cf2452a818dac4308e064ffa4c35 | 魏聪 |1 |979b7c0c0 |     Merge branch '5.2.0-uos' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.2.0-uos
979b7c0c01f5c3d8be0503f9ef74a9baa8f63559 | 魏聪 |10 |css/your_style.css; js/idv/desktop/controller.scene.js; js/voi/hardware/controller.printer.js; views/idv/dialog/template/add_tpl.html; views/idv/dialog/template/edit_tpl.html; views/idv/dialog/template/register_tpl.html; views/voi/dialog/template/add_tpl.html; views/voi/dialog/template/edit_tpl.html; views/voi/dialog/template/register_tpl.html; views/voi/dialog/terminal/printer_bind_detail.html |     修改了voi idv 下拉树换行问题
f6d33eddc0116bf3585985e6f9926d1f4662b7d8 | zagger |1 |views/vdi/dialog/desktop/personal_new.html |     新增桌面 去掉 镜像分层
1f4d88ffeaefd136a8075984c8868f8eed8b70b4 | 魏聪 |1 |img/client_voi_logo/vpc-fusion_zh-hans.bmp |     添加voi终端logo
8b6b5d66caa1dbc250e740d1ac18620659c1f2f0 | zagger |1 |views/vdi/dialog/desktop/personal_new.html |     去掉新增桌面，镜像分层代码
c78b06419e90fab4d19bac42c234d63061ffe231 | wangchuan |0 | |     VDI客户端包
f21630334870ff6b279f75d26fb22870c583fca7 | wangchuan |0 | |     VDI客户端包
ab41085bcf45ae917821e23c784d9cbf65f5c142 | zhangyao |1 |6e2b9871c |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
6e2b9871c46bb89e6ad71020ebcd238b8e2e7354 | zhangyao |2 |js/vdi/desktop/common.js; js/vdi/desktop/scene.js |     fix: 16677
775830c1a37a8f2cc1c738073f1ca20ba663fc89 | zagger |4 |js/vdi/desktop/personal.js; js/vdi/template/controller.person.js; views/vdi/dialog/desktop/personal_save_template.html; views/vdi/dialog/template/template_person_copy.html |     添加遗漏的管理范围的地方
449457d91f5c45422e5019ab1e579d9cf22b38be | zagger |1 |views/vdi/monitor/alarm.html |     告警信息-日期框改为跟日志这里一样的
4653540b37b420076c482b720a096074f23522e0 | 魏聪 |5 |views/vdi/dialog/template/template_teach_add.html; views/vdi/dialog/template/template_teach_edit.html; views/vdi/dialog/template/template_teach_register.html; views/vdi/dialog/template/template_teach_save_as.html; views/vdi/dialog/user/user_admin_scope.html |     vdi idv 范围选择下拉树添加不换行水平滚动
702de4bf56bbb0b3046db6c3e3add07447cd1f1b | 魏聪 |1 |70c0814c1 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
70c0814c1cb9341d36cd356ae618d87ea67e697e | 魏聪 |7 |css/your_style.css; views/idv/dialog/template/add_tpl.html; views/idv/dialog/template/edit_tpl.html; views/idv/dialog/template/register_tpl.html; views/voi/dialog/template/add_tpl.html; views/voi/dialog/template/edit_tpl.html; views/voi/dialog/template/register_tpl.html |     voi注册模板下拉范围选择框，文本换行改水平滚动
c3f72b26bbc7511f8794b8b82c2132a47e38fdad | zagger |0 | |     build for veryfy
8fd67737dedd086a3dfa5bd220ce7e2f9c6642ec | zagger |1 |ssh_terminal/terminal.js |     拼接webssh wss，在修改服务器端口号时，url地址
c42ea97bfd756fab96d0911803a4e5d1a2cb18d4 | wangchuan |0 | |     build
c0336105e8a7389564dc661879f3a060dadda490 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     存储监控：无数据时的样式
b31d71b41e9f5fdf0b88e94d2fec46e598e25800 | 魏聪 |1 |js/voi/hardware/controller.printer.js |     voi打印机转测
e78c57095cf6fb0b935f9d277f7f8e8b764306e5 | 0obuwawao0 |1 |views/voi/dialog/terminal/printer_bind_detail.html |     '修改打印机显示字段'
cb09e09fb572ebca9c786c2492b53fa9a3f1a1d1 | 0obuwawao0 |1 |views/voi/terminal/client.html |     '修打印字段'
687ac9231f7aa24a2feaa0a1fd332a2a818fbfbb | 0obuwawao0 |1 |views/voi/desktop/personal.html |     voi屏蔽个人桌面重置功能
6ca07873d5cfa89d382d8ce9e25c43a8cc02a972 | 0obuwawao0 |1 |views/voi/terminal/client.html |     修改点击样式
8a371a50bb4792ff0284175609c6a6a07e4f432c | 0obuwawao0 |1 |views/voi/terminal/client.html |     打印机终端列表里显示版本
21c1913050b78c3e1e2d5916e3f4fd04047ca876 | zagger |0 | |     build
754226d2e865b0d8f6818b844139b25f666843b8 | zagger |1 |a42ea0f05 |     Merge branch '5.2.0-uos' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.2.0-uos
a42ea0f0581ad45541f5184405249bf9b8382ac9 | zagger |3 |views/vdi/dialog/desktop/personal_alter.html; views/vdi/dialog/desktop/personal_new.html; views/vdi/dialog/desktop/sence_alter.html |     共享磁盘三个地方去掉：个人桌面：新增和修改，教学桌面：修改
80e0c87ae6932409ffe8d9fee43451f42d5b2198 | 魏聪 |0 | |     voi打包测试
893efbe5d98e0f2040ced4550e4b28aea51b0478 | 魏聪 |3 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/voi.js |     同步解决voi个人桌面和漫游桌面筛选域问题
9e03f37568b527ff104f04d1bbddfe81c2382b7b | 魏聪 |0 | |     voi打包测试
7c81ee8c51d16894644b8bfa522ebd7cfad008e3 | 魏聪 |1 |e2b103748 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
e2b103748355df0d1b5390f2d1ba42b208cbe02f | 魏聪 |5 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/voi.js; views/voi/desktop/personal.html; views/voi/dialog/desktop/alert_input_ok.html |     解决域树筛选桌面和数据更新问题
22e653df58f5ebe42641955a9d307bc1e3639b01 | zhangyao |0 | |     build
454daa52638f2193934bd33ce69c62d7110b5987 | zhangyao |3 |js/libs/spice/scripts/oevdi-0.1.12.min.js; js/libs/spice/scripts/workerprocess-0.1.12.min.js; js/vdi/utils/remote-desktop.spice.js |     更新 spice 库到 0.1.13
333040c3cf2406985ef5186b6951fe9425877b4a | wangchuan |0 | |     客户端包
a691081573919a0ec0282be94773cbe6e4f30cea | wangchuan |1 |b78b93a75 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
77fefbe228ba883f25c9161f08f718f0d3b45db7 | zagger |0 | |     添加定时修改密码假数据
b78b93a75c07bf6a71f24a93e1627497131d7848 | zagger |0 | |     添加定时修改密码假数据
25f986382322b324db2a5ca1ebd42ce9a5c94114 | zagger |1 |css/your_style.css |     镜像管理表格样式修复
9d0bd8cbef76a1a5f917be2f0fc04c0635f6e097 | zagger |1 |css/your_style.css |     系统桌面中特殊help-tip的dom结构样式修复
042e76d27a467767e95a893100d31736a00f8378 | zagger |2 |js/vdi/security/common.js; views/vdi/scheduler/disk.html |     用户帐号-添加帐号名称过长时，省略号显示，title显示全称
9a14f299094e0d76a7b152fe0560210b264c3413 | zagger |3 |css/your_style.css; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     conflict
8c7bc9df30e3bb335e3afbc37fe80560ba062fbc | zagger |1 |views/vdi/dialog/desktop/personal_new.html |     conflict
dbaf650a35c98c8a33b5808dab4a4afddb17a812 | zagger |1 |js/vdi/scheduler/disk.controller.js |     添加冲突
6142b9ae5f83d561e5b6ec7f9c54abf3cde3678d | zagger |1 |js/vdi/monitor/alarm.js |     告警信息-list接口-筛选参数问题：#16704
0dc1992920cf6e412c28da7317bfa99326ea812c | 魏聪 |0 | |     voi打包
cb7823d4c659e6117a6cbe616510ef0ba0821617 | zagger |1 |js/vdi/monitor/alarm.js |     告警信息-list接口-筛选参数问题：#16704
79711a668d927c859aaa575d77b07616672f436b | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/dialog/resource/storage/add_disk_group.html |     分布式存储：代码优化
a2f86aee5a584fe1e959bb930536d20b6f4e7417 | wangchuan |0 | |     假数据
3db55602f3d93310d3032821a5e83db2bae51f9a | wangchuan |1 |js/vdi/resource/storage/controllers.js |     配置公共存储：不激活不显示分布式选项
58485f6759676b13a0fada78b0d240506097895a | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     分布式存储：代码优化
ec988a846cbfa0218d824abb45a2c7ae25302ac3 | zagger |0 | |     build for verify
eb34d15f1c7bda4ad2a53d9f4a6e9db99d61da41 | zagger |1 |b5e2e6bb9 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
b5e2e6bb9307c9c7f31385234452279774fda43f | zagger |2 |js/vdi/scheduler/disk.controller.js; views/vdi/dialog/desktop/personal_new.html |     bugs
534904fff241ff4a20d049aba19448a540ccd445 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     存储监控：bug修改
e4909d12ef313b2fa4eefbc0d9a26d532f83721b | wangchuan |0 | |     build
3e38918c949df279bdb8184e044e9631d0b29782 | wangchuan |1 |08984aaed |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
eeb9b83be9ecdc19ced8c4e22dc1f2d5ef6dbb14 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     存储监控：优化
675f9c7fc207da9f503e432b35d07b3b199fb762 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     IO时延轮询优化
08984aaed61e632f7d5bb9e78d17515d4830fdb7 | zagger |3 |css/your_style.css; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     去掉影响全局的样式代码-帐号导入-样式
193a1cd90213374e7344f84e730f804aecd4966c | zagger |1 |b285010fc |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
4c89f726c41fd34ce2e0180f6af8fffc5e2f7340 | wangchuan |1 |views/vdi/dialog/resource/storage/add_disk_group.html |     添加分布式存储/磁盘：界面优化
b285010fc2cc9ae23111a2a8fc8e900072af661d | zagger |2 |js/vdi/security/common.js; views/vdi/scheduler/disk.html |     用户帐号-添加帐号名称过长时，省略号显示，title显示全称
ca775040208af09ca46df17a73211d05004e7af7 | 0obuwawao0 |1 |00d226890 |     合并代码
e323866977b8b8482d202eb158fc23bb10a801e2 | 0obuwawao0 |0 | |     voi打包测试
1e3dd30da2125cfcd926f032c13a8daa19aabf4a | 0obuwawao0 |1 |js/voi/desktop/controller.scene.js |     修改voi场景新增时下拉框可选
88fb7131474f556e172c36b73ec1212e2c158215 | zhangyao |1 |f1cae2551 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
f1cae255153f6a99b242e243a5306462aec984e5 | zhangyao |1 |js/vdi/spice.js |     fix: 16534
563101a0bc4600b11627e9e842844ef7ef89db8d | 0obuwawao0 |4 |js/idv/desktop/controller.scene.js; js/voi/desktop/controller.scene.js; views/idv/dialog/desktop/add_scene.html; views/voi/dialog/desktop/add_scene.html |     voi idv公共桌面新增的下拉树可选择
b56df3d128ec1f69aa436844337297fc25eea39c | zagger |1 |css/your_style.css |     系统桌面中特殊help-tip的dom结构样式修复
be4188e9e9824b6609864d9e128a4c3221d779c2 | wangchuan |0 | |     国产化：build
7c9f3bf6bf63f2577186f1277871c966e0a16843 | wangchuan |1 |ngconsole-webpack-plugin.js |     国产化：打包配置
6e51b27975ddf9d168f269c02f0a49e7652c4e47 | wangchuan |1 |a719661d9 |     合并5.1.4-vpc
a719661d98ad775ba0ac4ee505e1f36587890e50 | wangchuan |0 | |     国产化：VDI客户端包
cc4081cd9e5015b658aff547f1c4b28b7da3c530 | wangchuan |0 | |     VDI客户端包
ecd06792b1c2adf599a31000cd4a0d4d960092f7 | zagger |1 |css/your_style.css |     镜像管理表格样式修复
881094f0661978ad764a35798fe37e2e7760ba20 | wangchuan |0 | |     build
21d4760cdb96ccef56c7d422536801493c517dc7 | wangchuan |1 |192a89757 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
c58e4c9a70f033d267dfe2d1c06a56ff34c1a342 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     IO次数：四舍五入
a00344aac1f2e2bbacd7df2fa3a78132be5c96a2 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：IO吞吐趋势
192a89757b7910e584e67c2db26a1bb0352a34d6 | zhangyao |1 |753f0e8fb |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
753f0e8fbaeba4e31e01794c4fe7c663974b1a9e | zhangyao |1 |views/vdi/common/account-password-modify.html |     修改密码时去掉对旧密码的校验
00d226890d00c85ee7c534b87b391b56c8bf6c33 | 0obuwawao0 |15 |js/vdi/spice.js; js/voi/hardware/controller.printer.js; js/voi/help/controller.deploy.js; js/voi/terminal/controller.terminal.js; views/idv/desktop/scene.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/desktop/personal.html; views/voi/desktop/roam.html; views/voi/desktop/scene.html; views/voi/dialog/hardware/upload_printer.html; views/voi/hardware/printer.html; views/voi/help/deploy.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     修改voi idv 左侧树支持水平滚动
4b18527184bba5aaf1dab2837caef5fcb2516ee5 | 0obuwawao0 |2 |js/vdi/spice.js; js/voi/help/controller.deploy.js |     删除一些注解
deba3a5effd143f9fdda33576c9b72ca716fc7fc | 0obuwawao0 |0 | |     voi 打印机联调打包
dfd453f74e4110c72fedec66d8d5a0106b7c5e09 | 0obuwawao0 |1 |views/voi/desktop/scene.html |     修改voi场景左侧树支持水平滚动
4fc0192bd90fd3c13385694c95a868da17ecaebc | 0obuwawao0 |16 |js/vdi/spice.js; js/voi/hardware/controller.printer.js; js/voi/help/controller.deploy.js; js/voi/terminal/controller.terminal.js; spice.html; views/idv/desktop/scene.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/desktop/personal.html; views/voi/desktop/roam.html; views/voi/desktop/scene.html; views/voi/dialog/hardware/upload_printer.html; views/voi/hardware/printer.html; views/voi/help/deploy.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     修改voi idv 列表左侧树统一为自动水平滚动，避免深级别无法显示问题
1d72911894ea019848523851fea5f4d5d8806991 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     分布式：数据盘替换按钮显示逻辑
c189c33afb37971f5de777bcb0e7d778a6b9174a | zagger |7 |css/your_style.css; js/vdi/desktop/personal-desktop-pool.js; js/vdi/desktop/personal.js; js/vdi/desktop/scene.js; views/vdi/dialog/desktop/newDeskPool.html; views/vdi/dialog/desktop/personal_new.html; views/vdi/dialog/desktop/scene_new2.html |     【管理台】-【模板】模板类型调整说明需求
5e72378241a84ed9f07feabb82b39144e6f83fbb | zagger |2 |js/vdi/desktop/personal.js; js/vdi/os-types.js |     系统类型-删除不需要的系统类型，删除个人桌面不需要的代码
e5845ff9a2900d69584a6d08fe0ca0932051ea83 | zhangyao |1 |b1fb28075 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
b1fb28075fab01efbe5156d48f687fa280b6607b | zhangyao |5 |js/vdi/desktop/personal.js; js/vdi/resource/console/controllers.js; js/vdi/user/common.js; views/vdi/desktop/personal.html; views/vdi/desktop/scene.html |     fix 15568，16572，16533，16456
3259f227b52989f9459f0f01558f7a0ba59cc4bc | zagger |1 |views/vdi/scheduler/disk.html |     去掉多余代码
d810f1a666a371fb8e3c1d80666fcf60531652e3 | zagger |1 |views/vdi/scheduler/disk.html |     loading 时不显示分页，看下效果
e708356d82bd2a27b3a2a0acefa5f5f70f8cacfd | zagger |0 | |     build for verify
6fe49abccce8d69d90049b4977b1bb9d697f06f7 | zagger |1 |e955e3868 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
e955e38686f8f01f700a555af9ae95543de41558 | zagger |5 |js/vdi/scheduler/disk.controller.js; js/vdi/user/admin-user.js; js/vdi/user/uaa.js; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     网盘参数整理-uaa导入帐号代码bug
8788f558b5bf121a9c0c36dec906115ce89b38dd | zagger |3 |css/your_style.css; js/vdi/scheduler/disk.controller.js; js/vdi/user/admin-user.js |     1.添加弹窗中 影响全局的样式 加了个over-flow：hidden；2.添加注释代码
57d87e92ab236ad3bd970fc6c7b82a6f33c0237c | 0obuwawao0 |23 |js/idv/desktop/controller.scene.js; js/idv/template/controller.template.js; js/idv/terminal/controller.terminal.js; js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/desktop/controller.scene.js; js/voi/help/controller.deploy.js; js/voi/template/controller.template.js; js/voi/voi.js; views/idv/desktop/scene.html; views/idv/dialog/template/merge_tpl.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/desktop/personal.html; views/voi/desktop/roam.html; views/voi/desktop/scene.html; views/voi/dialog/desktop/desktop_detail.html; views/voi/dialog/desktop/host_config.html; views/voi/dialog/template/merge_tpl.html; views/voi/dialog/terminal/pool_add_edit.html; views/voi/help/deploy.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     手动合并voi idv 5.1.4-vpc分支的改动
6d52836170a4d8a09b0ee71e0b5c2767318d1545 | 0obuwawao0 |3 |js/voi/hardware/controller.printer.js; js/voi/help/controller.deploy.js; views/voi/help/deploy.html |     voi打包自测
fc9f281fe900f2eaa3a33370b92d8ce94111c2a9 | zhangyao |1 |a32c4247a |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a32c4247a727758e8617474dd30d307e214f1fbf | zhangyao |2 |js/vdi/utils/ui.js; views/vdi/common/password-strength.html |     解耦密码复杂度和密码强度
222d46c5127885499a1b800716cb9b5a58d0125a | zhangyao |2 |js/vdoi/main.js; views/vdi/login.html |     修复登录跳转后，登录页面销毁时有残影问题
c9e6776455b6fd423dda638415f7039efcab0502 | 0obuwawao0 |1 |js/idv/terminal/controller.terminal.js |     idv终端载入显示效果
62b7b9708d524c9ffc0198ea77e5a876941d1d0a | zagger |0 | |     build for verify
aff00ff231780fea0e645f80148274bf85946c41 | zagger |6 |css/font-jj.css; fonts/icomoon.eot; fonts/icomoon.svg; fonts/icomoon.ttf; fonts/icomoon.woff; views/vdi/login.html |     添加字体库 + login登录tab页两个icon添加
549e9b91471208d0dacdaa4c8bb974e9af5481e0 | zagger |1 |2332dcbb5 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
2332dcbb512ddd1b8288315ad50d484a74b2c928 | zagger |2 |css/your_style.css; img/logo/vpc-fusion_zh-hans.png |     设计师换图
93e92dd6a082e44640c09ddbd9a8b9abaf26231e | 0obuwawao0 |5 |js/idv/template/controller.template.js; js/voi/desktop/controller.roam.js; js/voi/template/controller.template.js; views/idv/dialog/template/merge_tpl.html; views/voi/dialog/template/merge_tpl.html |     voi解决漫游桌面下载录像地址问题
ba9db9a50afdd7233ee38ae03b37baf88770200c | 0obuwawao0 |6 |js/idv/template/controller.template.js; js/voi/desktop/controller.scene.js; js/voi/help/controller.deploy.js; js/voi/template/controller.template.js; views/idv/dialog/template/merge_tpl.html; views/voi/dialog/template/merge_tpl.html |     处理模板合并窗口提示，处理快速部署
53ccd65b8040e7578e056023a6359e3bdee23f22 | wangchuan |2 |js/vdi/security/system/controller.security.system.js; views/vdi/security/system/security_system.html |     系统安全：启用/禁用策略优化
bb7a00be6cf0521af7e40a5cb5e3af307d6e91a7 | wangchuan |1 |views/vdi/security/system/security_system.html |     系统安全：启用/禁用策略bug
d8db747207bbb37d20118bfc2840d76fc054ae5a | 0obuwawao0 |3 |js/voi/desktop/controller.roam.js; views/voi/desktop/roam.html; views/voi/dialog/desktop/host_config.html |     解决漫游桌面上的一些bug
1f871ebd526db1d9b0e2c3d9fd4e6562f139beb6 | wangchuan |1 |views/vdi/dialog/security/client/manage_security_client.html |     需求变更。产品要求：管理终端详情改为和管理桌面那一样
2d592fe461c39d5186792c5db1dac66d7aa9f459 | zagger |2 |js/vdi/user/role.js; views/vdi/app-header.html |     dms功能移除
92c03f37d9d297ce9d7aa93298f1f66d4f2376f1 | wangchuan |1 |2a018aa9c |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
2a018aa9ce8c1d4151fb979924b33c3e580a80fa | 0obuwawao0 |1 |2a78eaeef |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2a78eaeefdea9f3fc499b1d86050eb64547d3763 | 0obuwawao0 |4 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/terminal/controller.terminal.js; views/voi/desktop/personal.html |     解决跳转搜索问题，保持唯一性以及筛选显示
c6241991909a6b681a494e3e59d62582178c9ce7 | zagger |1 |083875203 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
083875203a835d3c5057cb03dbc40834883dc59c | zagger |1 |css/your_style.css |     logo靠左的边距10px
49bf88321d45726b611a92b428064a916a31dbeb | 0obuwawao0 |7 |js/idv/desktop/controller.scene.js; js/vdi/terminal/controller.terminal.js; js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/desktop/controller.scene.js; views/voi/desktop/personal.html; views/voi/desktop/roam.html |     解决一批bug
51d66d0d4b85f23915f832cb24032ee11f5f0441 | wangchuan |1 |views/vdi/dialog/HA/new_ha.html |     新增HA提示
b88d18dd49c2c0ce00127fd81c329da67af754b1 | wangchuan |0 | |     build
0b156a9955fd3360933f674ae917045a1c1b172d | wangchuan |1 |8d5d141aa |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
fa1a8d95a81c333be9517f4fa0d5b634e0b9ec80 | wangchuan |2 |personal_login/js/webLogin.js; personal_login/selectDesk.html |     修改选择桌面样式
761a627c63b761014fa1b071386554a1337da64b | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：IOPS数据去掉小数位
8d5d141aa9bf88f5f18f65592d8076563bed4ffb | wangchuan |1 |7aa31d08f |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
f5283d0ca0ce842be2e34ff8bfba27e4a73572dd | wangchuan |12 |views/idv/desktop/scene.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/vdi/dialog/security/client/apply_security_client.html; views/vdi/dialog/terminal/terminal_schoolroom_add.html; views/vdi/dialog/terminal/terminal_schoolroom_edit.html; views/vdi/terminal/client.html; views/vdi/terminal/schoolroom.html; views/voi/desktop/scene.html; views/voi/dialog/terminal/pool_add_edit.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     超出显示...的树
b2e76a1e42b05dcade1ac771fd02a056189b3bc2 | wangchuan |1 |css/your_style.css |     超出显示...的树
aa6d359cf7becfff0eb92aedaa172cf9213cfdd9 | wangchuan |13 |css/your_style.css; views/idv/desktop/scene.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/vdi/dialog/security/client/apply_security_client.html; views/vdi/dialog/terminal/terminal_schoolroom_add.html; views/vdi/dialog/terminal/terminal_schoolroom_edit.html; views/vdi/terminal/client.html; views/vdi/terminal/schoolroom.html; views/voi/desktop/scene.html; views/voi/dialog/terminal/pool_add_edit.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     超出显示...的树
7aa31d08f23e2d7df1781be02e9440ea5aef4b51 | zhangyao |1 |views/vdi/desktop/personal.html |     fix: 16455
f6c97579c4eb2dff3a1a8ca8ae389c1e3b33165b | zagger |1 |views/vdi/dialog/desktop/personal_detail.html |     个人桌面详情-gpu代码隐藏
71b66ecd801687d174c23477fa54540be72f39b0 | zhangyao |1 |3fc68f6ba |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
3fc68f6ba88ae6a5e8d8fe0a7acdbe8395aeb9d6 | zhangyao |1 |js/vdi/help/quick-deploy.js |     fix: 16228
69c326eb32d1767127698dc2ac82e3329f78db14 | zagger |11 |views/vdi/desktop/personal.html; views/vdi/desktop/poolList.html; views/vdi/desktop/teach.html; views/vdi/dialog/desktop/personal_alter.html; views/vdi/dialog/template/template_person_config.html; views/vdi/dialog/template/template_person_register.html; views/vdi/dialog/template/template_personal_add.html; views/vdi/dialog/template/template_teach_add.html; views/vdi/dialog/template/template_teach_config.html; views/vdi/dialog/template/template_teach_register.html; views/vdi/resource/pool/host.html |     gpu相关的代码隐藏
886cccacb6e9730653702e5729c35ce0911b1048 | zagger |2 |js/vdi/template/controller.hardware.js; views/vdi/dialog/template/template_hardware_add.html |     硬件配置-新增-添加注释
b995789d834bd77293230be3d3f229facd7d015a | zagger |2 |js/vdi/template/controller.hardware.js; views/vdi/dialog/template/template_hardware_add.html |     隐藏-硬件配置-新增硬件配置-html和js中gpu显卡的相关内容
58cae0a4ca3f727efb68ec98db5cae39d0f5d39c | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求：IOPS数据去掉小数位
9f7e695749de4027a503802851317cd27abae1f9 | 0obuwawao0 |1 |js/voi/template/controller.template.js |     voi打包自测
65a6579ed4606d3aa9a657907d9714bcdeec0570 | 0obuwawao0 |8 |js/idv/template/controller.template.js; js/voi/template/controller.template.js; views/idv/dialog/template/add_tpl.html; views/idv/dialog/template/edit_tpl.html; views/idv/dialog/template/register_tpl.html; views/voi/dialog/template/add_tpl.html; views/voi/dialog/template/edit_tpl.html; views/voi/dialog/template/register_tpl.html |     修改voi idv模板新增，编辑，注册范围下拉框
0ffb1cf908dd25c8d96522fb1ae021cc957931a4 | 0obuwawao0 |2 |js/idv/template/controller.template.js; js/voi/template/controller.template.js |     修改voi idv注册，编辑，新增模板时区域的下拉样式
3372f2c6905e02bbd1a24fe3fa1aed0f02fd170e | 0obuwawao0 |8 |js/idv/template/controller.template.js; js/voi/template/controller.template.js; views/idv/dialog/template/add_tpl.html; views/idv/dialog/template/edit_tpl.html; views/idv/dialog/template/register_tpl.html; views/voi/dialog/template/add_tpl.html; views/voi/dialog/template/edit_tpl.html; views/voi/dialog/template/register_tpl.html |     修改voi idv注册，编辑，新增模板时区域的下拉样式
af2e6f5b3318c501f103c1ae331432460091db5e | zagger |0 | |     build for voi test
141c9f7c8585c186496118815004bb06205e8707 | zagger |1 |fa5d2d54d |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
0e98f29d844616175218e2b00b8b1f5103e24f43 | 0obuwawao0 |4 |js/voi/desktop/controller.personal.js; js/voi/template/controller.template.js; views/voi/dialog/template/edit_tpl.html; views/voi/dialog/template/register_tpl.html |     正在改注册下拉框树
fa5d2d54dd79b76132b0d6110f4930848519b41a | zagger |1 |js/vdi/user/common.js |     多选框兼容voi和idv
8b6350818f129b37a233cea168a8435f1a26991e | zagger |1 |js/vdi/user/common.js |     多选框兼容voi和idv
76bccd85f1a279fc7d34219eda306da3d0218a86 | 0obuwawao0 |2 |js/voi/desktop/controller.personal.js; views/voi/dialog/desktop/add_personal.html |     去掉新增个人桌面时的3种类型
f192194d1a221ce04bf2e1ee59455b1a1b5291ea | wangchuan |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     设置终端
5125f2baab2f3b4aa303a8495d8c4f6cad6d61d4 | wangchuan |1 |2b6fadce7 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
1cda7b7a2f3bbd1476f1ff45b0f163622cd17e02 | wangchuan |2 |js/vdi/resource/storage/storage.css; views/vdi/resource/storage/disk.html |     分布式：样式
b945449f27abcadaf82715e9ed1a59247f5fdcb3 | wangchuan |5 |css/your_style.css; js/vdi/resource/storage/controllers.js; js/vdi/resource/storage/storage.css; views/vdi/resource/storage/disk.html; views/vdi/resource/storage/storage.html |     分布式：样式修改
63775d3ef8fe67c626c76cac8a80e56adcf4a783 | zagger |1 |js/vdi/user/role.js |     角色删除逻辑修改
2b6fadce79c4da3371248a95145e16465b98862f | zagger |0 | |     build for 91
52a291e803e38f67383fb9a0e12ff570154e4678 | 0obuwawao0 |1 |76f9ce5d8 |     合并修改
5d2b612608af9c08a6ccc712aed681937ac2eb17 | zagger |1 |84587d646 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
84587d646df310c6ebe2d5e7fc83ec0c1a423819 | zagger |1 |js/vdi/user/role.js |     角色删除逻辑修改
76f9ce5d848b0ae462a7f9de088543c9f9bd7f85 | 0obuwawao0 |8 |views/vdi/system/hardware_tab.html; views/voi/desktop/personal.html; views/voi/desktop/roam.html; views/voi/desktop/teach-list.html; views/voi/dialog/desktop/add_personal.html; views/voi/dialog/desktop/desktop_detail.html; views/voi/dialog/template/add_person_tpl.html; views/voi/terminal/client.html |     去掉不要的展开列表功能
5bc3c2695ab4f241832c79df834e999e49df306b | zhangyao |1 |b67d26493 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
b67d26493160bcdb92f7929237c1c44931e01d80 | zhangyao |1 |js/vdi/desktop/personal.js |     fix: 16388
d60d110e65473f8d0f9b959ae6f0f708536dd10c | zagger |4 |views/vdi/desktop/personal.html; views/vdi/desktop/scene.html; views/voi/desktop/personal.html; views/voi/desktop/teach-list.html |     移除-域操作移出需求说明
f6b78f22e845ed25fc2eaac8a4a62accabbdd81f | zagger |1 |js/vdi/help/controllers.js |     袁阳曰：小于0的强行改为0
dc180f38d2b830e8aba698ef2ce1866cf5801d2f | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     uaa帐号改变传参方式
2a93a7119e36f848498afa467f37712eb14727f5 | zagger |1 |js/vdi/user/role.js |     16394 【角色权限】有dms权限的管理账号登录管理台功能结构树会多一个dms
e937bc145ce8c0578decfbcfd2230a162ad1a19c | zagger |2 |css/your_style.css; views/vdi/help/deploy.html |     快速部署 袁阳需求强行要修改这里的按钮样式
b5aa3f8ecd8bc9779773a98cac8c2a129a191c81 | zagger |1 |js/vdi/help/controllers.js |     袁阳曰：小于0的强行改为0
8e002741f806efd0fb4ecc14898f38ad7a0cf3b6 | zagger |0 | |     build for 91
099ba7a991b046f53aad9b925fa0c322ee1910a5 | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     uaa帐号改变传参方式
c43acbaf2bdba8ca52208c83b201a5281309280c | zagger |0 | |     build for verify logo img
44239b309cacc2cc099eec0f4e935f8abf6954f2 | zagger |1 |img/logo/vpc-fusion_zh-hans.png |     换为最新的logo图片
4290de4cc13bb942217be0bef36cc87e4954faec | zagger |1 |js/vdi/user/role.js |     角色删除-去掉之前的判断
ee18e1f0e768ce071d0f78fab4acff6499651281 | zagger |1 |js/vdi/user/role.js |     16394 【角色权限】有dms权限的管理账号登录管理台功能结构树会多一个dms
a3220397c4ae74d4167b2141fab1dd4c90e5f171 | zagger |1 |js/vdi/user/role.js |     角色能否被删除不能通过名称去判断，暂时改为由后端去判断
d34d19cb91a1529ea2c6423fdf1486c5ac99f6f2 | wangchuan |1 |css/your_style.css |     样式修改
369d7640d2c5efde716691e6b70f6e485dfde4df | zagger |1 |views/vdi/login.html |     去掉登录界面温馨提示
b8ced109a91ccc3df2f2b53bcad50e963f950aa9 | zagger |2 |css/your_style.css; views/vdi/help/deploy.html |     快速部署 袁阳需求强行要修改这里的按钮样式
f54d0cc1245d03a449004eba93c673e7c1ee856b | zagger |1 |ngconsole-webpack-plugin.js |     临时解决读取不了翻译代码问题
8da36ac6f12540fcd590b896d66c62e51414a0d9 | wangchuan |1 |views/vdi/resource/storage/disk.html |     产品要求：去掉裂脑时间
b70bd36764a52004cef69c84242c798da846dbf4 | wangchuan |0 | |     build
19fa6f9ff36e3ca4ddf7ccf59703f8a870bf42ba | zhangyao |1 |1f02b0b66 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
1f02b0b6605fcc802675e8eb611ef1c51d9dc3e2 | zhangyao |1 |views/vdi/desktop/scene.html |     添加 title
58d6c9b6cffcf64f3b509a2662f0880f890511eb | wangchuan |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     设置终端
a93e362cd8b0806b8f154439add9dd6df2612c50 | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/dialog/security/client/add_edit_security_client.html |     终端安全：新增编辑
bcaccc4c059ff0af17ab0fa2b9b457c9039e92d4 | 0obuwawao0 |1 |013c95b57 |     voi打包准备
013c95b57d6524f1c15152b9d03a887c6cd83c5c | 0obuwawao0 |2 |js/voi/desktop/controller.personal.js; js/voi/voi.js |     修改个人桌面下拉框
758cb5b0bb125109c7f609abd6cd5ee34c618f09 | wangchuan |1 |fc02f9f35 |     Merge branch '5.1.4-vpc' into 5.2.0-uos
9db06542877601cd3f135fb3830dd7e9790e3b79 | wangchuan |1 |08b740bbc |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
fc02f9f352c3f93ac71497d7875d6ccf3912890a | zagger |1 |js/vdi/menus.js |     隐藏网盘功能
08b740bbc5c42e91792241d2533853f68e165f01 | zagger |0 | |     build for verify
5af22c3d9c73ef20b7e080921d579d0de91b0b86 | zagger |1 |js/vdi/scheduler/disk.controller.js |     初始化网盘分页页码
e227588b7438a8d6e03e0824debd48514fa385f7 | zagger |2 |js/vdi/scheduler/disk.controller.js; views/vdi/scheduler/disk.html |     处理清空页码数量所导致的bug
2c6a7b9a8cb02a37c43c3e253dea69ba0db74f31 | zagger |1 |views/vdi/dialog/desktop/personal_alter.html |     个人桌面桌面修改始终disabled掉镜像分层复选框空间
22c57fc4ebba0cb252e4030af77b7746dc1ab067 | wangchuan |1 |js/vdi/init.js |     杨燕思要求：初始化时查不到时间就一直查
0a4b368e06ad1169c7a48f907208f2bab40856fb | wangchuan |1 |js/vdi/summary/controllers.js |     概览修改
ca08f225df88922e2de3b584db267f9eab5d2803 | zagger |1 |35c4ff5e0 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
35c4ff5e039e0cc9785fb7613d1395cd6efd63fc | zagger |1 |views/vdi/dialog/scheduler/disk_show_detail.html |     网盘个人信息详情显示bug
7a7e162b8afd8bfa4ed1283bed7efe9bec67f24f | 0obuwawao0 |3 |js/vdi/spice.js; js/voi/desktop/controller.personal.js; spice.html |     在编辑模板界面加入载入打印机驱动
e8d7d473730e9e8015ef82365b83ed579605f784 | 0obuwawao0 |2 |js/voi/desktop/controller.personal.js; js/voi/voi.js |     修改个人桌面下拉框
97855cfc9cdca01d6f40a686da6d2bc74b5c7db1 | zagger |2 |js/vdi/desktop/personal.js; views/vdi/dialog/desktop/personal_alter.html |     去掉镜像分层代码
801de889460b9ac833e19e2068206b2b9d0d1812 | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/dialog/security/client/manage_security_client.html |     终端安全：管理终端列表过滤bug
5875ac500e8a4c0c920600ec035fec93b41f567a | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     磁盘是否可以替换逻辑更新
67a3badd78631b3ab5cefcf731544128301fbc39 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     产品要求:副本集只剩一个磁盘，不显示替换按钮
5e7e60108e11416d55689a3090ac1a61071039cd | wangchuan |0 | |     build
b36ef144bc73d375d00cf2ff3d99ec97f5c2ce2a | wangchuan |1 |314df0010 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
a2abf17d710145abec6d07b40f6247408e9b6237 | wangchuan |2 |js/vdi/system/system-logo-settings.js; views/vdi/system/set-general.html |     仲裁IP始终显示
314df00108d49517d2cc684e1f21cd2cdce9065f | zagger |1 |js/vdoi/main.js |     dms返回的路径去掉/
5428e27ff78f3d346b78b2d4baddd9a6f914e0a5 | zagger |0 | |     build
a7f3d41ef090b834c2b6ac3cbb7a780aeab7037b | zagger |1 |js/vdi/scheduler/disk.controller.js |     加上排序参数
e133cca86cefb93eebd040b8b48f4429d755e6fe | zagger |0 | |     build
f7e29a08b614abfbc1e546a6230071c058dc5a3d | zagger |2 |js/vdoi/main.js; views/vdi/app-header.html |     dms加上新接口来返回跳转地址
0be5a7e295046301b5502799d26baafc336b380a | zagger |1 |js/vdi/scheduler/disk.controller.js |     网盘加注释+加上一个固定项
832cede8c774eeeb0897cdea04db269cc0dc9b4d | wangchuan |1 |js/vdi/resource/storage/controllers.js |     IO时延echarts
6960a6ed1d3136b0ae4d421897269d9b5022e67e | wangchuan |1 |js/vdi/summary/common.js |     bug修改
adb3ad84e5ff66c9c09a31ff3ebef6f0fcadf405 | zagger |1 |js/vdi/vdi.js |     去掉无用代码
4610912ef77b09650c69dd2f671c033340c89fca | zagger |0 | |     build for verify
977991aca032814a6a3cb8bccaa83cac6edb93bb | zagger |1 |js/vdi/scheduler/disk.controller.js |     分页输入框清空时，如何获取分页
c6a3044c016916a4f35663abb9e4d191da65e1fb | zagger |0 | |     build for verify
ceae6a2f8b66a15e794cfaf2c9b203a42f2a4323 | zagger |3 |js/vdi/vdi.js; views/vdi/scheduler/disk.html; views/vdi/user/admin.html |     bugs
db394c1104f62c2cc5df47bf05fe0b3839c37bb2 | zagger |1 |views/vdi/dialog/scheduler/disk_show_detail.html |     网盘-uaa管理帐号详情部门显示问题
fb3c63cb79e083891e7431cfc025174b99da311e | zagger |1 |js/vdi/scheduler/disk.controller.js |     build for verify
b87e0aac9849c97e8378bf8738cfb9e140670ad6 | wangchuan |0 | |     build
28f6bf045189ec5dda65272181173cc6b145f0ba | wangchuan |1 |89e048828 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
89e0488280bd9a0f29006d231fcf8d9a27cf9a15 | zagger |1 |9b6563e50 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
9b6563e504ff24ab8ccf3580ee521c4f982ef120 | zagger |4 |css/your_style.css; js/vdi/scheduler/disk.controller.js; views/vdi/template/teach.html; views/vdi/user/admin.html |     build for verify
b3d296a70dc78ae9e8859544b542ace7508f2812 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求:有一个节点异常,则所有节点显示异常...
4d65928a7e4319ff0872b9689c2f80c1b28aedaf | wangchuan |1 |js/vdi/resource/storage/controllers.js |     产品要求io时延显示节点IP+磁盘名称
c780a0d0a61365c3ade1b1b0e401e63d17f1d82c | 0obuwawao0 |2 |js/voi/terminal/controller.terminal.js; views/voi/dialog/terminal/printer_bind.html |     修改打印机绑定提示
7fece634d1a43bf3b63b6a8b568f6a61b4de84ee | zhangyao |1 |189259d85 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
189259d85163782ed86eff396d1e873210f11582 | zhangyao |2 |js/vdi/desktop/styles.css; views/vdi/help/deploy.html |     修复bug
189441ea6832cda5ad11e1c8991af5d3de53e794 | wangchuan |2 |js/vdi/resource/pool/controllers.js; views/vdi/dialog/resource/pool/config_storage.html |     录屏存储不支持设置为分布式卷组
d92ff77fbc617940eb4232edb7634f004e793a03 | zagger |0 | |     build for5
99ad44eba546734159592b51975ba7954fc52136 | zagger |2 |js/vdi/scheduler/disk.controller.js; js/vdi/vdi.js |     build for5
4ecdbc6a6eac31382f3c399d58549ab1fee43e9c | zagger |2 |js/vdi/scheduler/disk.controller.js; js/vdi/vdi.js |     build for4
15d93f22e74395c892335381114a724d495549ca | zagger |3 |js/vdi/scheduler/disk.controller.js; js/vdi/template/controller.teach.js; js/vdi/vdi.js |     build for3
d60fbb57e6977bd22addc40d36e44ae8831e310d | zagger |1 |js/vdi/scheduler/disk.controller.js |     build for2
20576accc59361882605a973d38e4bdbb76e8f2e | zagger |2 |js/vdi/scheduler/disk.controller.js; views/vdi/scheduler/disk.html |     build for
0cffbb00537bc79f0d3015ef0e6d836892607506 | zagger |1 |b4b18e687 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
b4b18e687f90946ffc2e4af9ea63427500b4ec68 | zagger |1 |js/vdi/scheduler/disk.controller.js |     轮询改为了timeout，随之要去掉abort逻辑
3a4e6f23b950ba4aaa1be7ff4a4d0a19091f8a3f | zhangyao |1 |2537b263c |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2537b263cc249c4f5235e22e176aa33b8e86dfeb | zhangyao |1 |js/vdi/security/style.css |     详情保持一致
8bd735e37373bbb846ec452b46c485d70857ad59 | 0obuwawao0 |0 | |     voi打印机自测
507a7e7404e6eec9f75171fc20a4e68166fd60a1 | 0obuwawao0 |7 |js/voi/terminal/controller.terminal.js; js/voi/voi.js; views/voi/dialog/hardware/upload_printer.html; views/voi/dialog/terminal/printer_bind.html; views/voi/dialog/terminal/printer_bind_detail.html; views/voi/hardware/printer.html; views/voi/terminal/client.html |     完成打印机解绑，查看打印机详细
64e98a8313e62c84ba7e8acc5f9e1af7df41a0ad | wangchuan |1 |views/vdi/resource/storage/disk.html |     分布式存储：监控图表重绘前清空
9341a06a6f38acf5a6a725907e9dec7c04de99ad | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储：监控图表重绘前清空
11e6a5d0a413696d0889f8f10adf8234c75f5f6b | wangchuan |1 |js/vdi/summary/common.js |     扩展uiEcharts
fa9bca39ec404d66f1a137b12def7b2c62bf31b0 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储：监控echarts优化
719965eae89b56e47e27b9645d5509e9863a498a | zhangyao |1 |de0426be9 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
de0426be935dc0b4413088305d6df2a0761b9fe6 | zhangyao |1 |js/vdi/help/quick-deploy.js |     fix: #16225
8318d1949c46e57527a110418ebb5b5c7e4f169e | wangchuan |1 |views/vdi/dialog/security/client/manage_security_client.html |     管理终端：样式修改
2998bbc179e304b3411f395367ca66b6a063cabe | wangchuan |1 |img/clientLogo/vpc-fusion_zh-hans.png |     更改管理台vdi客户端默认logo
534af046b29143bc4cb405645769da350fdfcadf | 0obuwawao0 |1 |js/voi/hardware/controller.printer.js |     添加打印机控制器
aa042fe31518eab2b8527d509221b8106e45a011 | wangchuan |1 |js/vdi/summary/common.js |     恢复历史文件，option变化时去掉更新echarts前的clear
0ea1287196ad2ae7765065b46d5266f83d051a9c | 0obuwawao0 |9 |js/vdi/system/index.js; js/vdoi/system.js; js/voi/voi.js; views/vdi/system/hardware_tab.html; views/voi/dialog/hardware/edit_printer.html; views/voi/dialog/hardware/upload_printer.html; views/voi/dialog/terminal/printer_bind.html; views/voi/dialog/terminal/printer_bind_detail.html; views/voi/hardware/printer.html |     加入打印机功能
33cfc788769284425b32a726140732324891ae53 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储：监控echarts横纵坐标自动适配
9663612347a67169f12d47206015f777ee8923a5 | 0obuwawao0 |0 | |     解决voi bug测试
2de6b13c41dbc8d374f716e453612facd477ace1 | 0obuwawao0 |2 |js/idv/terminal/controller.terminal.js; js/voi/terminal/controller.terminal.js |     解决终端online状态获取bug
b2ef88ee2a1515564e739738dee24b899f2df278 | zhangyao |1 |08950dba3 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
08950dba35c3e31cd90ed88b846b85f8bb191386 | zhangyao |3 |js/vdi/help/system-upgrade.js; js/vdi/help/upgrade-server-modal.css; views/vdi/help/upgrade-tab-vdiclient.html |     fix: #16206
099c1433979a3f0715ca1d80114514bed8a86e72 | zagger |0 | |     更新获取管理帐号假数据
9dfa7ed147c5244eae9a41108d63dbb55a77f95e | zagger |2 |js/vdi/desktop/personal.js; views/vdi/dialog/desktop/personal_alter.html |     个人桌面 修改桌面-帐号树结构-去掉uaa
abddbbe20e5f647daa5c139d26f99444c0832358 | wangchuan |2 |views/vdi/terminal/client.html; views/vdi/terminal/schoolroom.html |     idv区域管理、终端管理样式
74db64d6a5382ecc7d64101fa0ba82ab0477c243 | wangchuan |1 |views/vdi/dialog/security/client/add_edit_security_client.html |     终端安全：新增编辑样式
9d93801e86be2670c1d4cbbbd1b69a87cc47ea69 | 0obuwawao0 |1 |js/voi/desktop/controller.personal.js |     修改voi个人桌面编辑时下拉树结构
846a3cea4ed767b36de1419d0bba91a616dcaa3a | zagger |1 |js/vdi/desktop/personal.js |     //胡海曰 镜像分层开启需要过滤boot_index为1的磁盘
019094256e56092a8d6f791efa7dd458b2366797 | zagger |1 |js/vdi/monitor/common.js |     highchart图受到左侧菜单栏动态宽度的影响
fb0d8e1f12510377bb61946997cd222a8901eb1c | zagger |3 |js/vdi/system/system-settings.js; js/vdi/user/common.js; views/vdi/system/set-general.html |     其他小问题
ac449624f2de6568e394a40e6b92250025daa591 | zagger |2 |js/vdi/auth/controllers.js; js/vdi/utils/user.js |     锟哥bug获取token的两个地方分别加上参数
fbdfedf14a69c59ce984fa2ed76bfb1f12a879a4 | wangchuan |3 |js/vdi/desktop/personal.js; js/vdi/terminal/controller.terminal.js; views/vdi/desktop/personal.html |     跳转到终端
7f2f1b41b9070f05cd0d1bfbc5116bf5718c3734 | wangchuan |1 |js/vdi/template/controller.teach.js |     公共模板-镜像管理：添加分布式存储tab
80291bd7c754ec50622a383572554e2e561aea3f | zagger |1 |views/vdi/system/set-general.html |     统一配置邮箱服务器验证邮箱规则
411f534afe4b3bffafcd41a0b173e30a1b251b38 | zagger |1 |js/vdi/system/system-settings.js |     bug#16131 【通用设置】必现-配置邮箱服务器处输入邮箱信息后点击取消，输入框报红
6df7725ea932ea25b25e40aa24b6f4a7485e346e | wangchuan |0 | |     build
dcb9b3517c66fc1bba6f2e9c4cfee6db2ef071d2 | wangchuan |1 |74a0e5b1a |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
74a0e5b1a8b0331134dfd09cd18be5e2b5cf6647 | zhangyao |3 |js/vdi/template/common.js; views/vdi/security/desktop.html; views/vdi/security/group.html |     修复列展示问题
051f0e991b068416ea3241b6c9475ca6a3c78c56 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     分布式存储：对接监控新数据
d0a0fa5bad0552920fefc798888ab26e2b140496 | zhangyao |1 |a87755e96 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a87755e96dbfb71fe11665ea8ed3a8c548f5fc77 | zhangyao |0 | |     idv 打包
1d19d4566811a719a881adf02ba4e4fd048cac89 | wangchuan |1 |views/vdi/dialog/resource/storage/new_storage.html |     研发讨论，去掉添加存储处的录屏存储下拉选项
1e0d9a43de465fcc5b330f67a712d535e37d1622 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     挑选磁盘优化
e925b4aa08d0bf3719ab02922e6b593c325b2feb | wangchuan |1 |views/vdi/dialog/resource/storage/add_bak_disk.html |     分布式存储：添加热备盘提示
d0faedaaa87f299783a3230cab9e5f834cfde03c | zagger |2 |js/vdi/template/controller.teach.js; js/vdi/user/common.js |     16118 【vdi-公共模板】vdi公共模板执行注册模板，指定区域里面有voi和idv的教室信息 16124 【管理账号-权限设置】权限设置中没有显示voi和idv下面的子区域
fc8fc48caf23ee4236958fcb87c7d88648c8d0e2 | zagger |1 |1aa54a16e |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
1aa54a16edf547669be0c881720ba1d1c3189bce | zagger |1 |views/vdi/common/select-multiple-dom.html |     去掉管理范围的userCommon-tree样式类
4828ab5efaf0f649f39a2869a356ae1cb4148149 | wangchuan |0 | |     build
1b0b6d766eb109420731da393e71acee1447047b | wangchuan |1 |ed2a478ae |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
ed2a478ae0466b9c09dd4017a2d2ab960da0c391 | wangchuan |0 | |     VDI客户端包
67444c0fb5d23cdd884aae12feb3b2c09ecefd30 | wangchuan |1 |js/vdi/desktop/common.js |     桌面-高级：存储设置默认选第一个不为disabled的
f458f2aef613fc89fbc6b42ad449cbe587bdb2df | wangchuan |3 |views/vdi/dialog/security/client/apply_security_client.html; views/vdi/dialog/terminal/terminal_schoolroom_add.html; views/vdi/dialog/terminal/terminal_schoolroom_edit.html |     应用终端、vdi新增编辑区域：区域树鼠标悬浮提示
4ca55b348ca93772c54b205c24cef780a0ab06f2 | wangchuan |0 | |     idv包
ef66872df6db0829f59ecf25882e2a7320eda47b | wangchuan |1 |d0b96c9dc |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
bb99b9eeb1f3a2b31dcf2426b7e41d3be634e0a8 | wangchuan |1 |views/vdi/terminal/client.html |     vdi终端：去掉查看桌面
0aaff8418aebefe10f8c55436afa3fc0a710d7fe | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式：监控新数据
9c1859dbff05b935824dbb5c2276094dd294845c | wangchuan |3 |js/vdi/vdi.js; views/vdi/dialog/desktop/host_config.html; views/vdi/dialog/resource/pool/config_storage.html |     select禁用选项
c517a5e089f55c5f79c1b8131e485e7be03ab213 | wangchuan |1 |views/vdi/dialog/desktop/host_config.html |     恢复历史文件
d0b96c9dcc1a242a3ac538fa7c02213c73a38623 | zagger |1 |adf743e04 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
adf743e0408e471d77e0d9b1b30d32aa822c99ca | zagger |1 |js/vdi/help/controllers.js |     授权激活+关于=》vpc激活标识+分布式激活标识引起的改变
a9d05f135f9f015dbce14009e46ae78fbfb0aa3c | wangchuan |1 |views/vdi/dialog/resource/pool/config_storage.html |     恢复历史文件
07632032bb04fe43513e197d721ae975cec0bb5c | zhangyao |1 |spice.html |     放开上传文件功能
64c249dafacd286862f2c4984e0639e9fd3c1513 | 0obuwawao0 |7 |js/voi/terminal/controller.schoolroom.js; views/idv/desktop/scene.html; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/desktop/scene.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     套用vdi树样式
c2fe379c41e33dfa375fd72cfd3828cf77962c27 | wangchuan |1 |views/vdi/resource/storage/disk.html |     被替换磁盘tip
019752ace74e8c52ce979a4e22f0e318669ab4ea | zagger |3 |js/vdi/scheduler/disk.controller.js; views/vdi/scheduler/disk.html; views/vdi/user/uaa.html |     1.网盘新增和解绑服务器端口号默认改为443 2.涉及到的树结构名称加上title显示全部名称
292aabb82da7934a36f63118a50592b348c1dd54 | zagger |1 |d525c2667 |     解决冲突
f37150e19c7e82e9edafdb76ffb2e84b6c1fd0b7 | wangchuan |1 |ffc57030b |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
290c4d3e17718f258b06c892f48521ab3405bed3 | wangchuan |1 |css/your_style.css |     所有树，横向超出隐藏
d525c2667a266e182a91c4db7b17eac80a5ae04c | zagger |1 |views/vdi/scheduler/disk.html |     网盘这里部门- 判断node.user_num != null就显示帐号数量
ffc57030b19f7af2d5fca79558452c446b74f817 | wangchuan |0 | |     build
1c5a9662afe11d16b683c9fa90b079b2888053bd | wangchuan |1 |b97d52297 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
c7dfec2028a2fe7c3f4dff1d4e5af2d3db412b05 | wangchuan |2 |views/vdi/terminal/client.html; views/vdi/terminal/schoolroom.html |     idv区域管理、终端管理：树结构超出隐藏
ba6e551282bc7903eace278af575966159aa18b3 | wangchuan |1 |css/your_style.css |     超出显示...的树
b97d522976b15799e22f5faa9b050b4a94d73bdd | 0obuwawao0 |2 |js/idv/system/controller.system.js; js/voi/system/controller.system.js |     voi打包自测
f6e7ef1166eb3fb56c7183f13fd5309f3800fc3a | wangchuan |1 |js/vdi/vdi.js |     IP范围校验bug
ce792672c561666d6fb99dc660cbb00e5df89608 | wangchuan |1 |views/vdi/dialog/resource/storage/replace-disk-dialog.html |     替换磁盘优化
1edb80bfe9c7bdf6cf54fd23460a95809b3d5c70 | wangchuan |1 |0b685abad |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
0b685abad88ac3265a44abddb3cc07c7d956d6c9 | 0obuwawao0 |7 |js/idv/desktop/controller.scene.js; js/idv/terminal/controller.classes.js; js/voi/desktop/controller.scene.js; js/voi/system/controller.system.js; js/voi/terminal/controller.schoolroom.js; views/idv/desktop/scene.html; views/voi/dialog/terminal/pool_add_edit.html |     解决idv场景排序问题
a12280a6981c9ec774341e17caac17cb3b9398a2 | 0obuwawao0 |1 |5c9e17fa3 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
db049969ed7b5d94751c9b5b15d7d58056084ea3 | wangchuan |1 |js/vdi/summary/common.js |     bug
e7e283c077eccd5a33c36c3cef1caf8e2e3e9c91 | wangchuan |2 |js/vdi/monitor/policy.js; views/vdi/dialog/monitor/config.html |     热备盘替换告警
c65474b9a5d61bfd1d92cd4a3601eae53aea2af9 | zagger |1 |5caa9a62e |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
5caa9a62ed1b55c8ac3f3bc84995c594bc98e379 | zagger |0 | |     build for verify
6fde250ff99006bfab0cda2e72dc58211f065794 | wangchuan |1 |f59dcaa54 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
5790a5c1ff4b078406f63bf3321085300fba9110 | wangchuan |6 |js/vdi/bootstrap.js; js/vdi/desktop/common.js; js/vdi/monitor/policy.js; js/vdi/resource/pool/controllers.js; js/vdi/system/system-logo-settings.js; js/vdi/template/controller.person.js |     分布式存储授权
f022c1f2b5128c8905475de8140dcc8a146cc2f8 | wangchuan |2 |js/vdi/help/controllers.js; views/vdi/help/activeAuth.html |     激活授权：分布式授权展示
f59dcaa54bee9cc77a113bea2bcba86e2540364f | zagger |1 |js/vdi/system/system-logo-settings.js |     去掉无用代码
798bf9d6fdf5d12f894af1cba0ba8bc2f9c01993 | wangchuan |1 |js/vdi/bootstrap.js |     分布式授权
5c9e17fa351db3c12475c82fa35b3f23c14aecd6 | 0obuwawao0 |1 |661aff58b |     合并修改
661aff58b2c02260b27cab1062501ed25035ae41 | weicong |1 |9f427e275 |     正在解决idv终端场景排序
61672af1cad0853dbc566300a22af9a7415e0287 | zagger |1 |51b9b7db8 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
51b9b7db889a69f47009a83366ed421b886e78a5 | zagger |2 |js/vdi/system/system-logo-settings.js; views/vdi/system/set-vdi.html |     vdi-logo上传等验证尺寸时机问题解决
99225388b00f209e0841c35c00862f1f42c4d803 | wangchuan |1 |5cd634a6d |     合并代码
2317723a7063340f1d67b426e233bfe074958563 | wangchuan |5 |js/vdi/desktop/common.js; js/vdi/resource/pool/controllers.js; js/vdi/resource/storage/controllers.js; views/vdi/dialog/desktop/host_config.html; views/vdi/dialog/resource/pool/config_storage.html |     分布式:授权到期
41954272fb72d19c0e36f74084ee92205e9c5b23 | wangchuan |1 |views/vdi/dialog/resource/storage/replace-disk-dialog.html |     替换磁盘：无磁盘提示
c1b0eb85ec06464b7f4cfcdf3d1670819355ca49 | wangchuan |2 |personal_login/js/rules.js; personal_login/views/user-form.html |     web桌面：用户名最短2字符，最长不限制
5cd634a6d70a8a471e1d9cc7bd1cced93581df6f | zhangyao |1 |js/vdi/desktop/personal.js |     个人桌面过滤模板字段修改
f6f87a4f489882d5bd18ee53c1b362ad99b75a90 | wangchuan |1 |23f064176 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
384e7825cf036b4da73ed9aa296678720fd2d1d0 | wangchuan |2 |js/vdi/resource/storage/controllers.js; js/vdi/utils/echarts.js |     分布式存储：监控echarts修改
9f427e275fe0582744ff8b51d572071b1756b1fd | weicong |4 |js/idv/desktop/controller.scene.js; js/voi/terminal/controller.schoolroom.js; views/idv/desktop/scene.html; views/voi/dialog/terminal/pool_add_edit.html |     正在解决idv终端界面上的一些问题
b40183aaefa048e3fdfa334f6931e20629f69960 | wangchuan |1 |js/vdi/summary/common.js |     echarts指令bug
23f0641761dfa4e962dcdbc1e241961592903cb1 | zagger |1 |js/vdi/menus.js |     菜单icon更换
e1ce15d63d8b9462b47e4ff93261d70380f3dfe8 | zagger |1 |views/vdi/user/uaa.html |     用户帐号-部门-icon换新
cb7a932a2eb8d7449f84cbc74b0e4c582be8698d | wangchuan |1 |a5d6a2471 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
1ed5ee6e933008f711afc755aa6963b7e6b4a6d5 | wangchuan |3 |views/idv/terminal/classes.html; views/vdi/terminal/schoolroom.html; views/voi/terminal/schoolroom.html |     区域管理：更换图标
eaf503902db902618b542d7d1a344ab3b27bcd05 | wangchuan |5 |css/font-jj.css; fonts/icomoon.eot; fonts/icomoon.svg; fonts/icomoon.ttf; fonts/icomoon.woff |     字体包更新
a5d6a247157919f419a18c06c3baab67b5a42f81 | 0obuwawao0 |3 |js/idv/terminal/controller.terminal.js; js/voi/terminal/controller.tab.terminal.js; js/voi/terminal/controller.terminal.js |     voi自测
aa8114bd96e3ad9e7f13ae7a993c4acb71186c44 | zagger |1 |afba3e677 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
afba3e6771e0d8c1b4d0b653caa9202ccc1758ec | zagger |3 |js/vdi/scheduler/disk.controller.js; views/vdi/dialog/desktop/personal_new.html; views/vdi/scheduler/disk.html |     个人桌面切换硬件配置和是否开启镜像分层-交替显示隐藏分层空间
f6bf8be8016368adc0b811171a9a706d5399cbc4 | 0obuwawao0 |1 |81bd62297 |     优化idv终端代码
54a079f3e405347bad81c3315f6db6164513f8f4 | wangchuan |1 |4b2e6fefb |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
5d104dbd2b13cec46e517991fbf292dd92e7db4e | wangchuan |3 |js/vdi/resource/storage/controllers.js; views/vdi/dialog/resource/storage/replace-disk-dialog.html; views/vdi/resource/storage/disk.html |     分布式存储：磁盘替换联调
4ae04d202c4e4ab74859a3ca386ae909dd409624 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     分布式存储监控联调
4b2e6fefbc67bd469dacec8c39c8ffb76c26ea91 | zagger |1 |views/vdi/desktop/personal.html |     个人桌面 镜像分层开启的 桌面 无法另存为模板
05b8f8278cd2ffe7b21424bef532586b76c526bc | zagger |1 |css/your_style.css |     表格 去掉斑马色
643c553423246473a77c991abd4e7e2a8b0bad0a | zagger |1 |css/your_style.css |     瓦片按钮颜色问题修复
d7145ce9d1db30e0a0771f2c4e2f2b541bcb944e | zagger |2 |js/vdi/template/controller.teach.js; js/vdi/user/admin-user.js |     获取所有区域的传参方式
81bd62297bdace826865db794f5e596698732191 | 0obuwawao0 |1 |5a20fe572 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
5a20fe57296db3fcb463c3fa07d236e564cd080c | weicong |2 |js/voi/dashboard/controller.dashboard.js; views/voi/dashboard/dashboard.html |     修改dash界面
bd78b2db3f6b0bd8e180e146ea70824566bc68b1 | zagger |0 | |     build
34827bc967830a13aaacf336d223dbb1dcefc4c7 | 0obuwawao0 |1 |cfaaf729d |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
cfaaf729ddacf3e71287e7b96cc70814fe2dfeea | 0obuwawao0 |2 |js/voi/terminal/controller.terminal.js; views/voi/dialog/desktop/add_personal.html |     解决个人桌面上判断镜像分层
c08df4d0d5ecb6c0388c681800efd849a818e010 | zhangyao |1 |views/vdi/security/group.html |     其它协议 => 所有协议
002c6fc92d0d84039a77e305ea1e72126a90eb8d | wangchuan |1 |2a631c389 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
bd869ad7693d1f3b0905907f5a9071bb4a5f0125 | wangchuan |2 |js/vdi/resource/pool/controllers.js; views/vdi/dialog/resource/pool/config_storage.html |     配置存储
2a631c38905326933712d010888147ed28040ad1 | 0obuwawao0 |1 |js/voi/terminal/controller.terminal.js |     voi终端修改代码格式化
b66f044c9d7ed8cd03897c19f07a3abf9d6a6938 | wangchuan |1 |js/vdi/resource/pool/controllers.js |     录屏存储位置优化
50e8588973a37e5de3ef1d8bb6cc7aa160054669 | 0obuwawao0 |1 |js/idv/terminal/controller.classes.js |     修改idv区域编辑ip
73ebb12bf048970ba4657bfd514cc92fdf1a7728 | 0obuwawao0 |2 |js/voi/terminal/controller.schoolroom.js; views/voi/dialog/terminal/pool_add_edit.html |     修改VOI区域IP终端
b4b259b2354119919404e2d7825742608091ea52 | wangchuan |1 |bebd5702d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
7dc3abf6aef80f0f26d0fe4341e624fd6aae37bd | wangchuan |2 |js/vdi/resource/pool/controllers.js; views/vdi/dialog/resource/pool/config_storage.html |     资源池-配置存储
bebd5702dee6c00092314ae07d004f8232084074 | wangchuan |1 |1172595c3 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
7aeb8351277093828df2315bd7ff62e84986c8d0 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     卷组详情饼图优化
f3f7c0e3c8ca11766f38800df647dfb8ad64caa9 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     自动修复策略优化
1172595c307bbe7f0e2a9eaee319f317fd41a1f9 | zagger |1 |85a0a0bde |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
85a0a0bded9850d05d88ce97856c7d00ed524a4f | zagger |7 |css/your_style.css; js/vdi/template/controller.teach.js; js/vdoi/template.js; views/vdi/dialog/template/template_teach_add.html; views/vdi/dialog/template/template_teach_edit.html; views/vdi/dialog/template/template_teach_register.html; views/vdi/dialog/template/template_teach_save_as.html |     vdi模板区域范围选择修改
6cacacc402011229e30c1faadce87ba424dd09db | wangchuan |1 |746b9de97 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
4c876c024950dfe7c5ebf4fff6f637b564cd7356 | wangchuan |1 |views/vdi/dialog/resource/storage/config_repair.html |     自动修复策略弹窗
746b9de97d6d543fe84ee3a0468b72173d1c755f | wangchuan |1 |7b554ab39 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
50b025ff296ca642f70fb974d43d62a6cdf81247 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/dialog/resource/storage/config-strategy-dialog.html |     自动修复策略联调
7b554ab398b0ec1724abae9ad1eb1aa7a7284d94 | zhangyao |1 |js/vdi/config/http.js |     spice 页面长时间未访问管理台退出优化
495fd4f5f0b73e6572e1cff1f01dd4176749f240 | zhangyao |4 |js/vdi/system/system-log.js; views/vdi/system/admin-log.html; views/vdi/system/backup-log.html; views/vdi/system/user-log.html |     fix: #15818
b59de294d62725c686106e5135b6cb906c541657 | zhangyao |1 |js/vdi/split.js |     裂脑修复接口发送到主控
95d889d382e8534935ebd2d61341ba0aa0d7a981 | zhangyao |1 |js/vdi/resource/console/controllers.js |     切换主备控时请求发给主控
1fad0b16d3dece20a8db0cb30e3333d5e346a4bd | wangchuan |0 | |     build
db581064c0b63ba25bd2401b9fcae739e8be47af | 0obuwawao0 |1 |js/voi/terminal/controller.terminal.js |     解决voi的一些bug
e350a9c18fbe3172de91488a65894755bf3b98b8 | zagger |3 |css/your_style.css; views/idv/system/set-idv.html; views/voi/system/set-voi.html |     voi,idv-系统设置页面空间禁用背景样式
afaefd0dbc3006778249818af929da28cf863599 | zagger |1 |327b01dea |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
327b01deac8d5af9f2fe6a0340ccee7fae0bc58b | zagger |2 |js/vdi/help/controllers.js; views/vdi/help/activeAuth.html |     about+授权激活界面
243fd59152d50e6773fa809245779232b23b8afe | wangchuan |1 |03c1cdf7a |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
4e4beca5616f3550cfc00201b04d28adbe06b712 | wangchuan |9 |js/vdi/bootstrap.js; js/vdi/monitor/policy.js; js/vdi/resource/storage/controllers.js; js/vdi/system/system-logo-settings.js; js/vdi/template/controller.person.js; views/vdi/dialog/monitor/config.html; views/vdi/dialog/template/template_imgManage.html; views/vdi/resource/storage/storage.html; views/vdi/system/set-general.html |     【分布式存储】未激活/授权到期
edf9ea6a3abf08f08124a9cea80276469588fbb5 | wangchuan |1 |js/vdi/security/system/controller.security.system.js |     系统安全：修改删除规则弹窗标题
03c1cdf7a38f815990535cf551108a464f82e4c2 | zhangyao |1 |d8ed96b50 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d8ed96b5044a148fe2960df756bea8bf40920038 | zhangyao |2 |js/idv/desktop/controller.scene.js; views/idv/dialog/desktop/add_scene.html |     修复IDV新增场景无法显示公共模板的问题
6bcb30c57c33aed576cdaf72d472ee736d58180a | wangchuan |1 |a368787bb |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
d25c8a72b7c8fcc2482990376b0dcfc1e84b097c | wangchuan |1 |js/vdi/summary/controllers.js |     概要修改
a368787bbb4b12b454b3df99c3856686dfe3fad1 | zhangyao |1 |18f3cbf1f |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
18f3cbf1fbe10b748728acdc905d8f156bc61c08 | zhangyao |1 |views/vdi/desktop/personal.html |     屏蔽移动至入口
829a0380d7106bf31e3eb97e07c400c7195ab131 | wangchuan |1 |b4297d8aa |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
4c3f2004b41b46333818ff65cfbc3e6cbc4d8a0b | wangchuan |2 |js/idv/terminal/controller.terminal.js; js/vdi/terminal/controller.terminal.js |     vdi，idv终端管理bug
125a4427c5030eaae9c1df2d9c45c4cb876d9666 | wangchuan |5 |css/your_style.css; js/vdi/resource/storage/controllers.js; views/vdi/dialog/resource/storage/add_disk_group.html; views/vdi/dialog/resource/storage/replace-disk-dialog.html; views/vdi/resource/storage/disk.html |     替换磁盘
b4297d8aaa73b625266075719c228ec2e96c5a86 | 0obuwawao0 |1 |views/voi/dialog/desktop/desktop_detail.html |     修改了桌面详细
e25c38630355e65a7472e7863c2633fdc1ab5020 | 0obuwawao0 |1 |js/voi/voi.js |     voi打包测试
772fd4b44d6e4cb9a6be09f02c9bab7f005ae561 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     删除分布式存储，始终刷新列表
80e5170d6633c72b36f5f324d9b0bec2f41e9458 | wangchuan |0 | |     客户端包
28f492f090ed33e545e61a04fec0bd58a554bc14 | wangchuan |0 | |     客户端包
7d2c33aaec42fa95688d98694c18b9bca70347f3 | 0obuwawao0 |1 |views/idv/template/teach.html |     idv模板解决 注册模式下 不显示详细
e4d2fd7364ec0d5ebb32340c8e83e58d99f17f91 | zagger |1 |views/vdi/system/set-general.html |     15804 【系统设置-配置认证服务器】端口号中输入小数，输入框没有标红提示
4872d7abf1c5fa5df518ffc805c3dd33ea7e2111 | zagger |1 |views/vdi/template/teach.html |     教学模板 瓦片 判断darken还是primery 条件不一样 现改成一样
beea7998f3abfb8a146178a7fee8ed5305c69801 | zagger |0 | |     build
69329e46c2517b178aaa64de6c1b2a4471e45441 | zagger |1 |4297f9d5c |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
4297f9d5ccfed37f53bf221b8b9f8e9223df6721 | zagger |1 |js/vdi/desktop/personal.js |     镜像分层bug
a49b3a93e9e38f6ed4bb9bebe38d6fec64c53007 | 0obuwawao0 |1 |views/voi/dialog/desktop/edit_personal.html |     voi修改镜像分层编辑时 也禁用对应的 系统还原属性
a746435808f96397fa71b2a5c151aac8ae63cdf0 | wangchuan |4 |js/vdi/resource/storage/controllers.js; js/vdi/resource/storage/storage.css; views/vdi/dialog/resource/storage/config-strategy-dialog.html; views/vdi/resource/storage/disk.html |     去掉数据平衡-立即执行，配置自动修复策略，样式调整
f417edff38f1ebf7c23604fdc383e6f163e5d63c | wangchuan |1 |235fd3b58 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
2f16f400c6ed3a47caa8a21d7307ff80a6cbebc2 | wangchuan |5 |img/icon-schoolroom.png; img/icon-terminal.png; js/vdi/summary/controllers.js; js/vdi/summary/summary.css; views/vdi/summary.html |     概要修改
235fd3b58f03a3ca15e10ddd5a6d16b654b8c4d0 | wangchuan |1 |d0f645d38 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
5d6e2116c7b16046eaee4948abb75536bb870a8c | wangchuan |1 |js/vdi/terminal/controller.schoolroom.js |     VDI区域管理：新增编辑优化
fe44329f8f7cd9451c118f467ec4126f378076bf | wangchuan |4 |js/idv/terminal/controller.classes.js; views/vdi/dialog/terminal/terminal_schoolroom_add.html; views/vdi/dialog/terminal/terminal_schoolroom_edit.html; views/voi/dialog/terminal/pool_add_edit.html |     VDI，IDV区域管理：IP范围校验
45a31591456024fc74ce1fc56cdfe4288c90c7a8 | wangchuan |1 |js/vdi/vdi.js |     validateIpRange添加disabled支持
5ca20b6a9cdf055b8fd3c80864872a4cdfd2cb7d | wangchuan |1 |css/your_style.css |     validateIpRange样式
9017e907eb3ddcb7c4229597a2840c2fc6ca3db9 | wangchuan |1 |js/vdi/vdi.js |     辅助formatIp校验IP范围指令
d0f645d386e28bde95ae5fee084b732364cce193 | zhangyao |0 | |     build
594f3e678c18ecb4c6e24d59d0364acfb50d9963 | zhangyao |1 |js/vdi/desktop/common.js |     修复获取教室列表传参问题
f562c7d944c6d2c3024069480710c8b6a2a88299 | wangchuan |0 | |     build
ca648d1a0efd0b54d988ea566280a4cc367d18c2 | wangchuan |1 |e2388635d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
e8bf3ffaa3b9c936283ef36c1ea071e01d2a6320 | wangchuan |1 |personal_login/js/webLogin.js |     web登录：bug
e2388635d0f39e8ee5613aaf25ff5f7260977f41 | 0obuwawao0 |0 | |     voi 打包自测
02fcfd689f223c385a78c0751adaadecef045977 | 0obuwawao0 |1 |6ac30b729 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
6ac30b72928859ecfff440b3cf1cf06201c13d8a | 0obuwawao0 |8 |css/your_style.css; js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/desktop/controller.scene.js; js/voi/terminal/controller.terminal.js; views/voi/desktop/scene.html; views/voi/dialog/desktop/desktop_detail.html; views/voi/dialog/desktop/download_video.html |     voi解决bug
ab645023774a21c95d29595a304c0a8101866903 | wangchuan |1 |views/vdi/system/recycle/system_recycle.html |     回收站：无桌面时清空回收站按钮禁用
eb3d6ea52daa6a5b655311a3afe7446251035639 | wangchuan |1 |views/vdi/dialog/system/recycle/deleteCompletely.html |     回收站：彻底删除提示信息标红
93281bf24e10329e8e382c36f52352d01a6fd967 | zhangyao |1 |e6d5f0905 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
e6d5f0905200b3af3298b03f20ec30f2fcf24d1f | zhangyao |6 |js/vdi/resource/console/controllers.js; js/vdi/system/common.js; js/vdi/system/system-log.js; views/vdi/desktop/personal.html; views/vdi/system/admin-log.html; views/vdi/system/user-log.html |     修复禅道bugs
37afb61e6ca9f8c50c901c672c3a51fc37de0860 | wangchuan |1 |js/vdi/system/recycle/controller.system.recycle.js |     回收站：编辑保留天数bug
fddc2d143df73695e9096b1092512db7a7638820 | 0obuwawao0 |8 |js/voi/help/controller.deploy.js; js/voi/terminal/controller.terminal.js; views/idv/template/teach.html; views/idv/terminal/classes.html; views/voi/dialog/help/system_deploy_import_from_local.html; views/voi/help/deploy.html; views/voi/template/teach.html; views/voi/terminal/schoolroom.html |     修改voi快速部署本地导入机制
e69551d93fc851bdc3e3a74f1e3aa29404c9b476 | wangchuan |2 |views/idv/terminal/client.html; views/vdi/terminal/client.html |     VDI,IDV:终端列表显示每页条数
b20d172407ca066c48d0296002bd336e7e0bc932 | wangchuan |1 |js/vdi/terminal/controller.terminal.js |     需求变回去了。。恢复历史
0571a3a9872ce97de407eeb2c50827e985fa5f75 | wangchuan |1 |views/vdi/dialog/terminal/terminal_calculateconfigureparameter_edit.html |     需求变回去了。。恢复历史文件
749e66d8a94b1e59451a8a17acfd59679e595b53 | zagger |1 |css/your_style.css |     区域选中样式先恢复-后面想办法
1394ca89ec4418ce69a8c894543ce71a81710aba | wangchuan |1 |js/vdi/terminal/controller.schoolroom.js |     产品要求，VDI第一个顶层节点视为默认节点
9ac8ae28fc8c8ca97444b9dc7fb471b5884ddfee | zagger |1 |js/vdi/monitor/alarm.js |     15774 【告警信息】-筛选选择起止时间后界面一直显示“数据正在加载”
b20a24f2a5706226b4c72f4da36933b22784feab | wangchuan |3 |personal_login/forgetPwdPage.html; personal_login/webLogin.html; personal_login/webRegister.html |     修改错误信息样式
87c5b1189f5fde0c9d9b03f963c8554943d4be84 | wangchuan |1 |views/vdi/dialog/system/recycle/editLeftDays.html |     回收站:剩余保留天数只能输入正整数
9596a84395a23851875cc396eb537db585e4b417 | zhangyao |1 |75947dfc5 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
75947dfc587e3f89c5efe5bf960a02b5345a52e6 | zhangyao |7 |js/idv/desktop/controller.scene.js; js/vdi/desktop/common.js; js/vdi/desktop/scene.js; js/vdi/utils/ui.js; views/idv/desktop/scene.html; views/idv/dialog/desktop/add_scene.html; views/vdi/desktop/scene.html |     公共桌面相关逻辑优化
5c6dcd2be1f39fd955ea9ae11fe0529167d380c0 | zhangyao |1 |webpack.config.js |     允许自定义假数据
5587da68b5ca67b3e1ee542b024b5e5b5d9a8583 | zhangyao |3 |js/idv/desktop/controller.scene.js; views/idv/desktop/scene.html; views/idv/dialog/desktop/add_scene.html |     IDV添加区域树
f0cd98b2365e55b0f567c7d1d424b94db534979c | zhangyao |2 |js/vdi/desktop/scene.js; js/vdi/utils/ui.js |     公共桌面bug修改
e85eee956c92d6496017a1f5d88a7fcbfd27d55c | wangchuan |0 | |     build
b1340e0ded62986dd3db7c58c2c2f1eb3aee1dde | wangchuan |1 |a63145fd6 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
24d81ffb967c364a46ed4e42bd18995439274056 | wangchuan |3 |js/vdi/terminal/controller.schoolroom.js; views/vdi/dialog/terminal/terminal_schoolroom_add.html; views/vdi/dialog/terminal/terminal_schoolroom_edit.html |     vdi区域IP范围校验
a63145fd6ef5a09c9e6131f22bf9d37bc93a759e | 0obuwawao0 |1 |js/voi/desktop/controller.roam.js |     打包voi转测
8d710beaadb21a37bea926b8550d48dd0045ae27 | 0obuwawao0 |1 |js/voi/desktop/controller.roam.js |     打包voi
5b35c58739ea1ef830fe2fed6aab530b025ac7ee | 0obuwawao0 |1 |13c5e1182 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
13c5e1182f6c74e51df61e863ff6a500aa11d44b | 0obuwawao0 |4 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/template/controller.template.js; js/voi/voi.js |     打包voi
a5246eae5ad23f03d530eabf857a3bab7de8f2c7 | wangchuan |1 |3164e2f96 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
8ace827ac2debaa7c596c356d049abac7b485259 | wangchuan |1 |multi-select/isteven-multi-select.js |     多选下拉框
3164e2f96c84b5f31faa44a72d9ca697c21451fd | zagger |1 |2d182248b |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
2d182248b4d0f46c25d57bb8e89ba68af7bda981 | zagger |1 |js/vdi/monitor/alarm.js |     15698 【警告信息 】必现-导出警告日志不选择时间可以导出
7da32474a27028792cadf40e181a017325d17a79 | 0obuwawao0 |3 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/voi.js |     voi个人桌面部门树接口修改
eb12bb7f0aa87d06626b5a1d70aa8cc237d6cabf | wangchuan |1 |views/vdi/dialog/terminal/terminal_schoolroom_edit.html |     VDI区域管理：编辑区域不支持空格
eb15f59c38a97e3202fd7ce826238fa8d569f5c8 | 0obuwawao0 |0 | |     voi打包
7acae9e8cae85203a7e6c663df2c16f1919170e6 | zagger |0 | |     build for package
c5e133df02a6e5cca7590365d44a8b5d0e3902d8 | zagger |1 |img/computer-other.png |     补图2
fb3424be1f5d0d19ca9e8b256758c3f6b73e1ee7 | zagger |1 |f76647965 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
f7664796572d31412e41e9fc1e679f47df364241 | zagger |2 |img/nostate.png; img/pause.png |     补图
9b323713a0995ef3ea44aad006ece0dfa74d7e09 | zagger |7 |css/your_style.css; img/terminal_defend.png; img/terminal_deploy.png; img/terminal_menu.png; img/terminal_power_off.png; img/terminal_power_on_linux.png; img/terminal_power_on_windows.png |     gs
0b0ddca20086aa57468acdd6d318ab7cd0c178ea | 0obuwawao0 |4 |views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     修改区域样式
f238b6a35eea1e6b95d4980d457edec69a7e285b | zhangyao |1 |2bbc0376d |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2bbc0376dd51b6bb133f8ba6c8859b71588a6ae2 | zhangyao |1 |js/vdi/security/group.js |     fix: #15586
419373c3678db13d2803b30f0eb955fd2b09fb12 | zagger |0 | |     build
b1ce78940085c8fef22b603585376b97872e9957 | zagger |1 |a661e9246 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
a661e924693fe51de3fdd97301ddb20aaeb0ef1f | zagger |2 |css/your_style.css; views/vdi/user/domain.html |     用户-域用户-瓦片样式
32148401e9cd97c0cec41d96214b7eedff1579c7 | wangchuan |0 | |     build
ce1f89100e94835c2dc4e8038819ea9da36d5cf9 | wangchuan |1 |336101e84 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
336101e84ebace7699da289838060ed0deff8188 | 0obuwawao0 |1 |js/voi/voi.js |     voi打包自测
73430e9e28eaddcadd67b32f17eadec8dbc13e18 | 0obuwawao0 |1 |ac219601a |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ac219601adf901185233ca47153f2b6e92e14814 | 0obuwawao0 |8 |js/idv/terminal/controller.terminal.js; js/voi/desktop/controller.roam.js; js/voi/terminal/controller.terminal.js; js/voi/voi.js; views/idv/terminal/classes.html; views/idv/terminal/client.html; views/voi/desktop/scene.html; views/voi/terminal/schoolroom.html |     添加 VOI idv终端管理授权解除功能
9c73d91a84b964982d67e5d36e4f128572b9bbc6 | zagger |0 | |     build
02e662242fa8cabdeeec63d84f77463f0f40426a | zagger |1 |74d041429 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
74d04142942dbd0e679057057f91d812e2980d42 | zagger |2 |js/vdi/user/domain-user.js; views/vdi/user/domainList.html |     域账号
496f30d874d0619b9201530d1c0c0a81ad866eaa | zhangyao |0 | |     build
7766f37185f0f4a3234f1682a00888b4b39db084 | zhangyao |4 |js/vdi/config/http.js; views/idv/desktop/scene.html; views/vdi/desktop/poolList.html; views/vdi/desktop/teach.html |     去掉idv相关界面字段
f2e7917f2b8bdab34e21bc927a4fca34741f2b27 | wangchuan |1 |views/vdi/dialog/monitor/config.html |     【分布式存储】告警策略配置项
e129815ba3294713703751f63df23339908cd89f | zagger |2 |css/your_style.css; views/vdi/user/uaa.html |     背景颜色修改
907e96d88da542f2e7a554842b79c995d074408b | zagger |2 |views/vdi/terminal/client.html; views/vdi/terminal/schoolroom.html |     去掉终端两个界面多余的框
561270de5dc917b93d8c64fc45f7911b6d945d73 | zagger |1 |421a3b811 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
421a3b8110a85565ce97eb08234fbf37ee640295 | zagger |1 |js/vdi/monitor/controllers.js |     highchart loading背景样色修改
5a7af5dbd4da4de8bd735e69c5f073b008b0bb7d | 0obuwawao0 |0 | |     voi打包自测
d0652f0a780ba909d4eee732a5060aa1bffbfd38 | 0obuwawao0 |1 |d62c01d14 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d62c01d14b3a03f90fb83f8974bd9c482d00036e | 0obuwawao0 |4 |js/voi/terminal/controller.terminal.js; js/voi/voi.js; views/voi/dialog/desktop/add_personal.html; views/voi/dialog/terminal/alert_input_password.html |     终端解除限制
f7d9eeeabaec9ea8220b8260dc95e98c7764c1e9 | zhangyao |1 |541737c93 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
541737c93289e724273eb0b496d7137bccc91b30 | zhangyao |9 |js/vdi/config/http.js; js/vdi/security/group.js; js/vdi/system/system-log.js; js/vdi/utils/ui.js; views/vdi/dialog/security/new_desktop_strategy.html; views/vdi/dialog/security/new_rule.html; views/vdi/dialog/system/backup-log-config.html; views/vdi/dialog/system/set-keeptime.html; views/vdi/security/group.html |     修改禅道bugs
e4f3fda5be4c97e8d58e51776e943927c8f55c01 | zagger |1 |b028dd823 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
b028dd823f223f230f9f3dc145a03f1d1cea9d3b | zagger |0 | |     新增个人模板获取接口 逻辑5build
bfa59f8c1368738dafe6aa49621e08a4d6385531 | zagger |1 |js/vdi/desktop/personal.js |     新增个人模板获取接口 逻辑5build
9e2ee95333b432aaa73925d25abc5937848840a5 | wangchuan |1 |363bd86f2 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
363bd86f2bc10a635c3c7579a2ae85c6c2f6f7f6 | wangchuan |1 |900dafd28 |     合并代码
edca40280c3f77079862b1bcd56370121f37d877 | zagger |0 | |     新增个人模板获取接口 逻辑4build
900dafd2876c322ddbaad05d2ab6b837306f51f5 | zagger |1 |js/vdi/desktop/personal.js |     新增个人模板获取接口 逻辑4
46b395ff4388fea56876ed18b336cac88750f3eb | zagger |0 | |     新增个人模板获取接口 逻辑build3
a1a90c487b7d1124ee3bc811243156a93cc2ef27 | zagger |1 |js/vdi/desktop/personal.js |     新增个人模板获取接口 逻辑3
9ccdc675de31ad437247060bb6eec14a9d2c137b | zagger |0 | |     新增个人模板获取接口 逻辑build
d3d8903231d59be39ea1bd9388f7410b598f25c9 | zagger |1 |js/vdi/desktop/personal.js |     新增个人模板获取接口 逻辑
d0093080a875e54231b055ca7271a2054f632889 | zagger |0 | |     联调镜像分层代码
653a8eceb1e29263ddcd9abd19d0cf03b9cb632e | zagger |21 |css/your_style.css; img/computer-off.png; img/computer-on.png; img/intance_error.png; img/intance_running.png; img/intance_suspended.png; js/vdi/desktop/personal.js; js/vdi/user/common.js; views/vdi/desktop/personal.html; views/vdi/desktop/scene.html; views/vdi/dialog/desktop/personal_alter.html; views/vdi/dialog/desktop/personal_new.html; views/vdi/network/dhcp/dhcp.html; views/vdi/network/externalNetwork/externalNetwork.html; views/vdi/scheduler/disk.html; views/vdi/system/desktop.html; views/vdi/system/set-general.html; views/vdi/system/set-vdi.html; views/vdi/terminal/schoolroom.html; views/vdi/user/domain.html; views/vdi/user/uaa.html |     镜像分层代码 + 一大波样式修改
ac346fe0804b04bff6f6bd66d8d5a43dfe7bec1d | wangchuan |6 |img/computer-off.png; img/computer-on.png; img/terminal_defend.png; js/vdi/summary/controllers.js; js/vdi/summary/summary.css; views/vdi/summary.html |     概要修改
5d980cf80524db76865e454d4e3e7c09a437f32c | wangchuan |1 |js/vdi/security/client/controller.security.client.js |     产品要求改个文字
4baaa6b2ed2cc3566f9d104290cab7736e70e2f1 | 0obuwawao0 |3 |js/voi/terminal/controller.terminal.js; views/voi/dialog/terminal/alert_input_password.html; views/voi/terminal/client.html |     正在做终端解除限制功能
f97bebda71ead8601271db31d974b12c49840b75 | 0obuwawao0 |1 |a3f3af758 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a3f3af7586c247a51739732e9aaddb9374d78843 | 0obuwawao0 |1 |views/voi/desktop/roam.html |     漫游桌面列表去掉CPU 资源池列
47a9bf1a310503a5df5382ebf989cbdefc160f54 | wangchuan |1 |views/vdi/dialog/security/client/apply_security_client.html |     产品要求给区域加个终端数量展示
f6c742ff9fa5e8ddb839b78a92e770f92cad6368 | wangchuan |1 |personal_login/index.html |     上一次提交错误
e932831b5487e9e66abb87fa53ec8238fcf9e7cd | wangchuan |1 |2b96cc901 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
7f5e37bc327602f35d52730a4270ca04b812e5ee | wangchuan |1 |personal_login/index.html |     历史bug
7b124bff9fdc258ece099e743ecb8da470204bd5 | wangchuan |1 |views/vdi/dialog/resource/storage/add_disk_group.html |     产品要求加个提示
94c355e8e550a2b81ab4f70df4f06d6599d32b38 | wangchuan |1 |js/vdi/security/client/controller.security.client.js |     产品要求添加时间限制
2b96cc90182e08680a01e92f847933ae03782a8c | 0obuwawao0 |2 |js/vdoi/system.js; views/vdi/system/set-general.html |     放开通用设置中的随机码
32976ac2dc84dc8ac0a7848f219378ad23e46f50 | zagger |2 |js/vdi/monitor/common.js; views/vdi/system/set-general.html |     1.bug#15544 【通用设置-】必现-配置邮箱服器复杂的测试邮件地址不能输入    2.15542 【通用设置-】必现-配置邮箱服务可以输入不合法的端口号
7e8fa92f489dc874ca7c728d5294aa365a02c628 | zhangyao |2 |js/vdi/desktop/common.js; js/vdi/utils/ui.js |     教室树形选择器优化
48fdacd347c41f971f3bf3f395fb46dfe79dc375 | zhangyao |1 |d7840727c |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d7840727cf1c79576ae5261c5f8aedb0c885e3be | zhangyao |2 |js/vdi/security/desktop.js; views/vdi/dialog/security/new_desktop_strategy.html |     核对编辑策略需求
2c9ffec58361f36cde825c26d66e3b40a8c42398 | 0obuwawao0 |2 |js/voi/help/controller.deploy.js; views/voi/dialog/help/system_deploy_import_from_local.html |     块速部署本地上传和vdi保持一致
0354dff9cab5b221e560f419eb18bdcfa643c2c5 | zhangyao |3 |js/vdi/desktop/common.js; js/vdi/desktop/scene.js; js/vdi/utils/ui.js |     教室选择器细节优化
e8046125624cca86e48471e13d05905c3f5cb90d | zhangyao |3 |js/vdi/desktop/common.js; js/vdi/desktop/scene.js; js/vdi/utils/ui.js |     进一步完善 picker 逻辑
985220b382f0f0f1483d3a90ea2d30b575c12c49 | zhangyao |7 |.gitignore; css/your_style.css; js/vdi/desktop/common.js; js/vdi/desktop/scene.js; js/vdi/utils/ui.js; js/vdi/utils/user.js; views/vdi/dialog/desktop/scene_new2.html |     完善picker指令
9ab2d65241e614a4d361b9b3aa45a43532e5ef64 | zhangyao |1 |4c9b0f1f6 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
4c9b0f1f6aa1f277773436eb2e858db3cec8bcd0 | zhangyao |1 |js/vdi/utils/ui.js |     添加 ui-picker ui-tree-picker 指令
2fe989fe5ea7e61216c3ac9e8802964a879c2c60 | wangchuan |1 |b49adf5e2 |     概要修改
322460b71749345f08693ead01040e0c1932332c | wangchuan |4 |js/vdi/summary/controllers.js; js/vdi/summary/summary.css; js/vdi/vdi.js; views/vdi/summary.html |     概要
b49adf5e276d9090b0a2d36336e046a61ce6d18f | zhangyao |1 |ff4d69a28 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ff4d69a28dcb768801f10ae0a3af533b396acf39 | zhangyao |4 |js/vdi/help/quick-deploy.js; js/vdi/system/common.js; views/vdi/dialog/system/system_deploy_import_from_local.html; views/vdi/help/deploy.html |     fix #15471
fb8c9cabd96f6ea688fe05568e75991e0092445e | 0obuwawao0 |1 |a2eb2ef79 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a2eb2ef795d83ed6601751ff18319a0f6cb74153 | 0obuwawao0 |4 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; views/voi/dialog/desktop/add_scene.html; views/voi/dialog/desktop/desktop_detail.html |     修改VOI个人桌面详细，漫游桌面详细
a613ed7006dd7318365b2e66e44b71867bc4b586 | zhangyao |0 | |     build
7a23a0f465ff5bae7ba2e920641206efb9dfc983 | wangchuan |0 | |     客户端包
c190a3938841c82b74df2b2fcfce2202b18174d6 | wangchuan |1 |6212328c3 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
6212328c3af77343c5cc6a8bb01108f085f5137d | zhangyao |1 |bf8bf9080 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
bf8bf9080f1d59cc05f9cbe8dfae8bb3250e77d2 | zhangyao |1 |js/vdi/system/system-log.js |     修复日志设置保留时间问题
f8c44d7da97853d0361cac73a4cff99da86bbf81 | wangchuan |1 |js/vdi/summary/controllers.js |     概要修改
1abbf47276ecb901350378b0f606d90e70297c3a | wangchuan |2 |js/vdi/summary/controllers.js; views/vdi/summary.html |     概要修改
61c4e066cbd9c30c09b7a7718074e506f3a66b9d | wangchuan |1 |js/vdi/resource/storage/controllers.js |     存储管理：配置公共存储bug
d21c71009fd171c37cc6c8e369de66ec68e93674 | wangchuan |4 |js/vdi/terminal/controller.terminal.css; js/vdi/terminal/controller.terminal.js; js/vdi/vdi.js; views/vdi/dialog/terminal/terminal_configureclassroom_edit.html |     终端管理：移动至优化
57e5abdaccf844d1955777d3d042746326b2150e | zagger |1 |js/vdi/user/uaa.js |     build
4a676fe810fd13899f4a1e2d105d85fe50d20a86 | zagger |1 |7added9ea |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
7added9eac69e9c8a9055f60f40a83ff01527685 | zagger |1 |js/vdi/monitor/alarm.js |     告警信息成功提示信息添加
1eab79acafb1156b61b362c3b3823dc1d3515464 | zhangyao |1 |c3c5df4b6 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
c3c5df4b6e2909e038368c60b955150f24dff706 | zhangyao |2 |js/vdi/security/shared.js; views/vdi/dialog/security/manage_desktops_for_strategy.html |     fix: #15464
30cd998bb9b45408cf33cef689af02b5a763a287 | zagger |0 | |     build for backend fixed bug
38d0be98526c11e4820db8311d270ebdff8bbe1f | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     uaa-管理帐号和普通帐号-一键同步配合后端修改
8fea297e997fcd1413f678a1ecf572aad6296ff3 | zagger |1 |js/vdi/monitor/controllers.js |     监控兼容一下报错
6cea52c2fbe5d4767db19d1a91f1493ef583751f | zagger |1 |66762828c |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
5833a5461537565eee48d7f8cd09da2927c2061f | 0obuwawao0 |0 | |     voi联调
6f1da9a2e2ddbde39a4e0b600585bfe6a30186d1 | 0obuwawao0 |0 | |     登录假数据修改
16540cd3560275cb5d12c6d73206e659caf5230c | 0obuwawao0 |5 |img/yhkylin.png; js/voi/dashboard/controller.dashboard.js; js/voi/desktop/controller.roam.js; js/voi/desktop/controller.scene.js; views/vdi/summary.html |     修改dash
188f73f14d2df8a7b77a14bc4aeda2d5e30fd8ec | 0obuwawao0 |1 |f1d4d7d2d |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
f1d4d7d2db80bf0d9c468e41dadbc3a115f00da7 | 0obuwawao0 |5 |js/voi/help/controller.deploy.js; js/voi/voi.js; views/voi/dialog/help/system_deploy_import_by_server.html; views/voi/dialog/help/system_deploy_import_from_local.html; views/voi/help/deploy.html |     修改快速部署
66762828c906a84b02aa326fa2f6de80008288e9 | zagger |2 |css/your_style.css; js/vdi/scheduler/disk.controller.js |     1.修改select多选框样式，高度掉下来了2. 网盘界面，开始loading问题
254b882a81312db0f82840169be7af5c46b7c4e4 | zhangyao |1 |6d4211247 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
6d421124771bc409045eec231f289e245c16e2e6 | zhangyao |0 | |     build
a6c29e0081fab62aeba25b6adc8f96f1fde1a50f | wangchuan |0 | |     客户端包
83a34637aa687574f4665032c4624c0f15b56960 | wangchuan |1 |3e6dc6aec |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
3e6dc6aec828ef80eb79b3c3960f882465b2222e | zagger |2 |js/vdi/auth/controllers.js; js/vdi/scheduler/disk.controller.js |     1. 登录失败-清空密码框    2. 网盘域帐号-查询条件
258cfa5fda14e70ee320d07ed59d9f06d687a46f | zhangyao |2 |js/vdi/security/group.js; views/vdi/security/group.html |     fix: #15232
e8c85681aa266bb0a5a445b5073dfb82f95c8974 | zhangyao |1 |da76995ee |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
da76995ee1f273cc4ba75b9a11aceea816c5d822 | zhangyao |1 |js/vdi/utils/ui.js |     fix: #15450, colorpicker 问题
f249f819b959112c3cd011aaaa92739c56dfe992 | wangchuan |3 |personal_login/js/common.js; personal_login/js/components/pwd-complexity-tooltip.js; personal_login/js/rules.js |     密码强度
8c55c2a2a2770279667dae599b26d4a2a58d2be0 | 0obuwawao0 |5 |js/voi/voi.js; views/voi/desktop/roam.html; views/voi/desktop/scene.html; views/voi/terminal/client.html; views/voi/terminal/schoolroom.html |     树高修改
5d1f5c6c4cfc4f5d0934bd11ae714d05cad353c6 | 0obuwawao0 |6 |js/idv/terminal/controller.terminal.js; js/voi/terminal/controller.terminal.js; js/voi/voi.js; views/voi/desktop/personal.html; views/voi/dialog/terminal/terminal_move_groups.html; views/voi/terminal/client.html |     处理VOI,IDV移动终端窗口逻辑
db0b95d64e0ea87b886fa8d2b8dc8bf1a8a359fe | wangchuan |0 | |     客户端包
6726161e9e374e8d537661d4118b1f6deee5869a | zagger |1 |views/vdi/user/uaa.html |     15376 【用户帐号】-必现-普通帐号登录了终端，帐号信息上次登录IP未记录
584dd9589ea716d488f03066791d1b828c00adca | zagger |2 |js/vdi/user/admin-user.js; views/vdi/user/admin.html |     15389 【管理帐号】-必现-admin帐号重置密码与需求不符
a9ddc9391e11ee4a13087119b14709bbc93f89de | zagger |1 |forget-pwd.html |     15401 【登录-忘记密码】-必现-忘记密码不输入密码可以修改成功
31d373a8c0d6a40dc4fb44c51a8df886e82f6320 | zagger |2 |js/vdi/user/common.js; views/vdi/common/select-multiple-dom.html |     恢复select多选框的结果项删除功能
ddd0189279ad8d6c25dfaac7da67b0b7681b6ded | 0obuwawao0 |1 |bb742859c |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
bb742859c61cc8aabcb187f0a23cc36ad485c545 | 0obuwawao0 |6 |css/your_style.css; img/uos.png; img/yhkylin.png; js/vdi/os-types.js; js/voi/desktop/controller.scene.js; js/voi/voi.js |     修改模板图标标识
af13108567a3078d9f775db07b69ba8bc3980995 | wangchuan |1 |9211972d4 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
9211972d4c6cdd26aaba8e41bc97c89719faed7b | zagger |1 |01259b87d |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
01259b87d789d5cd65cd0651c1d6f8116c2381cb | zagger |4 |css/your_style.css; js/vdi/user/admin-user.js; js/vdi/user/common.js; views/vdi/common/select-multiple-dom.html |     多选框样式解决
eac49455973d27937f4f2f48c15a4ec569a8c7a7 | wangchuan |0 | |     客户端包
cbcb8ddd42ae72c332fc70e7f22712e55b623cc4 | 0obuwawao0 |6 |css/your_style.css; js/voi/desktop/controller.scene.js; views/idv/template/teach.html; views/voi/desktop/scene.html; views/voi/template/personal.html; views/voi/template/teach.html |     修改VOI,IDV模板界面样式，隐藏工具栏按钮图标，修改voi公共区域界面
929f600138569a331d97c7bc5e98c3a757820887 | zagger |3 |js/vdi/user/common.js; views/vdi/common/select-multiple-dom.html; views/vdi/dialog/user/user_admin_scope.html |     管理帐号-范围代码-完整保存-完整读取版
3e72a4267d12d4af5c2ba79ceb3993087ad83968 | wangchuan |6 |css/smartadmin-production.min.css; js/vdi/summary/controllers.js; js/vdi/summary/summary.css; js/vdoi/main.js; views/vdi/app-main.html; views/vdi/summary.html |     概要界面
2e36d0e329a4f9bac33e50bc4606cf1d89a55154 | zhangyao |1 |js/vdi/utils/ui.js |     修复树形删除逻辑
1871bb8b865e53b0e95836262bc48711d3fe4ca9 | zagger |4 |css/your_style.css; js/vdi/user/admin-user.js; js/vdi/user/common.js; views/vdi/common/select-multiple-dom.html |     管理帐号-范围代码
b9c0276ccbb1801534d5e9f089f20d19b92a03c2 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     bug
cccdfbdb2673d0f4027de607c23db5bb9a109f4d | 0obuwawao0 |5 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.scene.js; js/voi/terminal/controller.terminal.js; views/vdi/system/set-general.html; views/voi/desktop/scene.html |     正在修改场景
01f5505526c78631788fcbab3aa1c13f34147237 | zhangyao |6 |img/watermark-bg.png; js/vdi/desktop/scene.js; js/vdi/security/desktop.js; js/vdi/security/style.css; views/vdi/desktop/scene.html; views/vdi/dialog/security/watermark_preview.html |     解决场景过滤问题
b1c92db2e7ae04dc172a8215c3345621fcbffd3d | zhangyao |0 | |     build
c07a11ca3ee30acee22820af4595e0c722d64f2e | zhangyao |1 |a60a33b1e |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a60a33b1e55077e28235024be9b09a0fd7100d65 | zhangyao |5 |css/your_style.css; js/vdi/config/http.js; js/vdi/utils/ui.js; views/vdi/common/confirm.html; views/vdi/system/set-general.html |     修复影响打包问题
bfbd80e2da5706c50fec404388be4e2e5e96756a | wangchuan |0 | |     客户端包
a974f270dda96f39520d35d3ec4fcec9a48f223a | zhangyao |0 | |     build
13340f8f441873b24f5212d252b376c050fddd62 | zhangyao |1 |73c8b3f98 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
73c8b3f98b1eed637708bd1d84ca86642232f88a | zhangyao |4 |js/vdi/desktop/personal.js; js/vdi/resource/storage/controllers.js; js/vdi/security/shared.js; views/vdi/dialog/security/manage_desktops_for_strategy.html |     修复几个bug
55e1f675dfcd66689d702350c6e8c5aec077fa00 | 0obuwawao0 |3 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; views/voi/desktop/roam.html |     漫游桌面添加详细窗口
8a26d601e8b91277816c7c55d93ffc9732163d76 | 0obuwawao0 |1 |646b6f578 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
646b6f578bf853fb1c121348b01aa8e92df9db56 | 0obuwawao0 |7 |js/idv/system/controller.system.js; js/vdoi/system.js; js/voi/system/controller.system.js; js/voi/voi.js; views/idv/system/set-idv.html; views/vdi/system/set-general.html; views/voi/system/set-voi.html |     修改设置，分离出局部控制器
94494680a11bea3107b5e94d68bb17a7dbaf898e | zagger |3 |css/your_style.css; views/vdi/help/about.html; views/vdi/help/activeAuth.html |     激活授权界面样式修改
57df7d0753fa968026f92ec2156267d910e6e20d | zagger |0 | |     forget.js参数改错地方了
ccd4bdb1e06935a5bf7647fc4383c6ea28a09efb | zagger |1 |js/vdi/forget.js |     forget.js参数改错地方了
31b05d2aad207d06fe3607c367e45fc55bd5f39d | zagger |0 | |     打包给后端测试
daab63ada75e45330212e8db3e4cd7fdd259faba | zagger |2 |css/your_style.css; views/vdi/help/about.html |     about 界面样式修改
da14c483d456d8c18e39f398578489416aa4aa3b | zagger |1 |9c83bcae8 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
9c83bcae874660e95a76afb8e42110e8ad75cd60 | zagger |1 |js/vdi/forget.js |     忘记密码界面-获取验证码接口配合后端加个参数type
535853254f2c591632669711d80a87fa886866d1 | wangchuan |0 | |     客户端包
3630f6408e3c8de55bfae713691aff5793cf1efb | wangchuan |1 |9d7d9cdaf |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
3f3e79d8ca5791b7010a263016bdba4965c2f0ff | wangchuan |1 |views/vdi/terminal/client-tab.html |     终端管理文本
9d7d9cdafa7fc113686f67042f2bd6db523c4f84 | wangchuan |1 |views/vdi/system/set-general.html |     仲裁IP
6f5abca0a2ac652f276c3bb9cf1a33c52153cc70 | wangchuan |1 |38c07c87d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
141bd092fdd2a69569c21fd8c2dc479e733853f6 | wangchuan |2 |js/vdi/system/system-settings.js; views/vdi/system/set-general.html |     仲裁IP设置
38c07c87d56b631c2c9f581316f43946b7101448 | zagger |1 |678dd6cdc |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
678dd6cdcdbc581b06bfd49dae1ff1d0affa01da | zagger |6 |css/your_style.css; views/vdi/resource/console/console.html; views/vdi/resource/pool/host.html; views/vdi/template/hardware.html; views/vdi/template/personal.html; views/vdi/template/teach.html |     一大波样式修改-待验证
561af8b61e7676ca3a710b85eef8984686f7d49e | zhangyao |0 | |     build
0c234c786e501a9ad3b9a4875130d8fd7642f3a5 | zagger |1 |ssh_terminal/terminal.js |     调试3
cc6c5b475e4bd9834f5c82bcb28f0231e2cbac4e | zagger |1 |ssh_terminal/terminal.js |     调试2
4b2a1cd4ced3f6b6c334c679529282be8efd5a30 | zagger |0 | |     yuancheng 调试
47c614a4fc8784f8fc8886587f7944389b4ac7e0 | zagger |1 |ssh_terminal/terminal.js |     ss2
15f492607d2b9efb8656c4cbbcf821bb27a08418 | zagger |1 |ssh_terminal/terminal.js |     ssh
da64860e1ae11eff7ec83792d98d81eca71adaab | zagger |1 |041284f7d |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
041284f7df983a3173ce33290704b2d794a00e20 | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     没有邮箱重置密码给提示
db934ec8760df95ed21ed41091a36094fc8f2d51 | zhangyao |1 |ebfc489f0 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ebfc489f099b03ef082a29681421cd8af87c0a96 | zhangyao |1 |views/vdi/dialog/license/addlicense.html |     修复下载链接
a235f5e9df228d01bdb5127e94e701bd44ec89c9 | zagger |1 |1d19423b9 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
1d19423b9511fd7326b818e16fc54fcff549eaac | zagger |1 |js/vdi/monitor/controllers.js |     代码提交timer
c7ed73bc0cd0fae65a61f35debd87f11a749a41d | 0obuwawao0 |5 |js/idv/terminal/controller.terminal.js; js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/voi.js; views/voi/desktop/roam.html |     修改漫游桌面布局
b07d1d80fcbc6d40b8f0b51b2088421fd258305f | zhangyao |2 |js/vdi/desktop/scene.js; views/vdi/desktop/scene.html |     添加区域树
7a26abfae447c1e1f73b850ebef0d4f7c6d98127 | zhangyao |0 | |     build
f61579655dc605c6ba23f30a9d88d3f00c7e08a5 | wangchuan |1 |15f27130e |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
15f27130e4bd23eb8ecdf56f3ca59b3d89d4f746 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     echarts
48ec3a2c9f130cacf7173a73d29adbea6b2b3a9d | zhangyao |1 |d1670f41f |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d1670f41f8a933924564a4443d5b9dbbd28e9736 | zhangyao |6 |js/vdi/config/http.js; js/vdi/resource/api.js; js/vdi/security/desktop.js; js/vdi/security/shared.js; views/vdi/desktop/personal.html; views/vdi/dialog/security/manage_desktops_for_strategy.html |     修复禅道BUGs
04efe2fcd3fc5c7bf67787650e2d5fe14268852d | wangchuan |1 |js/vdi/resource/storage/controllers.js |     echarts
a8684bb0deac1f0095ad65392be754a25284dc4d | zagger |1 |js/vdoi/main.js |     兼容报错代码
747774b44fa38af75cfce6ba38d9770cb8b11cb4 | zagger |1 |css/your_style.css |     工具条样式修改
868dec439a7b12fd46ce3616747298ce5a6be847 | zagger |1 |views/vdi/system/set-general.html |     认证服务器+修改时不能解除认证服务器+保存时验证表单
d8c863aa67179921082e8da7956237451fe0f780 | zhangyao |2 |includes/userMenu.html; js/vdi/vdi.js |     fix 15085
8c84f09cc35a14dba21f37cc3e71ee7660c09a96 | wangchuan |1 |js/vdi/system/recycle/controller.system.recycle.js |     bug
dc3fc43e742d948ea35ea8ecbec0cbe0f815ffa8 | zagger |2 |js/vdi/system/system-settings.js; views/vdi/system/set-general.html |     邮箱服务器bug
d78cfc829cbc0143b67e4ffb96d1c8a27a6cce19 | zagger |1 |js/vdi/menus.js |     bug#15275 【管理台】-必现-主界面桌面、模板菜单顺序与需求不一致
ca62f735fffaaac7fc684e933ce4c24714b5997b | zagger |1 |js/vdi/monitor/common.js |     修改textarea-email指令 bug， 换行之后的值没有trim掉空格
14f22515562eef01521d7644020632607b4f8763 | zagger |2 |js/vdi/system/system-settings.js; views/vdi/system/set-general.html |     认证服务器bug#15290，认证成功提示+取消之后，重置填完之后的值
83d8b03b206c304a07d9561df80d5ce4e9097caf | zagger |1 |e23bbcaa5 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
e23bbcaa5d228e9699b945eec01cd644a49b5f2f | zagger |1 |css/your_style.css |     header背景图 background-size:cover;展示
01bb5e9f937db4bdaf590e41c6f3ec219aa3db24 | zhangyao |0 | |     build
31f72e3cea3313911821d4e6ea0dfbe196f2a752 | zhangyao |3 |js/vdi/bootstrap.js; js/vdi/config/http.js; js/vdi/split.js |     http请求拦截器修改
c567febc1de927d2e1d3a83bd973cbab866b2abe | wangchuan |0 | |     build
e625c379fae0ce48ec72b05abc6a86931bae3fae | wangchuan |1 |fa4ec8f11 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
be6345c4017c90b6f3a464333fe42697e203d177 | wangchuan |1 |personal_login/js/components/user-form.js |     获取token加type
719077f6455a809ac457713f8ca484e222e5b75b | wangchuan |4 |personal_login/index.html; personal_login/js/components/login-timeout-tip-modal.js; personal_login/js/components/pwd-expired-tip-modal.js; personal_login/js/webLogin.js |     登录时效性提示
fa4ec8f115c33c03ee351ca5642e3eedee2e89a3 | zhangyao |0 | |     build
6684209be077e0de43f758ec2c5be6a446dff0f1 | wangchuan |1 |24c4ee956 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
24c4ee9564f63b587ee84e32f6422fa9eb0efdbe | wangchuan |0 | |     客户端包
27a6a1e05795e5206fe2fd79fe8e219e12fdc3cd | zagger |1 |8858b982f |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
8858b982fa6f05574f6fb8e7afbdec8c327a59ff | zagger |1 |js/vdi/auth/controllers.js |     邮箱获取验证码时已经知道了验证码的邮箱的，不用前端提示
9189ed6b638860002fe497432fa413dba57afbc9 | zagger |2 |views/vdi/user/admin.html; views/vdi/user/uaa.html |     前端放开对帐号的重置密码的限制
6f14cbf8937ba46a6f081acb9c87acf894b2684a | wangchuan |1 |cf41b5a5c |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
37f06a32bf688b8c5115a373d9ce63dc87830cdd | wangchuan |5 |js/vdi/resource/storage/controllers.js; personal_login/forgetPwdPage.html; personal_login/js/components/combined-login-modal.js; personal_login/js/components/user-form.js; personal_login/js/webLogin.js |     代码优化
cf41b5a5cb20bf5bd9981eaed3fe51a243f9aa2d | zhangyao |2 |js/vdi/utils/ui.js; views/vdi/dialog/security/new_desktop_strategy.html |     修复禅道bugs
3034c2bf82ad7cf8daa17e8d2ed3b68029b6bbff | zhangyao |1 |d0e963f8d |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
d0e963f8d0b08cb8ac4bc8199403bab934ac6fd8 | zhangyao |4 |js/vdi/config/http.js; js/vdi/desktop/personal.js; js/vdi/utils/ui.js; views/vdi/dialog/desktop/personal_download_video.html |     完善通用校验指令
48a0d3161bc887485fb7839d69838d97219fe33a | wangchuan |0 | |     客户端包
acf80373149625ed66525527773ce2a8ebf680b7 | wangchuan |0 | |     build
4051dae9d8dd900f8e8ad0675e454254bedcbc50 | wangchuan |1 |a24d1a135 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
4b1a56432a2d643ca6dcd1d1f636422626f14291 | wangchuan |1 |personal_login/js/components/bind-mail-modal.js |     代码优化
a24d1a135d51d437d3507a6cf919a2e21477422b | zhangyao |1 |f7dc49dad |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
f7dc49dade95a0f7fce12c4cd5793409a625b29c | zhangyao |3 |js/vdi/desktop/personal.js; js/vdi/security/group.js; views/vdi/dialog/desktop/personal_delete.html |     修复禅道bug
8ddc3fa5e9eae89e5e64d0002dd6df89d5a46c82 | wangchuan |10 |personal_login/css/webLogin.css; personal_login/js/components/bind-mail-modal.js; personal_login/js/components/modify-default-pwd-modal.js; personal_login/js/components/user-form.js; personal_login/js/rules.js; personal_login/js/validator.js; personal_login/js/webLogin.js; personal_login/views/user-form.html; personal_login/webLogin.html; views/vdi/dialog/security/client/apply_security_client.html |     代码优化
50fd5b0d7c72d559b5991df3708c1b0fc0486d7b | zagger |5 |forget-pwd.html; js/vdi/auth/controllers.js; views/vdi/common/force-modify-pwd.html; views/vdi/common/login-step2.html; views/vdi/login.html |     验证码和动态密令
61eb93440762ccd01942766bfd9dcefbe09826b3 | zagger |0 | |     测试强制绑定邮箱-假数据
32722fe60d455316ddcec7610c77f2e7809eeb67 | zagger |4 |js/vdi/auth/controllers.js; js/vdi/forget.js; js/vdi/utils/user.js; views/vdi/common/login-step2.html |     获取验证码-前端提示黄色框，提示邮箱地址
f6c17371430c4d2f74d5462e3f60e625c0b38074 | wangchuan |6 |css/your_style.css; views/vdi/dialog/security/client/add_edit_security_client.html; views/vdi/dialog/security/system/add_edit_security_system.html; views/vdi/security/client/security_client.html; views/vdi/security/system/security_system.html; views/voi/dialog/terminal/pool_add_edit.html |     bug修改
1da34a9b8fe01fda8163a16bf3668ed5640d8c36 | wangchuan |2 |js/vdi/resource/storage/controllers.js; views/vdi/resource/storage/disk.html |     bug修改
e82850905cc75bc41c532850d36fa5a8be39eda0 | zhangyao |5 |js/vdi/security/desktop.js; js/vdi/system/common.js; js/vdi/system/system-log.js; views/vdi/dialog/security/manage_desktops_for_strategy.html; views/vdi/dialog/system/export-log.html |     修改bug
9b8f8aa76152a0bdc6f5f009d6c22a80fc6d0f20 | zagger |1 |2d31ddce9 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
2d31ddce9a089e61468d6179488e529fe25d3873 | zagger |1 |views/vdi/dialog/user/admin_uaa_import.html |     优化选择角色的问题
94e327b354457fd8b59bc3d58bc9d8ee91b29909 | 0obuwawao0 |1 |5cb78bc17 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
5cb78bc170b67ec56ce8819f22412ee60757fd01 | 0obuwawao0 |14 |js/voi/desktop/controller.personal.js; js/voi/desktop/controller.roam.js; js/voi/terminal/controller.schoolroom.js; js/voi/terminal/controller.terminal.js; js/voi/voi.js; package-lock.json; views/voi/desktop/personal.html; views/voi/desktop/roam.html; views/voi/desktop/teach-list.html; views/voi/dialog/desktop/add_personal.html; views/voi/dialog/desktop/desktop_detail.html; views/voi/dialog/desktop/download_video.html; views/voi/dialog/desktop/edit_personal.html; views/voi/terminal/client.html |     漫游桌面添加录像管理，VOI终端修改布局，VOI公共桌面修改布局,VOI区域管理修改布
06c0c601cd048b8d212452445ca6c66b1a4646a6 | zhangyao |1 |591328cb8 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
8ded53434d2e707a7457ced95d608aa81c2fbd9e | zagger |2 |views/vdi/dialog/user/common_uaa_import.html; views/vdi/user/uaa.html |     去掉多余的代码所有分组+ 由于需求原因，uaa少显示了邮箱这一列
303c81dac60c1cc8319a423e095837f1a7215a05 | zagger |1 |views/vdi/dialog/user/admin_uaa_import.html |     添加默认请选择角色占位选择项
dd1a5bedb934373bcc53cf6993b37437449d9c66 | zagger |5 |js/vdi/user/admin-user.js; views/vdi/common/account-password-modify.html; views/vdi/common/force-modify-pwd.html; views/vdi/dialog/user/user_admin_scope.html; views/vdi/user/admin.html |     bug#15125#15124
591328cb8a57e21aa4aa556764d7df5f8a3cb70e | zhangyao |1 |js/vdi/security/desktop.js |     透明值改为不透明
6a3f0bd1613e34165133b859b9b796f326fc3de7 | zagger |1 |views/vdi/common/force-modify-pwd.html |     绑定邮箱提示
a803125b2f0d0e90cd998869ffe74b9f97e2daa1 | zagger |1 |7f7f5fcc6 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
7f7f5fcc6748f36cb2afab3c5edb7cd26ee6a9e1 | zagger |4 |js/vdi/help/controllers.js; js/vdi/help/index.js; views/vdi/help/about.html; views/vdi/help/activeAuth.html |     about代码整理
da25ed99c3c9265b93d31f4eaa7ee62bf4b66c5b | zagger |6 |css/font-jj.css; css/your_style.css; js/vdi/help/about-authority.css; js/vdoi/main.js; views/vdi/app-header.html; views/vdi/app-menu.html |     样式修改1
d973e894eeb089af3750f65f40685d69eb59c045 | zhangyao |1 |views/vdi/security/desktop.html |     fix #15083
053756c8c71171e2915319cd678156c042c31281 | zhangyao |1 |05a7fb2b7 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
05a7fb2b7fa4752147233dcd5955d6fa1c401b91 | zhangyao |2 |js/vdi/desktop/personal.js; js/vdi/utils/ui.js |     优化个人桌面左侧部门树
d11eb450bb88b97933e2a243f3758343c3e1b232 | wangchuan |1 |5fe5710ae |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
5fe5710aed84559e978e4d54cda54720eea4244e | wangchuan |4 |js/vdi/security/client/controller.security.client.js; views/vdi/dialog/security/client/add_edit_security_client.html; views/vdi/dialog/security/client/manage_security_client.html; views/vdi/dialog/terminal/terminal_schoolroom_add.html |     代码优化，bug
c5b579519bd152ec6c113e10d3a6f3fc953358f8 | zagger |1 |1ae5fd922 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
1ae5fd922adb0518e08b969e3fe817c1ebd8c4d2 | zagger |6 |img/new_login_icon/about_bg.png; js/vdi/scheduler/disk.controller.js; js/vdi/user/admin-user.js; js/vdi/user/uaa.js; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     bugs
4f2f80ef1453bceaf7d7cdc4801f624eecda4e33 | wangchuan |4 |js/vdi/security/client/controller.security.client.js; js/vdi/security/system/controller.security.system.js; js/vdi/system/recycle/controller.system.recycle.js; views/vdi/security/client/security_client.html |     代码优化
8c1ef8a89d3e2de49af6a7fc12bd8b7f5c89d4a9 | wangchuan |1 |fd7d39952 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
d3692f1957bafbf5ed422eafd7c955360b2b58f6 | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/security/client/security_client.html |     终端安全：后端过滤
fd7d3995271d6593ee444d2e4632049511facbfd | zagger |1 |js/vdi/bootstrap.js |     添加todo
99beafa03660bbb027642c8ab6ef083cfbdbf42d | zagger |1 |js/vdi/bootstrap.js |     端口统一-继承port+host+protocol，只考虑路径问题
72b1df90c6dbe3db453b9ef3c8cc3b3fd1b004a0 | wangchuan |1 |personal_login/views/user-form.html |     bug
752aed82b4aafeb6bd4cd95483901036dd181c67 | zhangyao |1 |dc076a0d9 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
dc076a0d9c43b60fe10f255e10e9df3a88dad3ea | zhangyao |13 |css/your_style.css; js/vdi/desktop/personal.js; js/vdi/security/group.js; js/vdi/system/system-log.js; views/vdi/desktop/personal.html; views/vdi/dialog/security/apply_strategy2desktop.html; views/vdi/dialog/security/new_rule.html; views/vdi/dialog/system/export-log.html; views/vdi/security/group.html; views/vdi/system/admin-log.html; views/vdi/system/backup-log.html; views/vdi/system/logs-tabpanel.html; views/vdi/system/user-log.html |     修复测试发现的问题
f88213e9815735d3f100a6baf5c0d8a32dd5c09e | zagger |0 | |     build
208d844a791662978adae661adee8f0de268fd34 | zagger |1 |5d96ffa95 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
5d96ffa95839a20b0629e92f0085387817a2fe98 | zagger |1 |views/vdi/app-header.html |     隐藏主题
1f7e1d9c75c7319ed12a5eda06e2f0bc57b3bac6 | wangchuan |0 | |     build,客户端包
74c44fc7e16830977a311d747386fe920aefd855 | wangchuan |1 |a9b689c6b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
a9b689c6b2f32d2fdd86617f81d4f2c375506f90 | wangchuan |1 |personal_login/js/webLogin.js |     bug
4c332667335dda5b93638de3b74dd8b6e11970ec | zagger |0 | |     build
c1b4485e1f54916615f3e8755e5852ccd3c89801 | wangchuan |1 |personal_login/js/webLogin.js |     web登录bug
b64fb0bec2a199cade6b8cc549c1201c17495136 | zagger |1 |76556cfd8 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
76556cfd897824da179fb56f2eda28eb93d45764 | zagger |4 |css/forget-pwd.css; css/your_style.css; forget-pwd.html; js/vdi/forget.js |     忘记密码bug修复
74563be96fa18ae487ca16bf7be5fc2476ec19cf | wangchuan |1 |5f7ef8c9b |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
ab3dea68234e54441b18418a18ed88c84eeef692 | wangchuan |1 |personal_login/js/webLogin.js |     bug
5f7ef8c9bf80cd834a7af5b031cd45af7ee09b8e | wangchuan |1 |7a5a43699 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
7a5a4369925b85785563c16f7ad18c81308d6732 | zagger |3 |js/vdi/auth/controllers.js; js/vdi/forget.js; js/vdi/utils/user.js |     验证码获取问题修复
2680e5fc7f4dd4c3b2ebbeb83f5fd0db49481880 | wangchuan |1 |personal_login/js/components/bind-mail-modal.js |     假数据；样式
73ca9f9f350bafe84d2921ccaab2d3085ed34e0b | zagger |1 |js/vdi/utils/ui.js |     初次登录修改密码，自动飘红的问题
fb37c1e8f45330eba9111b1526f5ce9bb0588db8 | zagger |1 |bc55a2d1f |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
bc55a2d1f454818d705ec0c986dbc835d4df4921 | zagger |1 |views/vdi/common/force-modify-pwd.html |     特殊字符无法显示的问题
144f4566dee9b273391d1a76f843d7f22bf38594 | wangchuan |1 |10b15c1eb |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
147c3a3b6d109b6ac7326f200c67cc2693ecd2b9 | wangchuan |2 |personal_login/css/webLogin.css; personal_login/js/webLogin.js |     web桌面：登录时效性；样式
10b15c1eb4f0979f63178b998c54384e38c8870a | zagger |1 |js/vdi/monitor/alarm.js |     告警信息传参 都传字符串
1637c119566a92719891faf01c41ae08805db528 | wangchuan |0 | |     客户端包
286f0bc23c0d5ae09415da360a4cd1d3c613eab7 | zagger |0 | |     build for package
0c6b0dce2c504bcd8d69ea19de6b8e7a1a3eb75d | wangchuan |1 |a7b9cb735 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
3ef467401aff113d6b58ea97909088b39003c9ef | wangchuan |4 |personal_login/js/components/bind-mail-modal.js; personal_login/js/components/user-form.js; personal_login/js/webLogin.js; personal_login/webLogin.html |     web个人桌面登录
a7b9cb73542165014cac6eb2f31baba2a5fdc691 | wangchuan |0 | |     客户端重新打包
2a7dc514de6e8c2b828897cd2676c238e1d2befe | zagger |4 |js/vdi/auth/controllers.js; views/vdi/common/account-password-modify.html; views/vdi/common/time-modify-pwd.html; views/vdi/login.html |     添加定时修改密码逻辑
79db70fc2c358dbc5b000fb98b90b29d541978d7 | zagger |1 |views/vdi/app-menu.html |     恢复菜单显示代码
1dfea75125abfaf55813b349dbfbe7b3a910db71 | jiazhihao |0 | |     添加客户端包
9c215df4acb16275487c671d7532d0e9d60491e4 | jiazhihao |0 | |     build
7261492d6558289b5c5fddd3beeca659912a8b65 | jiazhihao |1 |b3b483041 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc        merge
e82fd02621f88926eb03f19b1a39c7f37aacd385 | wangchuan |2 |personal_login/js/components/pwd-expired-tip-modal.js; views/vdi/dialog/security/system/add_edit_security_system.html |     代码优化
b3b48304196d4f9dc9b011d9c11a5dd45cc6dc0e | wangchuan |2 |js/vdi/security/system/controller.security.system.js; views/vdi/security/system/security_system.html |     系统安全：禁止关闭策略
9481ebd183cb479d3f1ae55104a1254977021aa8 | zagger |0 | |     build
e7f174e63a1a4151d818a213ce1568f3c2424107 | zagger |1 |views/vdi/app-menu.html |     显示-菜单展开和收缩错误修复
6ea94a448222ddf4e54989fdcee2049a5b2a37f7 | zagger |1 |921174043 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
92117404360bc02790ae072e6d72ce869f943709 | zagger |2 |img/new_login_icon/header_bg.png; js/vdi/auth/controllers.js |     强制绑定邮箱-回显邮箱地址
52eb47aefaa7310406b7a5ec4d562c57a72554f0 | wangchuan |0 | |     提交vdi客户端资源包
eb0c5d5f59d0f1430fd369e3bec4d0607aa16686 | zagger |0 | |     build
4052445b97019e9cb8be02206961fa09821b11cc | zagger |1 |88e8431cc |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
88e8431cc4c50de1b31419f743dea54c3b971b29 | zagger |0 | |     build
bd9f5efd53496dc226de04fa94b037b4bce3682a | zagger |3 |js/vdi/system/system-settings.js; js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     解绑认证服务器url修改    导入帐号-传参问题``
ea9266292a5aa66e85eaf05699bcf00f30af77a7 | zhangyao |7 |js/vdi/security/common.js; js/vdi/security/desktop.js; js/vdi/system/system-log.js; js/vdi/system/system-logo-settings.js; js/vdi/utils/ui.js; views/vdi/security/desktop.html; views/vdi/system/set-general.html |     修改共享文档上的问题
34ebd2bc10611789edbfb748e376b584f7c26994 | zagger |1 |4628281d5 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
4628281d514fa464b3f6e6a385e5a3f8f543a2d4 | zagger |1 |js/vdi/monitor/alarm.js |     告警信息获取
bcde666afb3abc80c952319b9927655f1fa473d7 | zhangyao |1 |85f64b6c4 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
85f64b6c4fe5c56799303bdb8ef1106970e0b460 | zhangyao |3 |js/vdi/security/desktop.js; js/vdi/system/system-log.js; views/vdi/dialog/system/backup-log-config.html |     备份日志去掉 请选择
7d397c209fcfe0a7579c35ddc2b92d160b6a1b18 | zagger |0 | |     built
2d8ce4b6d1af56b5b2eb08b0dbc5984cc3a7df3c | zagger |1 |742fc3c85 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
742fc3c858c5ac111d46a1f6526909423ee0e772 | zagger |3 |js/vdi/user/admin-user.js; views/vdi/user/admin.html; views/vdi/user/uaa.html |     zicebugs
8dd38d6ec3d6f5f30388dea020a7bdebfe55f3ba | wangchuan |1 |cfad25112 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
d7747c59227e09123908622aaeb13c4f1ffc8627 | wangchuan |2 |js/vdi/system/recycle/controller.system.recycle.js; personal_login/js/components/pwd-expired-tip-modal.js |     代码优化
cfad251120e55fd2f942aae3735fb40af918b6a7 | zagger |0 | |     build
6cbfbf6c98b8a30d035dc5c7074407b3a8c728dc | zagger |1 |js/vdi/monitor/alarm.js |     导出下载
0acbab5778eb8cf4503ac1e4eedd923a154b64e5 | zagger |0 | |     build
f2980c1b711fe900c5f8be5fb6bcf3c72f49a14a | zagger |1 |5c7bc037c |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
5c7bc037cd1c3aceb883f8fa46b0d27f710b8a11 | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     编辑邮箱接口添加
a087b0db0a5956453567e3e34977e108c213aa90 | zhangyao |1 |2f6f84f4e |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2f6f84f4eb71ccd3bafca1cd938e2e6f7416ae3e | zhangyao |4 |js/vdi/desktop/personal.js; js/vdi/security/common.js; js/vdi/security/shared.js; views/vdi/security/group.html |     修复自测发现的问题
a6e0631cae2f2b0d4cfa6d4c58af8ef8beac5251 | wangchuan |1 |b8e82d09d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
b8e82d09dbcf1ebd52246d26318c4a70061ee236 | zagger |1 |86f3810f2 |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
86f3810f2d9ff3dd5797a133e4f10a72beb4cb3c | zagger |2 |js/vdi/forget.js; js/vdi/user/uaa.js |     url地址显示问题
cf66b32e39c140d0b72c1162ab5ca79e9915db05 | zhangyao |1 |b88c2842b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
b88c2842be2abc257979a26328debcca1b340e9a | zhangyao |12 |js/vdi/bootstrap.js; js/vdi/config/http.js; js/vdi/desktop/personal.js; js/vdi/security/common.js; js/vdi/security/desktop.js; js/vdi/security/group.js; js/vdi/security/shared.js; views/vdi/dialog/security/manage_desktops_for_strategy.html; views/vdi/dialog/security/new_group.html; views/vdi/dialog/security/new_rule.html; views/vdi/security/desktop.html; views/vdi/security/group.html |     自测问题修复
127f4979d2037679736a661cfeb62f8df96661b8 | zagger |0 | |     build
88390c68ca7e8b5b344641c2c734c82bdc124524 | zagger |1 |js/vdi/scheduler/disk.controller.js |     网盘传递参数bug
5b8e82c3c146b9575fa75a8229d29e531368fbd2 | zhangyao |1 |c5c31c6cc |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
c5c31c6cc8dba9fbe99cd51f33ee355e0393cc59 | zhangyao |9 |includes/pagination.html; js/vdi/security/desktop.js; js/vdi/system/system-log.js; js/vdi/vdi.js; views/vdi/dialog/desktop/personal_detail.html; views/vdi/dialog/desktop/personal_download_video.html; views/vdi/help/deploy.html; views/vdi/system/admin-log.html; views/vdi/system/user-log.html |     自测问题修复
9b904fca04334fd87a8ab367e41fbc865b850a81 | zagger |0 | |     build
a75ddded10ab9ee72644628865a963c985f5b980 | zagger |2 |js/vdi/monitor/alarm.js; views/vdi/dialog/monitor/set-keep-time.html |     告警信息-补缺少接口-获取配置接口
2c88d24d442256dee70df8dfbe4ff414bb0d82ee | zagger |1 |js/vdi/user/uaa.js |     普通帐号修改邮箱-报错
c13c04b9c37150097225613ab4cafb6b23d3f734 | wangchuan |3 |personal_login/css/webLogin.css; personal_login/js/webLogin.js; personal_login/webLogin.html |     web个人桌面:样式
52437baf4eb4f172e5ba9b43523f461eea662d4a | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     添加重置密码对邮箱的判断，没有邮箱无法重置密码
0a98f4d4b96795f72fb11bcccc8d3fa03bae5a60 | wangchuan |7 |personal_login/css/webLogin.css; personal_login/js/components/bind-mail.js; personal_login/js/components/mail-after-login-modal.js; personal_login/js/components/modify-default-pwd-modal.js; personal_login/js/components/password-expired-tip.js; personal_login/js/webLogin.js; personal_login/webLogin.html |     web个人桌面登录:代码优化
0d21c5124415c503abf40acd7add093ae82f918b | wangchuan |1 |personal_login/selectDesk.html |     恢复文件历史
1595948e7c608fb1b803c6cdd747d3d1d6aaf0a7 | zagger |0 | |     build代码
2d8007b6504c300ffca44b8a720137502ef92f2e | zagger |1 |views/vdi/user/admin.html |     解决管理帐号普通管理员无法选中admin用户的问题
4b00c23f5dbbc21e9db140918e7644d96470cb9a | zagger |1 |js/vdi/menus.js |     解决网盘菜单没有显示wenti
ca35d42e1587cededba48babe3ea1f4469fccc48 | zagger |2 |js/vdi/bootstrap.js; js/vdi/config/http.js |     还原前端跨域问题代码
21386f3376c792f50f70adb550f72eaf0984dc82 | zagger |1 |9a921eaeb |     Merge branch '5.1.4-vpc' of http://bbt.os-easy.com/hanxiaoxiang/ngconsole into 5.1.4-vpc
9a921eaebad273ef05a241a8c32d1a95d277dd79 | zagger |5 |js/vdi/user/uaa.js; views/vdi/dialog/user/user_admin_edit_email.html; views/vdi/dialog/user/user_common_department_add.html; views/vdi/dialog/user/user_common_department_modify.html; views/vdi/user/admin.html |     1.部门名称不能有空格    2.管理帐号-loading问题
4b3f0d9b4a23af14ca8474d454045b26d503ec83 | wangchuan |1 |1f3181ced |     Merge branch '5.2.0-vpc' into 5.1.4-vpc
1f3181ced3e92c40873a091fcff239688f687e06 | wangchuan |1 |4d81cba9d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
4d81cba9d05b4a2b17ee16d19fb803c148cd9efb | zhangyao |8 |js/vdi/bootstrap.js; js/vdi/config/http.js; js/vdi/desktop/personal.js; js/vdi/help/quick-deploy.js; js/vdi/security/common.js; js/vdi/security/group.js; views/vdi/dialog/security/manage_desktops_for_strategy.html; views/vdi/help/deploy.html |     根据自测用例自测
e95bddce2f8569301d092e95127e74add697ba2a | zhangyao |5 |js/vdi/desktop/personal.js; js/vdi/init.js; js/vdi/plan/api.js; js/vdi/resource/api.js; js/vdi/template/api.js |     修复自测问题
c7039bffe5cd21e604bbf7eb22482738da61be87 | zagger |4 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js; views/vdi/dialog/user/admin_uaa_import.html; views/vdi/dialog/user/common_uaa_import.html |     导入帐号-细节处理
e1c7dcc454804809a4386a25b816b9e2274882f4 | zagger |3 |js/vdi/template/system-iso.js; js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     导入帐号-分组信息改变，触发change事件处理
e016160fa061558dba34ee85f642531271d603ce | wangchuan |1 |847d70cbe |     Merge branch '5.2.0-vpc' into 5.1.4-vpc
5ab6fa992e2d8c67315cf8b0f0fe2c42f4b8955c | zagger |1 |js/vdi/template/system-iso.js |     添加iso移动至接口
b8a7f246a61af0837c54fdddf100ec5340d16cd7 | zagger |0 | |     添加权限返回数据-以便联调
3a22b5647f8376d2f3d95b9164abd15d472e0ff1 | zagger |2 |js/vdi/user/role.js; views/vdi/user/role.html |     默认角色不能删除的问题
03152d2c0effafdfdb751b31594968d9f3501c41 | zagger |1 |92f69e33b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
92f69e33be9cc92271a63ae08b8a3f98679630e1 | zagger |1 |js/vdi/user/uaa.js |     分页参数传错了
3b77e98455bf3a76d5753433ffd3766fbf8cf710 | zhangyao |1 |847d70cbe |     xMerge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
847d70cbe5e53afb1e7a2838bc4e033aadef83ac | zhangyao |2 |views/vdi/system/admin-log.html; views/vdi/system/user-log.html |     日志主机字段修改为 host
372b073e354b1e937675cbc850d7a8704045d9b4 | zhangyao |0 | |     build
83f0b07a3be47d4c76d4dba656821bdada90269f | zhangyao |1 |ea28cfd75 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ea28cfd75aedd53245f9971314968ce1c7be1d9a | zhangyao |5 |js/vdi/desktop/personal.js; js/vdi/security/group.js; js/vdi/system/system-log.js; views/vdi/dialog/desktop/personal_detail.html; views/vdi/security/group.html |     fix bugs
bbd819cb0597385e9933299d46ba098f6e69dce7 | wangchuan |0 | |     build
7083d9c539cab50e7dcc3a8c9495e4fad43998be | wangchuan |1 |personal_login/js/webLogin.js |     修改初始密码url
1b7e676b71c307150e2b8412dc91777c8bd5d2c9 | wangchuan |1 |bfbc72635 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
39a20c75dbdefb911e7118093699b47f43390a8e | wangchuan |4 |personal_login/js/components/user-form.js; personal_login/js/rules.js; personal_login/js/validator.js; personal_login/js/webLogin.js |     web桌面:代码优化
bfbc72635f090f51a3d77d60fae851b984927b50 | wangchuan |1 |84a4f3492 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
696e9332689a593b1cffa4b765749fcb539b5de8 | wangchuan |4 |personal_login/css/webLogin.css; personal_login/js/components/pwd-complexity-tooltip.js; personal_login/js/webLogin.js; personal_login/views/user-form.html |     web桌面：bug
84a4f3492fe8538aa0a54837eb4907d15c0ac73b | wangchuan |1 |46d7a865d |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
f2da45bc6a06fab138dfa556adb0ab4717baff4b | wangchuan |1 |personal_login/js/components/user-form.js |     web桌面：bug修改
693e875cf39ca3a40e391160071202b95b940494 | wangchuan |1 |personal_login/js/webLogin.js |     web桌面：bug修改
46d7a865d221fcd00d36b568bf0a0c849ac95d38 | zhangyao |1 |ada7af1d0 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
ada7af1d083f81deba14d9f590392abe48002deb | zhangyao |10 |js/vdi/desktop/personal.js; js/vdi/security/desktop.js; js/vdi/security/shared.js; js/vdi/system/system-log.js; views/vdi/desktop/personal.html; views/vdi/dialog/desktop/personal_delete.html; views/vdi/dialog/desktop/personal_detail.html; views/vdi/dialog/security/manage_desktops_for_strategy.html; views/vdi/dialog/security/new_desktop_strategy.html; views/vdi/dialog/system/backup-log-config.html |     fix bugs
0719136371c447a0a62e4632ea36741584f484c4 | wangchuan |1 |716a6efe2 |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
3c37dcdd94b43efa82e016975472e0177aaee98c | wangchuan |6 |personal_login/js/components/mail-after-login-modal.js; personal_login/js/components/password-expired-tip.js; personal_login/js/components/pwd-complexity-tooltip.js; personal_login/js/components/user-form.js; personal_login/js/webLogin.js; personal_login/webLogin.html |     web桌面登录：代码优化
716a6efe279b1f33085c91611cf8413afca7ddd5 | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     重置密码
bc1b0f2c5db1bb7e0bc961f450f018f9d79be61f | zhangyao |3 |js/vdi/utils/ui.js; js/vdi/vdi.js; views/vdi/common/account-password-modify.html |     修复修改密码的校验问题
062ff63c4d359252c2bc68c82a431f2217539e83 | zagger |1 |2f6a1009d |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2f6a1009d3e4891a1b52e27e2d90a8d39bc79046 | zagger |1 |views/vdi/app-header.html |     解除uaa禁用密码修改功能
fc6ca8a7b73bcd2ce523fef1fd72b2ad46d574e6 | zhangyao |1 |ngconsole-webpack-plugin.js |     资源的处理过程增加魔法替换功能
d06f3254983c598df1962991d5be7ed3904d335e | zagger |1 |js/vdi/user/admin-user.js |     build
d9be9521b3dff8dcd856db40dd286b09fd6015fa | zagger |1 |package-lock.json |     build
e0c45fa46681db5fbe25334fc66a20eb5abfda72 | zagger |1 |0ef7cca6b |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
0ef7cca6bb481cbd9b63e13aa33d4908a55fbc3a | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     uaa_id
97a3a6126b6bbd16b3306cc46e0e127c9e7b0518 | wangchuan |0 | |     build
e3994d24901aa09d2fbf239b0dd7313c174a025e | wangchuan |0 | |     假数据
64ef49795cd6a4e9dba3c1e9eda9be6343319cb1 | wangchuan |1 |js/vdi/security/client/controller.security.client.js |     终端安全：bug
e8673848c4bc0b58d5228390dc5d37349ff5aeba | wangchuan |1 |303a90ef6 |     Merge branch '5.2.0-vpc' into 5.1.4-vpc
303a90ef62c178caf5425f76355cdfc8d4f124a3 | wangchuan |1 |966f7ccd9 |     合并5.2.0-vpc到5.1.4-vpc
966f7ccd927d0e6deac1cea4142280ca0f95488a | zhangyao |1 |5f0bd32aa |     Merge branch '5.1.4-vpc' of e.coding.net:mystorp/ngconsole into 5.1.4-vpc
5f0bd32aa689bfb8e6cf11e7295925775c8c2e60 | zagger |8 |js/vdi/auth/controllers.js; js/vdi/scheduler/disk.controller.js; js/vdi/user/admin-user.js; js/vdi/user/role.js; js/vdi/utils/user.js; js/vdoi/main.js; views/vdi/app-header.html; views/vdi/user/admin.html |     1.添加dms权限配置带啊2.网盘添加排除本地帐号的过滤参数3.管理帐号添加对admin帐号的特殊处理
4af52c41cb5fc0cd5952bdad0187b910ad3efb77 | wangchuan |1 |views/vdi/resource/storage/storage.html |     恢复网盘存储
3437158385efa243c74e0a6629957956162f6351 | wangchuan |3 |personal_login/js/components/user-form.js; personal_login/js/rules.js; personal_login/js/webLogin.js |     web个人桌面:联调
e3887866461dae4a731037a7f688f7c4d9e4fe37 | wangchuan |11 |personal_login/css/webLogin.css; personal_login/js/components/bind-mail.js; personal_login/js/components/mail-after-login-modal.js; personal_login/js/components/modify-default-pwd-modal.js; personal_login/js/components/user-form.js; personal_login/js/validator.js; personal_login/js/webLogin.js; personal_login/selectDesk.html; personal_login/views/associate-mail-modal.html; personal_login/views/user-form.html; personal_login/webLogin.html |     web个人桌面：联调
64d187e366e4ba8d7294c9585134eb958a457da8 | zagger |0 | |     build for zice
73d6f47f498e1ebc1fe32e8a9bab49fdcaac6dc0 | zagger |6 |js/vdi/auth/controllers.js; js/vdi/forget.js; js/vdi/user/admin-user.js; js/vdi/user/uaa.js; js/vdi/utils/user.js; views/vdi/dialog/user/admin_uaa_import.html |     帐号部门问题修改
0979aa87c93ee7fbff2e01e43ad6a46b694ac56c | zagger |2 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js |     部门帐号-一键同步传参
e7a2966e3632d50884887cabd5b4d7a20dfdbc75 | wangchuan |15 |js/vdi/utils/validator.js; personal_login/css/webLogin.css; personal_login/forgetPwdPage.html; personal_login/index.html; personal_login/js/components/mail-after-login-modal.js; personal_login/js/components/modify-default-pwd-modal.js; personal_login/js/components/pwd-complexity-tooltip.js; personal_login/js/components/user-form.js; personal_login/js/rules.js; personal_login/js/validator.js; personal_login/js/webLogin.js; personal_login/views/associate-mail-modal.html; personal_login/views/user-form.html; personal_login/webLogin.html; personal_login/webRegister.html |     web个人桌面：联调
70aebb2fa38e9e0271bc8376bb377d1f967ef0be | wangchuan |1 |e85217dbe |     Merge remote-tracking branch 'base/5.1.4-vpc' into 5.1.4-vpc
d631afad4041d3f99cb03f7b855108a63caa6397 | wangchuan |1 |views/vdi/dialog/template/template_imgManage.html |     提交到错误分支，恢复历史
835fa003ac8b29c21ede9f4fefb387a4067735b6 | wangchuan |1 |views/vdi/dialog/template/template_imgManage.html |     接口返回更改
39f1fa4632282834e49392168cdfaf5a77d28976 | wangchuan |2 |views/vdi/dialog/resource/pool/config_storage.html; views/vdi/dialog/resource/storage/new_storage.html |     桌面录屏存储设备
e85217dbe42c5d530b13af17152b123718a239d1 | zagger |4 |js/vdi/auth/controllers.js; js/vdi/forget.js; js/vdi/utils/user.js; views/vdi/common/login-step2.html |     登录代码优化
e2cef0bbeabbd1b643e48665793cc015b0a17a0b | wangchuan |1 |js/vdi/resource/storage/controllers.js |     提交到错误分支，恢复历史
466757b7b9078d0ae12c36eb3b990238ca0430e4 | wangchuan |1 |js/vdi/resource/storage/controllers.js |     分布式存储：解决bug，14880
f69a1487e86c6e56c213ab0dc0a56ced2513bde6 | zagger |1 |js/vdi/spice.js |     还原端口号
3a036a5d34d86445c0f0973c79c16797a7a9487a | zagger |0 | |     端口号修改测试
95e4c0b50e45d51fdaa3873454462bb336e4262b | zagger |2 |js/vdi/monitor/controllers.js; js/vdi/spice.js |     端口号修改测试
75028b07d12a7070a4238307614437f6f61358e4 | zagger |10 |desktopScreenshot.html; js/vdi/bootstrap.js; js/vdi/spice.js; js/vdi/system/system-log.js; js/vdi/template/browser.openVNC.js; js/vdi/utils/user.js; personal_login/js/webLoginSpice.js; ssh_terminal/terminal.js; views/idv/desktop/desktopScreenshot.html; views/voi/desktop/desktopScreenshot.html |     打包测试接口统一
7178aec58673c4a9086b24dd2033d42a31fb45de | zagger |1 |.gitignore |     添加.gitignore
61b9be9382140293484977fd5f206f2969a85007 | zagger |0 | |     打包后端验证问题
f38e476716de773a4090ccf26856f70ed9561cbc | zagger |1 |js/vdi/utils/user.js |     验证码laoding问题
f9fd22772dcc4afdfa184612548dbb31fc70a722 | zagger |4 |js/vdi/auth/controllers.js; js/vdi/forget.js; js/vdi/utils/user.js; views/vdi/common/login-step2.html |     登录接口联调
d399feaaed3083cf7f9a7e27989d7a3e42336747 | wangchuan |2 |js/vdi/utils/validator.js; package.json |     通用form验证
5773e0e249980b349d7bfa3795aa81e3050f4b51 | zagger |3 |js/vdi/monitor/policy.js; js/vdi/system/system-settings.js; views/vdi/system/set-general.html |     配置邮箱服务器-前端代码完成
eaa54e96b0efdb760744dd809a7b7c02ea196259 | zagger |2 |js/vdi/monitor/policy.js; views/vdi/dialog/monitor/config.html |     告警信息+新增认证服务器离线
045d0ee3d18c03473a752de22df0141f6bdf5df1 | zagger |4 |js/vdi/user/admin-user.js; js/vdi/user/uaa.js; views/vdi/user/admin.html; views/vdi/user/uaa.html |     帐号部门接口文档给-接口联调
e4f4020116e838df69a40991db2c071a743e1028 | wangchuan |1 |js/vdi/terminal/controller.terminal.js |     终端管理：终端设置，去掉H264、磁盘共享到桌面联调
d6a895aec2f37e9335c9122e2f1b20d50cc8d5b9 | wangchuan |0 | |     终端安全：假数据
cbbac9ddd2976ef478d1c7de9da264edfa64f3e3 | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/dialog/security/client/manage_security_client.html |     终端安全：联调
0470e428c4f60464f85ca90b723385d84238a811 | wangchuan |1 |js/vdi/security/system/controller.security.system.js |     系统安全：联调
69d3cc3e6c3b65889d907e0349ad82d14ad19408 | wangchuan |0 | |     系统安全：假数据
04602c746448d9c1d723a32df1f6d9f0d798bed7 | wangchuan |1 |views/vdi/security/system/security_system.html |     系统安全:bug修改
b1ed18ce7a9168c7d2e0b4c6416ddfd77d29db95 | wangchuan |1 |js/vdi/system/recycle/controller.system.recycle.js |     回收站：代码优化
b2c185011b37ad5036a6a18988f7eec8d8acdd4b | wangchuan |3 |js/vdi/security/system/controller.security.system.js; views/vdi/dialog/security/system/add_edit_security_system.html; views/vdi/security/system/security_system.html |     系统安全：联调
1e9703dcee5b6d25717db97ac7d536da6fcd9aa2 | wangchuan |0 | |     终端安全：假数据
50794e7038bd7795c5772962beebddb7ecc02acd | wangchuan |0 | |     终端安全：假数据
16052b7eb7e834325c3c3c740df4511d18a46abb | wangchuan |1 |css/your_style.css |     禁用下的input样式
343c0e6ee279b06e78564445c7f0c7b83328e897 | wangchuan |2 |js/vdi/security/client/controller.security.client.js; views/vdi/dialog/security/client/manage_security_client.html |     终端安全：联调
f9d64d70d62ab9b3980a67cbfc981f7af9e7a89f | wangchuan |1 |js/vdi/security/client/controller.security.client.js |     终端安全：联调
79c82daee5d835de3ce5dba3101ac30501740895 | zagger |2 |js/vdi/auth/controllers.js; js/vdi/utils/user.js |     登录之后弹弹窗临时解决
80e7f16416ab321d4132fb0885b012a151f5d7be | zagger |4 |forget-pwd.html; js/vdi/auth/controllers.js; js/vdi/forget.js; views/vdi/common/force-modify-pwd.html |     强制修改密码接口+忘记密码，接口代码
23109dd74448876a83c1250f762c0a0c3db666c5 | zagger |7 |css/your_style.css; js/vdi/auth/controllers.js; js/vdi/scheduler/disk.controller.js; js/vdi/utils/user.js; views/vdi/common/force-modify-pwd.html; views/vdi/common/login-step2.html; views/vdi/login.html |     登录初次联调-走完-登录第一步到第二部，登录后是否弹窗----未完成：密令-验证码-走流程
988e08ecee8369745445b1590e41b778d87124f8 | zagger |2 |js/vdi/scheduler/disk.controller.js; views/vdi/scheduler/disk.html |     网盘帐号部门-添加管理帐号和域账号
64d2bcd4968b3071463758e97d2ee8205ea494b5 | zagger |2 |js/vdi/monitor/controllers.js; views/vdi/monitor/host.html |     图标样式设置
07ae4bf6182d2cfce1b1229e26af3fc82af7b536 | zagger |2 |js/vdi/monitor/common.js; js/vdi/monitor/controllers.js |     监控-代码整理
3d64ba4ae4b4391e43a6bd50aad74fcd09fcdfc7 | zagger |1 |js/vdi/monitor/controllers.js |     监控-定时器处理
b40bb840589de2ffcf1232a576d6dd4c570dacb5 | zagger |1 |2bc007309 |     Merge branch '5.1.4-vpc' of http://172.16.203.254/hanxiaoxiang/ngconsole into 5.1.4-vpc
2bc0073097d0bb8337a02d4a4750007dedff14d7 | zagger |2 |js/vdi/monitor/controllers.js; views/vdi/monitor/host.html |     监控-画图代码
6c2ff9d30065b3bc0775496bc9acbfe45f84be80 | zagger |1 |js/vdi/monitor/controllers.js |     监控-时间联调
e1e69a706e849cb95377576352782db7df8941b2 | zhangyao |1 |views/vdi/system/iso.html |     修复安装包下载链接问题
3b53f894ec0a91291fdff22768c38d6ba14985e2 | zhangyao |1 |6f6bdfc80 |     fix conflicts
6f6bdfc80618c04cb280fd806c1aa4dc88fe3772 | zhangyao |0 | |     build
d37c874fd549fbbe9ce921738ac934f66a1cade5 | zhangyao |1 |js/vdi/terminal/controller.terminal.js |     修复手动排序报错
0ebe948fde7124dadeb642531a6e5a2eb95fd52b | zhangyao |1 |js/vdi/terminal/controller.terminal.js |     终端自动排序界面，默认不自动按序号排序
efdba7019a2eed23cb33c45cc9a836cba77d0042 | zhangyao |1 |js/vdi/terminal/controller.terminal.js |     适配自动排序需求变更
4 : 40
 : 1
5 : 26
6 : 18
7 : 15
8 : 9
9 : 5
10 : 4
11 : 2
21 : 1
12 : 2
13 : 2
0 : 194
14 : 1
23 : 1
1 : 610
15 : 2
2 : 150
16 : 1
3 : 64


### [vim](https://github.com/KiteAB/.config/tree/master/zsh)

- w!!  
- jj <Esc>
- enter
- enter+c
- enter+d
- v+%
- visual模式下，S"
- cs"'
- c-n
- v选中后，再按c-n
- n/N下一个和上一个光标
- q skip当前选中的
- c-up c-down 自由选中多个光标
- coc.vim

	- Language server protocol
微软开发的 让任何编辑器不限编程语言都能享受统一补全体验的协议
	- 需要安装nodejs

		- npm i -g neovim yarn

	- coc也需要安装插件 

		- CocInstall coc-json

	- [coc-settings.json](https://github.com/neoclide/coc.nvim/blob/master/data/schema.json)

	  {
	   |   "$schema": "http://json-schema.org/draft-07/schema#",
	   |   "description": "Configuration file for coc.nvim",
	   |   "additionalProperties": false,
	   |   "definitions": {
	   |     "languageServerBase": {
	   |       "type": "object",
	   |       "properties": {
	   |         "enable": {
	   |           "type": "boolean",
	   |           "default": true
	   |         },
	   |         "cwd": {
	   |           "type": "string",
	   |           "default": "",
	   |           "description": "Working directory of languageserver, absolute path or relative to workspace folder, use workspace root by default"
	   |         },
	   |         "disableDynamicRegister": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Disable dynamic registerCapability feature for this languageserver to avoid duplicated feature regstration."
	   |         },
	   |         "disableWorkspaceFolders": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Disable workspaceFolders feature for this languageserver."
	   |         },
	   |         "disableSnippetCompletion": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Disable completion snippet feature for this languageserver, the languageserver may not respect it."
	   |         },
	   |         "disableDiagnostics": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Disable handle diagnostics for this languageserver."
	   |         },
	   |         "disableCompletion": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Disable completion feature for this languageserver."
	   |         },
	   |         "formatterPriority": {
	   |           "type": "number",
	   |           "default": 0,
	   |           "description": "Priority of this languageserver's fomatter."
	   |         },
	   |         "env": {
	   |           "type": "object",
	   |           "default": null,
	   |           "description": "Environment variables for child process."
	   |         },
	   |         "stdioEncoding": {
	   |           "type": "string",
	   |           "default": "utf8",
	   |           "description": "Encoding used for stdio of child process."
	   |         },
	   |         "rootPatterns": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Root patterns used to resolve rootPath from current file, default to workspace root",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "requireRootPattern": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "If true, doesn't start server when root pattern not found."
	   |         },
	   |         "ignoredRootPaths": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Absolute root paths that language server should not use as rootPath, higher priority than rootPatterns.",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "filetypes": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Supported filetypes, add * in array for all filetypes.",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "additionalSchemes": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Additional uri schemes, default schemes including file & untitled.",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "revealOutputChannelOn": {
	   |           "type": "string",
	   |           "default": "never",
	   |           "description": "Configure message level to show the output channel buffer",
	   |           "enum": ["info", "warn", "error", "never"]
	   |         },
	   |         "progressOnInitialization": {
	   |           "type": "boolean",
	   |           "default": true,
	   |           "description": "Enable progress report on languageserver initialize."
	   |         },
	   |         "initializationOptions": {
	   |           "type": "object",
	   |           "default": {},
	   |           "description": "initializationOptions passed to languageserver"
	   |         },
	   |         "settings": {
	   |           "type": "object",
	   |           "default": {},
	   |           "description": "Settings of languageserver"
	   |         },
	   |         "trace.server": {
	   |           "type": "string",
	   |           "default": "off",
	   |           "enum": ["off", "messages", "verbose"],
	   |           "description": "Trace level of communication between server and client"
	   |         }
	   |       }
	   |     },
	   |     "languageServerSocket": {
	   |       "type": "object",
	   |       "allOf": [{ "$ref": "#/definitions/languageServerBase" }],
	   |       "required": ["port", "filetypes"],
	   |       "additionalProperties": false,
	   |       "properties": {
	   |         "port": {
	   |           "type": "integer",
	   |           "description": "Port number of socket server"
	   |         },
	   |         "host": {
	   |           "type": "string",
	   |           "default": "127.0.0.1",
	   |           "description": "Host of server"
	   |         },
	   |         "disableWorkspaceFolders": {},
	   |         "disableSnippetCompletion": {},
	   |         "disableDynamicRegister": {},
	   |         "disableDiagnostics": {},
	   |         "disableCompletion": {},
	   |         "formatterPriority": {},
	   |         "enable": {},
	   |         "rootPatterns": {},
	   |         "requireRootPattern": {},
	   |         "ignoredRootPaths": {},
	   |         "filetypes": {},
	   |         "additionalSchemes": {},
	   |         "revealOutputChannelOn": {},
	   |         "progressOnInitialization": {},
	   |         "initializationOptions": {},
	   |         "settings": {},
	   |         "stdioEncoding": {},
	   |         "trace.server": {}
	   |       }
	   |     },
	   |     "languageServerModule": {
	   |       "type": "object",
	   |       "allOf": [{ "$ref": "#/definitions/languageServerBase" }],
	   |       "required": ["module", "filetypes"],
	   |       "additionalProperties": false,
	   |       "properties": {
	   |         "module": {
	   |           "type": "string",
	   |           "default": "",
	   |           "description": "Absolute path of javascript file, should works in IPC mode"
	   |         },
	   |         "args": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Extra arguments of module",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "runtime": {
	   |           "type": "string",
	   |           "default": "",
	   |           "description": "Absolute path of node runtime."
	   |         },
	   |         "execArgv": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Argv passed to node when using module, normally used for debugging, ex: [\"--nolazy\", \"--inspect-brk=6045\"]",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "transport": {
	   |           "type": "string",
	   |           "default": "ipc",
	   |           "description": "Transport kind used by server, could be 'ipc', 'stdio', 'socket' and 'pipe'",
	   |           "enum": ["ipc", "stdio", "socket", "pipe"]
	   |         },
	   |         "transportPort": {
	   |           "type": "integer",
	   |           "description": "Port number used when transport is 'socket'"
	   |         },
	   |         "cwd": {},
	   |         "env": {},
	   |         "enable": {},
	   |         "disableDynamicRegister": {},
	   |         "disableWorkspaceFolders": {},
	   |         "disableSnippetCompletion": {},
	   |         "disableDiagnostics": {},
	   |         "disableCompletion": {},
	   |         "formatterPriority": {},
	   |         "rootPatterns": {},
	   |         "requireRootPattern": {},
	   |         "ignoredRootPaths": {},
	   |         "filetypes": {},
	   |         "additionalSchemes": {},
	   |         "revealOutputChannelOn": {},
	   |         "progressOnInitialization": {},
	   |         "initializationOptions": {},
	   |         "stdioEncoding": {},
	   |         "settings": {},
	   |         "trace.server": {}
	   |       }
	   |     },
	   |     "languageServerCommand": {
	   |       "type": "object",
	   |       "required": ["command", "filetypes"],
	   |       "allOf": [{ "$ref": "#/definitions/languageServerBase" }],
	   |       "additionalProperties": false,
	   |       "properties": {
	   |         "command": {
	   |           "type": "string",
	   |           "default": "",
	   |           "description": "Executable in $PATH to start languageserver, should not used with module"
	   |         },
	   |         "args": {
	   |           "type": "array",
	   |           "default": [],
	   |           "description": "Arguments of command",
	   |           "items": {
	   |             "type": "string"
	   |           }
	   |         },
	   |         "detached": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Detach the languageserver process"
	   |         },
	   |         "shell": {
	   |           "type": "boolean",
	   |           "default": false,
	   |           "description": "Use shell for process"
	   |         },
	   |         "cwd": {},
	   |         "env": {},
	   |         "enable": {},
	   |         "disableDynamicRegister": {},
	   |         "disableWorkspaceFolders": {},
	   |         "disableSnippetCompletion": {},
	   |         "disableDiagnostics": {},
	   |         "disableCompletion": {},
	   |         "formatterPriority": {},
	   |         "rootPatterns": {},
	   |         "requireRootPattern": {},
	   |         "ignoredRootPaths": {},
	   |         "filetypes": {},
	   |         "additionalSchemes": {},
	   |         "revealOutputChannelOn": {},
	   |         "progressOnInitialization": {},
	   |         "initializationOptions": {},
	   |         "stdioEncoding": {},
	   |         "settings": {},
	   |         "trace.server": {}
	   |       }
	   |     }
	   |   },
	   |   "properties": {
	   |     "http.proxy": {
	   |       "type": "string",
	   |       "default": "",
	   |       "pattern": "^https?://([^:]*(:[^@]*)?@)?([^:]+|\\[[:0-9a-fA-F]+\\])(:\\d+)?/?$|^$",
	   |       "description": "The proxy setting to use. If not set, will be inherited from the `http_proxy` and `https_proxy` environment variables."
	   |     },
	   |     "http.proxyStrictSSL": {
	   |       "type": "boolean",
	   |       "description": "Controls whether the proxy server certificate should be verified against the list of supplied CAs",
	   |       "default": true
	   |     },
	   |     "http.proxyAuthorization": {
	   |       "type": ["null", "string"],
	   |       "description": "The value to send as the `Proxy-Authorization` header for every network request.",
	   |       "default": null
	   |     },
	   |     "http.proxyCA": {
	   |       "type": "string",
	   |       "description": "CA (file) to use as Certificate Authority",
	   |       "default": null
	   |     },
	   |     "npm.binPath": {
	   |       "type": "string",
	   |       "default": "npm",
	   |       "description": "Command or absolute path to npm or yarn."
	   |     },
	   |     "suggest.enablePreselect": {
	   |       "type": "boolean",
	   |       "description": "Enable preselect feature of LSP, only works on neovim",
	   |       "default": false
	   |     },
	   |     "suggest.maxPreviewWidth": {
	   |       "type": "number",
	   |       "default": 80,
	   |       "description": "Maximum width of floating preview window."
	   |     },
	   |     "suggest.enablePreview": {
	   |       "type": "boolean",
	   |       "description": "Add preview option to completeopt, default: false.",
	   |       "default": false
	   |     },
	   |     "suggest.floatEnable": {
	   |       "type": "boolean",
	   |       "description": "Enable floating window for documentation when possible.",
	   |       "default": true
	   |     },
	   |     "suggest.labelMaxLength": {
	   |       "type": "number",
	   |       "description": "Max length of abbr that shown as label of complete item.",
	   |       "default": 200
	   |     },
	   |     "suggest.detailMaxLength": {
	   |       "type": "number",
	   |       "description": "Max length of detail that should be shown in popup menu.",
	   |       "default": 100
	   |     },
	   |     "suggest.detailField": {
	   |       "type": "string",
	   |       "default": "preview",
	   |       "description": "Where to show the detail text of CompleteItem from LS.",
	   |       "enum": ["abbr", "menu", "preview"]
	   |     },
	   |     "suggest.autoTrigger": {
	   |       "type": "string",
	   |       "default": "always",
	   |       "description": "How should completion be triggered",
	   |       "enum": ["always", "trigger", "none"]
	   |     },
	   |     "suggest.languageSourcePriority": {
	   |       "type": "number",
	   |       "default": 99,
	   |       "description": "Priority of language sources."
	   |     },
	   |     "suggest.numberSelect": {
	   |       "type": "boolean",
	   |       "description": "Input number to select complete item, works on neovim >= 0.4.0 only.",
	   |       "default": false
	   |     },
	   |     "suggest.disableKind": {
	   |       "type": "boolean",
	   |       "description": "Remove kind field from vim complete item.",
	   |       "default": false
	   |     },
	   |     "suggest.disableMenu": {
	   |       "type": "boolean",
	   |       "description": "Remove menu field from vim complete item.",
	   |       "default": false
	   |     },
	   |     "suggest.disableMenuShortcut": {
	   |       "type": "boolean",
	   |       "description": "Disable shortcut of completion source in menu.",
	   |       "default": false
	   |     },
	   |     "suggest.snippetIndicator": {
	   |       "type": "string",
	   |       "default": "~",
	   |       "description": "The character used in abbr of complete item to indicate the item could be expand as snippet."
	   |     },
	   |     "suggest.maxCompleteItemCount": {
	   |       "type": "number",
	   |       "default": 50,
	   |       "description": "Maximum number of complete items shown in vim"
	   |     },
	   |     "suggest.preferCompleteThanJumpPlaceholder": {
	   |       "type": "boolean",
	   |       "description": "Confirm completion instead of jump to next placeholder when completion is activated.",
	   |       "default": false
	   |     },
	   |     "suggest.fixInsertedWord": {
	   |       "type": "boolean",
	   |       "description": "Make inserted word replace word characters after cursor position.",
	   |       "default": true
	   |     },
	   |     "suggest.localityBonus": {
	   |       "type": "boolean",
	   |       "description": "Boost suggestions that appear closer to the cursor position.",
	   |       "default": true
	   |     },
	   |     "suggest.triggerAfterInsertEnter": {
	   |       "type": "boolean",
	   |       "description": "Trigger completion after InsertEnter, auto trigger should be 'always' to enable this option",
	   |       "default": false
	   |     },
	   |     "suggest.timeout": {
	   |       "type": "integer",
	   |       "default": 5000,
	   |       "minimum": 500,
	   |       "maximum": 15000,
	   |       "description": "Timeout for completion, in miliseconds."
	   |     },
	   |     "suggest.minTriggerInputLength": {
	   |       "type": "number",
	   |       "default": 1,
	   |       "description": "Mininal input length for trigger completion, default 1"
	   |     },
	   |     "suggest.triggerCompletionWait": {
	   |       "type": "integer",
	   |       "default": 100,
	   |       "minimum": 30,
	   |       "maximum": 500,
	   |       "description": "Wait time between text change and completion start, cancel completion when text changed during wait."
	   |     },
	   |     "suggest.echodocSupport": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "When enabled, add function signature to user_data.signature to support echodoc.vim"
	   |     },
	   |     "suggest.acceptSuggestionOnCommitCharacter": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "Controls whether suggestions should be accepted on commit characters. For example, in JavaScript, the semi-colon (`;`) can be a commit character that accepts a suggestion and types that character. Requires CompleteChanged event to work."
	   |     },
	   |     "suggest.noselect": {
	   |       "type": "boolean",
	   |       "description": "Not make vim select first item on completion start",
	   |       "default": true
	   |     },
	   |     "suggest.keepCompleteopt": {
	   |       "type": "boolean",
	   |       "description": "When enabled, completeopt is not overriden, auto completion will be disabled if completeopt doesn't have noinsert and noselect.",
	   |       "default": false
	   |     },
	   |     "suggest.lowPrioritySourceLimit": {
	   |       "type": "integer",
	   |       "minimum": 1,
	   |       "maximum": 100,
	   |       "description": "Max items count for source priority lower than 90."
	   |     },
	   |     "suggest.highPrioritySourceLimit": {
	   |       "type": "integer",
	   |       "minimum": 1,
	   |       "maximum": 100,
	   |       "description": "Max items count for source priority bigger than or equal to 90."
	   |     },
	   |     "suggest.removeDuplicateItems": {
	   |       "type": "boolean",
	   |       "description": "Remove completion items with duplicated word for all sources, snippet items are excluded.",
	   |       "default": false
	   |     },
	   |     "suggest.defaultSortMethod": {
	   |       "type": "string",
	   |       "description": "Default sorting behavior for suggested completion items.",
	   |       "default": "length",
	   |       "enum": ["length", "alphabetical", "none"]
	   |     },
	   |     "suggest.completionItemKindLabels": {
	   |       "type": "object",
	   |       "default": {},
	   |       "description": "Set custom labels to completion items' kinds.",
	   |       "properties": {
	   |         "text": { "type": "string" },
	   |         "method": { "type": "string" },
	   |         "function": { "type": "string" },
	   |         "constructor": { "type": "string" },
	   |         "field": { "type": "string" },
	   |         "variable": { "type": "string" },
	   |         "class": { "type": "string" },
	   |         "interface": { "type": "string" },
	   |         "module": { "type": "string" },
	   |         "property": { "type": "string" },
	   |         "unit": { "type": "string" },
	   |         "value": { "type": "string" },
	   |         "enum": { "type": "string" },
	   |         "keyword": { "type": "string" },
	   |         "snippet": { "type": "string" },
	   |         "color": { "type": "string" },
	   |         "file": { "type": "string" },
	   |         "reference": { "type": "string" },
	   |         "folder": { "type": "string" },
	   |         "enumMember": { "type": "string" },
	   |         "constant": { "type": "string" },
	   |         "struct": { "type": "string" },
	   |         "event": { "type": "string" },
	   |         "operator": { "type": "string" },
	   |         "typeParameter": { "type": "string" },
	   |         "default": { "type": "string" }
	   |       },
	   |       "additionalProperties": false
	   |     },
	   |     "suggest.invalidInsertCharacters": {
	   |       "type": "array",
	   |       "items": {
	   |         "type": "string"
	   |       },
	   |       "description": "Invalid character for strip valid word when inserting text of complete item.",
	   |       "default": [" ", "(", "<", "{", "[", "\r", "\n"]
	   |     },
	   |     "suggest.asciiCharactersOnly": {
	   |       "type": "boolean",
	   |       "description": "Suggest ASCII characters only",
	   |       "default": false
	   |     },
	   |     "diagnostic.enable": {
	   |       "type": "boolean",
	   |       "description": "Set to false to disable diagnostic display",
	   |       "default": true
	   |     },
	   |     "diagnostic.level": {
	   |       "type": "string",
	   |       "description": "Used for filter diagnostics by diagnostic severity.",
	   |       "default": "hint",
	   |       "enum": ["hint", "information", "warning", "error"]
	   |     },
	   |     "diagnostic.locationlistUpdate": {
	   |       "type": "boolean",
	   |       "description": "Update locationlist on diagnostics change, only works with locationlist opened by :CocDiagnostics command and first window of associated buffer.",
	   |       "default": true
	   |     },
	   |     "diagnostic.checkCurrentLine": {
	   |       "type": "boolean",
	   |       "description": "When enabled, show all diagnostics of current line if there are none at the current position.",
	   |       "default": false
	   |     },
	   |     "diagnostic.messageTarget": {
	   |       "type": "string",
	   |       "description": "Diagnostic message target.",
	   |       "default": "float",
	   |       "enum": ["echo", "float"]
	   |     },
	   |     "diagnostic.messageDelay": {
	   |       "type": "number",
	   |       "description": "How long to wait (in milliseconds) before displaying the diagnostic message with echo or float",
	   |       "default": 200
	   |     },
	   |     "diagnostic.refreshOnInsertMode": {
	   |       "type": "boolean",
	   |       "description": "Enable diagnostic refresh on insert mode, default false.",
	   |       "default": false
	   |     },
	   |     "diagnostic.displayByAle": {
	   |       "type": "boolean",
	   |       "description": "Use Ale for display diagnostics in vim, will disable coc for display diagnostics, restart required on change.",
	   |       "default": false
	   |     },
	   |     "diagnostic.virtualText": {
	   |       "type": "boolean",
	   |       "description": "Use NeoVim virtual text to display diagnostics",
	   |       "default": false
	   |     },
	   |     "diagnostic.virtualTextCurrentLineOnly": {
	   |       "type": "boolean",
	   |       "description": "Only show virtualText diagnostic on current cursor line",
	   |       "default": true
	   |     },
	   |     "diagnostic.virtualTextPrefix": {
	   |       "type": "string",
	   |       "description": "The prefix added virtual text diagnostics",
	   |       "default": " "
	   |     },
	   |     "diagnostic.virtualTextLines": {
	   |       "type": "number",
	   |       "description": "The number of non empty lines from a diagnostic to display",
	   |       "default": 3
	   |     },
	   |     "diagnostic.virtualTextLineSeparator": {
	   |       "type": "string",
	   |       "description": "The text that will mark a line end from the diagnostic message",
	   |       "default": " \\ "
	   |     },
	   |     "diagnostic.enableSign": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Enable signs for diagnostics."
	   |     },
	   |     "diagnostic.enableHighlightLineNumber": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Enable highlighting line numbers for diagnostics, only works with neovim and diagnostic.enableSign is true."
	   |     },
	   |     "diagnostic.enableMessage": {
	   |       "type": "string",
	   |       "default": "always",
	   |       "description": "When to enable show messages of diagnostics.",
	   |       "enum": ["always", "jump", "never"]
	   |     },
	   |     "diagnostic.highlightOffset": {
	   |       "type": "number",
	   |       "description": "Offset number of buffer.addHighlight, neovim only.",
	   |       "default": 1000
	   |     },
	   |     "diagnostic.signPriority": {
	   |       "type": "number",
	   |       "description": "Priority of diagnostic signs, default to 10",
	   |       "default": 10
	   |     },
	   |     "diagnostic.errorSign": {
	   |       "type": "string",
	   |       "description": "Text of error sign",
	   |       "default": ">>"
	   |     },
	   |     "diagnostic.warningSign": {
	   |       "type": "string",
	   |       "description": "Text of warning sign",
	   |       "default": "⚠"
	   |     },
	   |     "diagnostic.infoSign": {
	   |       "type": "string",
	   |       "description": "Text of info sign",
	   |       "default": ">>"
	   |     },
	   |     "diagnostic.hintSign": {
	   |       "type": "string",
	   |       "description": "Text of hint sign",
	   |       "default": ">>"
	   |     },
	   |     "diagnostic.maxWindowHeight": {
	   |       "type": "number",
	   |       "description": "Maximum height of diagnostics floating window.",
	   |       "default": 8
	   |     },
	   |     "diagnostic.maxWindowWidth": {
	   |       "type": "number",
	   |       "description": "Maximum width of diagnostics floating window.",
	   |       "default": 80
	   |     },
	   |     "diagnostic.filetypeMap": {
	   |       "type": "object",
	   |       "description": "A map between buffer filetype and the filetype assigned to diagnostics. To syntax highlight diagnostics withs their parent buffer type use `\"default\": \"bufferType\"`",
	   |       "default": {}
	   |     },
	   |     "diagnostic.format": {
	   |       "type": "string",
	   |       "description": "Define the diagnostic format that shown in float window or echoed, available parts: source, code, severity, message",
	   |       "default": "[%source%code] [%severity] %message"
	   |     },
	   |     "diagnostic.separateRelatedInformationAsDiagnostics": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "Separate related information as diagnostics"
	   |     },
	   |     "diagnostic.showUnused": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Show unused variables"
	   |     },
	   |     "diagnostic.showDeprecated": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Show deprecated variables"
	   |     },
	   |     "signature.enable": {
	   |       "type": "boolean",
	   |       "description": "Enable signature help when trigger character typed, require restart service on change.",
	   |       "default": true
	   |     },
	   |     "signature.triggerSignatureWait": {
	   |       "type": "integer",
	   |       "default": 500,
	   |       "minimum": 200,
	   |       "maximum": 1000,
	   |       "description": "Timeout for trigger signature help, in miliseconds."
	   |     },
	   |     "signature.target": {
	   |       "type": "string",
	   |       "description": "Target of signature help, use float when possible by default.",
	   |       "default": "float",
	   |       "enum": ["float", "echo"]
	   |     },
	   |     "signature.maxWindowWidth": {
	   |       "type": "integer",
	   |       "default": 80,
	   |       "description": "Maximum width of signature float window (or popup on vim8)."
	   |     },
	   |     "signature.maxWindowHeight": {
	   |       "type": "number",
	   |       "description": "Maximum height of signature float window (or popup on vim8).",
	   |       "minimum": 3,
	   |       "default": 8
	   |     },
	   |     "signature.preferShownAbove": {
	   |       "type": "boolean",
	   |       "description": "Show signature help float window above cursor when possible, require restart service on change.",
	   |       "default": true
	   |     },
	   |     "signature.hideOnTextChange": {
	   |       "type": "boolean",
	   |       "description": "Hide signature float window when text changed on insert mode.",
	   |       "default": false
	   |     },
	   |     "codeLens.enable": {
	   |       "type": "boolean",
	   |       "description": "Enable codeLens feature, require neovim with set virtual text feature.",
	   |       "default": false
	   |     },
	   |     "codeLens.separator": {
	   |       "type": "string",
	   |       "description": "Separator text for codeLens in virtual text",
	   |       "default": "‣"
	   |     },
	   |     "codeLens.subseparator": {
	   |       "type": "string",
	   |       "description": "Subseparator between codeLenses in virtual text",
	   |       "default": " "
	   |     },
	   |     "refactor.openCommand": {
	   |       "type": "string",
	   |       "description": "Open command for refactor window.",
	   |       "default": "vsplit"
	   |     },
	   |     "refactor.saveToFile": {
	   |       "type": "boolean",
	   |       "description": "Save to file when write refactor buffer with ':noa wa' command, set to false if you want save buffer by yourself.",
	   |       "default": true
	   |     },
	   |     "refactor.beforeContext": {
	   |       "type": "number",
	   |       "default": 3,
	   |       "description": "Print num lines of leading context before each match."
	   |     },
	   |     "refactor.afterContext": {
	   |       "type": "number",
	   |       "default": 3,
	   |       "description": "Print num lines of trailing context after each match."
	   |     },
	   |     "dialog.maxHeight": {
	   |       "type": "number",
	   |       "default": 20,
	   |       "description": "Maximum height of dialog window."
	   |     },
	   |     "dialog.maxWidth": {
	   |       "type": "number",
	   |       "default": 80,
	   |       "description": "Maximum width of dialog window."
	   |     },
	   |     "dialog.confirmKey": {
	   |       "type": "string",
	   |       "default": "<cr>",
	   |       "description": "Confirm key for confirm selection used by menu and picker, you can always use <esc> to cancel."
	   |     },
	   |     "dialog.pickerButtons": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Show buttons for picker dialog window/popup."
	   |     },
	   |     "dialog.pickerButtonShortcut": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Show shortcut in buttons of picker dialog window/popup, used when dialog.pickerButtons is true."
	   |     },
	   |     "dialog.floatHighlight": {
	   |       "type": ["string", "null"],
	   |       "default": null,
	   |       "description": "Highlight group for dialog window/popup, default to 'CocFloating'"
	   |     },
	   |     "dialog.floatBorderHighlight": {
	   |       "type": ["string", "null"],
	   |       "default": null,
	   |       "description": "Highlight group for border of dialog window/popup, default to 'CocFloating'"
	   |     },
	   |     "notification.marginTop": {
	   |       "type": "number",
	   |       "default": 1,
	   |       "description": "Margin top for notification dialog."
	   |     },
	   |     "notification.marginRight": {
	   |       "type": "number",
	   |       "default": 1,
	   |       "description": "Margin right for notification dialog."
	   |     },
	   |     "notification.maxWidth": {
	   |       "type": "number",
	   |       "default": 60,
	   |       "description": "Maximum content width of notification dialog."
	   |     },
	   |     "notification.maxHeight": {
	   |       "type": "number",
	   |       "default": 10,
	   |       "description": "Maximum content height of notification dialog."
	   |     },
	   |     "notification.highlightGroup": {
	   |       "type": "string",
	   |       "default": "CocFloating",
	   |       "description": "Highlight group of notification dialog."
	   |     },
	   |     "notification.minProgressWidth": {
	   |       "type": "number",
	   |       "default": 30,
	   |       "description": "Minimum width of progress notification."
	   |     },
	   |     "workspace.ignoredFiletypes": {
	   |       "type": "array",
	   |       "default": ["markdown", "log", "txt", "help"],
	   |       "description": "Filetypes that should be ignored for resolve workspace folder.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "workspace.bottomUpFiletypes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Filetypes that should have workspace folder should resolved from base directory of file.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "workspace.workspaceFolderCheckCwd": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Whether the cwd directory should be checked first when resolving workspace folder."
	   |     },
	   |     "list.indicator": {
	   |       "type": "string",
	   |       "default": ">",
	   |       "description": "The character used as first character in prompt line"
	   |     },
	   |     "list.alignColumns": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "Whether to align lists in columns, default: `false`"
	   |     },
	   |     "list.interactiveDebounceTime": {
	   |       "type": "number",
	   |       "default": 100,
	   |       "description": "Debouce time for input change on interactive mode."
	   |     },
	   |     "list.height": {
	   |       "type": "number",
	   |       "default": 10,
	   |       "description": "Height of split list window."
	   |     },
	   |     "list.statusLineSegments": {
	   |       "type": ["array", "null"],
	   |       "default": [
	   |         "%#CocListMode#-- %{get(b:list_status, \"mode\", \"\")} --%*",
	   |         "%{get(b:list_status, \"loading\", \"\")}",
	   |         "%{get(b:list_status, \"args\", \"\")}",
	   |         "(%L/%{get(b:list_status, \"total\", \"\")})",
	   |         "%=",
	   |         "%#CocListPath# %{get(b:list_status, \"cwd\", \"\")} %l/%L%*"
	   |       ],
	   |       "items": {
	   |         "types": "string"
	   |       },
	   |       "description": "An array of statusline segments that will be used to draw the status line for list windows."
	   |     },
	   |     "list.signOffset": {
	   |       "type": "number",
	   |       "default": 900,
	   |       "description": "Sign offset of list, should be different from other plugins."
	   |     },
	   |     "list.selectedSignText": {
	   |       "type": "string",
	   |       "default": "*",
	   |       "description": "Sign text for selected lines."
	   |     },
	   |     "list.extendedSearchMode": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Enable extended search mode which allows multiple search patterns delimited by spaces."
	   |     },
	   |     "list.limitLines": {
	   |       "type": "number",
	   |       "default": 30000,
	   |       "description": "Limit lines for list buffer."
	   |     },
	   |     "list.maxPreviewHeight": {
	   |       "type": "number",
	   |       "default": 12,
	   |       "description": "Max height for preview window of list."
	   |     },
	   |     "list.previewSplitRight": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "Use vsplit for preview window."
	   |     },
	   |     "list.matchHighlightGroup": {
	   |       "type": "string",
	   |       "default": "Search",
	   |       "description": "Highlight group used for matched texts in list window."
	   |     },
	   |     "list.previewHighlightGroup": {
	   |       "type": "string",
	   |       "default": "Search",
	   |       "description": "Highlight group used for highlight the range in preview window."
	   |     },
	   |     "list.nextKeymap": {
	   |       "type": "string",
	   |       "default": "<C-j>",
	   |       "description": "Key used for select next line on insert mode."
	   |     },
	   |     "list.previousKeymap": {
	   |       "type": "string",
	   |       "default": "<C-k>",
	   |       "description": "Key used for select previous line on insert mode."
	   |     },
	   |     "list.normalMappings": {
	   |       "type": "object",
	   |       "default": {},
	   |       "description": "Custom keymappings on normal mode."
	   |     },
	   |     "list.insertMappings": {
	   |       "type": "object",
	   |       "default": {},
	   |       "description": "Custom keymappings on insert mode."
	   |     },
	   |     "list.source.diagnostics.includeCode": {
	   |       "type": "boolean",
	   |       "description": "Whether to show the diagnostic code in the list.",
	   |       "default": true
	   |     },
	   |     "list.source.diagnostics.pathFormat": {
	   |       "type": "string",
	   |       "description": "Decide how the filepath is shown in the list.",
	   |       "enum": ["full", "short", "filename", "hidden"],
	   |       "default": "full"
	   |     },
	   |     "list.source.symbols.excludes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Patterns of minimatch for filepath to execlude from symbols list.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "list.source.outline.ctagsFilestypes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Filetypes that should use ctags for outline instead of language server.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "cursors.cancelKey": {
	   |       "type": "string",
	   |       "default": "<esc>",
	   |       "description": "Key used for cancel cursors session."
	   |     },
	   |     "cursors.nextKey": {
	   |       "type": "string",
	   |       "default": "<C-n>",
	   |       "description": "Key used for jump to next cursors position. "
	   |     },
	   |     "cursors.previousKey": {
	   |       "type": "string",
	   |       "default": "<C-p>",
	   |       "description": "Key used for jump to previous cursors position."
	   |     },
	   |     "coc.preferences.enableMessageDialog": {
	   |       "type": "boolean",
	   |       "default": false,
	   |       "description": "Enable messages shown in notification dialog."
	   |     },
	   |     "coc.preferences.maxFileSize": {
	   |       "type": "string",
	   |       "default": "10MB",
	   |       "description": "Maximum file size in bytes that coc.nvim should handle, default '10MB'"
	   |     },
	   |     "coc.preferences.promptWorkspaceEdit": {
	   |       "type": "boolean",
	   |       "description": "Prompt confirm from user when apply workspace edit for unloaded files.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.listOfWorkspaceEdit": {
	   |       "type": "string",
	   |       "default": "quickfix",
	   |       "description": "List should contains changed locations after workspace edit, default to vim's quickfix",
	   |       "enum": ["quickfix", "location", "none"]
	   |     },
	   |     "coc.preferences.useQuickfixForLocations": {
	   |       "type": "boolean",
	   |       "description": "Use vim's quickfix list for jump locations,\n need restart on change.",
	   |       "default": false
	   |     },
	   |     "coc.preferences.extensionUpdateCheck": {
	   |       "type": "string",
	   |       "default": "never",
	   |       "description": "Interval for check extension update, could be daily, weekly, never",
	   |       "enum": ["daily", "weekly", "never"]
	   |     },
	   |     "coc.preferences.snippetStatusText": {
	   |       "type": "string",
	   |       "default": "SNIP",
	   |       "description": "Text shown in statusline to indicate snippet session is activated."
	   |     },
	   |     "coc.preferences.hoverTarget": {
	   |       "type": "string",
	   |       "description": "Target to show hover information, default is floating window when possible.",
	   |       "enum": ["preview", "echo", "float"]
	   |     },
	   |     "coc.preferences.colorSupport": {
	   |       "type": "boolean",
	   |       "description": "Enable color highlight if language server support it.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.previewAutoClose": {
	   |       "type": "boolean",
	   |       "description": "Auto close preview window on cursor move.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.previewMaxHeight": {
	   |       "type": "number",
	   |       "default": 12,
	   |       "description": "Max height of preview window for hover."
	   |     },
	   |     "coc.preferences.currentFunctionSymbolAutoUpdate": {
	   |       "type": "boolean",
	   |       "description": "Automatically update the value of b:coc_current_function on CursorHold event",
	   |       "default": false
	   |     },
	   |     "coc.preferences.formatOnSaveFiletypes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Filetypes that should run format on save.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.preferences.enableFloatHighlight": {
	   |       "type": "boolean",
	   |       "description": "Enable highlight for floating window.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.rootPatterns": {
	   |       "type": "array",
	   |       "default": [".git", ".hg", ".projections.json"],
	   |       "description": "Root patterns to resolve workspaceFolder from parent folders of opened files, resolved from up to down.",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.preferences.watchmanPath": {
	   |       "type": "string",
	   |       "description": "executable path for https://facebook.github.io/watchman/, detected from $PATH by default",
	   |       "default": null
	   |     },
	   |     "coc.preferences.jumpCommand": {
	   |       "type": "string",
	   |       "description": "Command used for location jump, like goto definition, goto references etc.",
	   |       "enum": ["edit", "split", "vsplit", "tabe", "drop", "tab drop", "pedit"],
	   |       "default": "edit"
	   |     },
	   |     "coc.preferences.messageLevel": {
	   |       "type": "string",
	   |       "description": "Message level for filter echoed messages, could be 'more', 'warning' and 'error'",
	   |       "default": "more",
	   |       "enum": ["more", "warning", "error"]
	   |     },
	   |     "coc.preferences.bracketEnterImprove": {
	   |       "type": "boolean",
	   |       "description": "Improve enter inside bracket `<> {} [] ()` by add new empty line below and place cursor to it. Works with `coc#on_enter()`",
	   |       "default": true
	   |     },
	   |     "coc.preferences.formatOnType": {
	   |       "type": "boolean",
	   |       "description": "Set to true to enable format on type",
	   |       "default": false
	   |     },
	   |     "coc.preferences.formatOnTypeFiletypes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Filetypes that should run format on typing. Only take effect when `coc.preferences.formatOnType` set `true`",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.preferences.highlightTimeout": {
	   |       "type": "integer",
	   |       "default": 500,
	   |       "minimum": 200,
	   |       "maximum": 5000,
	   |       "description": "Highlight timeout for buffer in floating window."
	   |     },
	   |     "coc.preferences.snippets.enable": {
	   |       "type": "boolean",
	   |       "description": "Set to false to disable snippets support.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.floatActions": {
	   |       "type": "boolean",
	   |       "description": "Set to false to disable float/popup support for actions menu, won't work on vim without float or popup window support.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.promptInput": {
	   |       "type": "boolean",
	   |       "description": "Use prompt buffer in float window for user input.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.enableMarkdown": {
	   |       "type": "boolean",
	   |       "description": "Tell the language server that markdown text format is supported, note that markdown text may not rendered as expected.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.silentAutoupdate": {
	   |       "type": "boolean",
	   |       "description": "Not open split window with update status when performing auto update.",
	   |       "default": true
	   |     },
	   |     "coc.preferences.willSaveHandlerTimeout": {
	   |       "type": "integer",
	   |       "default": 500,
	   |       "minimum": 200,
	   |       "maximum": 5000,
	   |       "description": "Will save handler timeout"
	   |     },
	   |     "coc.source.around.enable": {
	   |       "type": "boolean",
	   |       "default": true
	   |     },
	   |     "coc.source.around.firstMatch": {
	   |       "type": "boolean",
	   |       "description": "Filter complete items by first letter strict match.",
	   |       "default": true
	   |     },
	   |     "coc.source.around.shortcut": {
	   |       "type": "string",
	   |       "default": "A"
	   |     },
	   |     "coc.source.around.priority": {
	   |       "type": "integer",
	   |       "default": 1
	   |     },
	   |     "coc.source.around.disableSyntaxes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.source.buffer.enable": {
	   |       "type": "boolean",
	   |       "default": true
	   |     },
	   |     "coc.source.buffer.shortcut": {
	   |       "type": "string",
	   |       "default": "B"
	   |     },
	   |     "coc.source.buffer.priority": {
	   |       "type": "integer",
	   |       "default": 1
	   |     },
	   |     "coc.source.buffer.firstMatch": {
	   |       "type": "boolean",
	   |       "description": "Filter complete items by first letter strict match.",
	   |       "default": true
	   |     },
	   |     "coc.source.buffer.ignoreGitignore": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Ignore git ignored files for buffer words"
	   |     },
	   |     "coc.source.buffer.disableSyntaxes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.source.file.enable": {
	   |       "type": "boolean",
	   |       "default": true
	   |     },
	   |     "coc.source.file.shortcut": {
	   |       "type": "string",
	   |       "default": "F"
	   |     },
	   |     "coc.source.file.priority": {
	   |       "type": "integer",
	   |       "default": 10
	   |     },
	   |     "coc.source.file.disableSyntaxes": {
	   |       "type": "array",
	   |       "default": [],
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.source.file.triggerCharacters": {
	   |       "type": "array",
	   |       "default": ["/"],
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.source.file.trimSameExts": {
	   |       "type": "array",
	   |       "default": [".ts", ".js"],
	   |       "description": "Trim same extension on file completion",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "coc.source.file.ignoreHidden": {
	   |       "type": "boolean",
	   |       "default": true,
	   |       "description": "Ignore completion for hidden files"
	   |     },
	   |     "coc.source.file.ignorePatterns": {
	   |       "type": "array",
	   |       "default": [],
	   |       "description": "Ignore patterns of matcher",
	   |       "items": {
	   |         "type": "string"
	   |       }
	   |     },
	   |     "languageserver": {
	   |       "type": "object",
	   |       "default": {},
	   |       "description": "Dictionary of languageservers, key is used as id of languageserver.",
	   |       "patternProperties": {
	   |         "^[_a-zA-Z]+$": {
	   |           "oneOf": [
	   |             {
	   |               "$ref": "#/definitions/languageServerModule"
	   |             },
	   |             {
	   |               "$ref": "#/definitions/languageServerCommand"
	   |             },
	   |             {
	   |               "$ref": "#/definitions/languageServerSocket"
	   |             }
	   |           ]
	   |         }
	   |       }
	   |     }
	   |   }
	   | }
	  
		- suggest.noselect:true,
suggest.enablePreseect:false
自动补全不默认选中，直接回车，直接下一行
如果按tab就自动选中第一行，再回车，会展开那个补全的提示。

	- [neovim安装coc缺失bash-language-server](https://blog.csdn.net/u013297137/article/details/103507199)

- 多选多行进行选择

	- 1.c-v,上下选中多行选中visualblock模式
2.shfit+i,输入注释符号
3.esc退出visualblock模式

- easyalign

	- ga=,用＝对齐

- autoformat

	- \f执行自动格式化
	- AutoformatLine

- To make prettier do the format, use command :CocCommand prettier.formatFile
To save without formatting, use :noa w
- *#
- %

	- 使用 % 在匹配的括号之间跳转

- /?

	- 使用 / 和 ? 来快速正向和反向搜索等

- <leader>s

	- nmap <leader>s <Plug>(easymotion-s2)

- [vim中输入方向键 转化为 A B C D](https://blog.csdn.net/stpeace/article/details/49407857)

- [解决wsl中安装好了xclip也无法访问系统剪切板的问题](https://qastack.cn/vi/12376/vim-on-wsl-synchronize-system-clipboard-set-clipboard-unnamed)

	- if system('uname -r') =~ "Microsoft"
  augroup Yank
    autocmd!
    autocmd TextYankPost * :call system('clip.exe ',@")
  augroup END
endif

### ranger

- shfit-v:创建文件
- shfit-m:创建文件夹
- cw：重命名文件名，包括后缀

### [fzf](https://zhuanlan.zhihu.com/p/91873965)

- fzf安装方法和问题集合

	- fzf相关地址

		- https://github.com/junegunn/fzf#installation

- c-t
- c-r
- c-j/c-k/c-n/c-m光标移动
- enter用来选中
- -m，tab和shfit-tab用来多选
- 可扩展搜索

  fzf默认会以“extened-search"模式启动， 这种模式下你可以输入多个以空格分隔的搜索关键词， 如^music .mp3$, sbtrkt !fire.
  
  如果你不想用fuzzy match， 可以用fzf -e做精确匹配 符号"|"可以做or匹配， 比如
  
   # 表示以core开头，以go或rb或py结尾的
   ^core go$|rb$|py$
  
### [lazygit](https://github.com/jesseduffield/lazygit/blob/master/docs/keybindings/Keybindings_en.md)

- file面板

	- a：all files stage/unstage
	- space: one single file stage
	- enter: enter into one line stage mode
	- 如果只想stage一个文件的一部分：
先enter，进入界面，
按空格一行一行的stage，
可以按a，选中所有hook，然后按空格，直接hook添加例如
按tab切换unstage面板还是stage面板，
在unstage面板中在某一行上按d，然后回车，就直接删除了，不可逆。
	- c:commit
	- A：amend last commit
	- C:编辑消息
	- d：放弃一个更改
D:快速清理工作目录

- branch面板

	- 默认显示本地分支
	- n（现在设为i）：添加分支
	- 空格：选中分支
	- P：发布分支到远程
	- s：隐藏文件
	- M：merge合并分支：先切换到我想合并到的分支，然后移动到新提交的分支，按大写M

- commit提交面板

	- enter：查看本次提交中改动的文件

		- d：删除本次提交中此文件的修改
		- c:回滚，帮你添加一个更改，把文件回到这次提交的版本

	- ,.：翻页
<>：最上最下
	- /：搜索
	- r: 更改提交信息
R：在编辑器中更改提交信息
	- 滚回：选中一次提交，按空格，就可以checkout到这个提交了，到了一个假分支，可以新增分支
	- reflog上选中一个，按小写g，reset
	- g：显示重置选项
soft：选择的那次commit之前的所有提交都会从历史消失，但是更改的文件，恢复到了工作目录，编程没有提交的更改。
hard：选择的那次commit之前的所有提交都会从历史消失，文件也不存在了
mixed：
	- 复制提交：commit面板c：cherry-pick复制commit，回到想复制到的分支，commit面板中按v粘贴commit
	- 删除一次提交：在一个提交上按d，删除提交
	- interactive rebase

- stash 隐藏面板

	- g：pop一次stash，隐藏恢复出来并把这次隐藏删除
	- 空格：直接应用这次隐藏，apply
	- d:直接删除这次隐藏drop

- x: 查看帮助
- []切换面板
- s隐藏提交
- m移动提交到新的分支上
- r更改提交信息
- R在编辑器中编辑
- e编辑commit
f，s，d，p，修改状态
m，continue

- 冲突

	- b两个版本

- delta pager

	- delta --dark --paging=never --24-bit-color=never --theme="OneHalfDark"

- [主题颜色配置](https://github.com/969191832/lazygit/blob/master/docs/Config.md)

- cherry-pick使用教程

	- 1.c
2.换分支
3.v

### less编辑器

less 是linux快速浏览文件的命令(防止 误修改文件) 

less主要就是 浏览文件 查找文件 浏览文件涉及到的就是上下翻页 具体翻页的按键如下表

less | 向上翻页 | 向下翻页
一页 | b (back) | 空格
半页 | u (undo) | d (down)
一行 | y (...) | 回车

