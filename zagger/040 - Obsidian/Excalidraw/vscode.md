---
created: 2023-11-15T20:52
updated: 2023-11-15T20:52
---
# vscode

## 插件

### Vue VSCode Snippets

- [地址](https://juejin.cn/post/6965382258341445646)

## 备份macos setting配置的json

{
    "files.associations": {
        "*.vue": "vue",
        "*.wpy": "vue",
        "*.wxml": "html",
        "*.wxss": "css",
        "*.cjson": "jsonc",
        "*.wxs": "javascript",
        "*.ejs": "html"
    },
    "sync.gist": "3020f683c1170760f6e00b3237969bb1",
    "editor.minimap.maxColumn": 100,
    "workbench.tree.indent": 14,
    "sync.autoDownload": true,
    "sync.autoUpload": true,
    "git.autofetch": true,
    "emmet.triggerExpansionOnTab": true,
    "emmet.showAbbreviationSuggestions": true,
    "emmet.showExpandedAbbreviation": "always",
    "emmet.includeLanguages": {
        "vue-html": "html",
        "vue": "html",
        "wpy": "html",
        "wxml": "html"
    },
    "search.followSymlinks": false,
    "editor.tabCompletion": "on",
    // "editor.codeActionsOnSave": { "source.organizeImports": true },
    // 在使用搜索功能时，将这些文件夹/文件排除在外
    "search.exclude": {
        "**/node_modules": true,
        "**/bower_components": true,
        "**/target": true,
        "**/logs": true,
        "**/.data": true,
        "**/.history": true,
        "**/.vscode": true,
        "**/.idea": true,
        "**/built": true,
        "**/bootstrap": true,
        "**/libs": true,
        "**/locale": true,
        "**/plugin": true
    },
    // 这些文件将不会显示在工作空间中
    "files.exclude": {
        "**/.git": true,
        "**/.svn": true,
        "**/.hg": true,
        "**/CVS": true,
        "**/.DS_Store": true,
        "**/*.js": {
            "when": "$(basename).ts" //ts编译后生成的js文件将不会显示在工作空中
        }
        // "**/node_modules": true
    },
    // windows 10 wsl GPM config
    "gitProjectManager.baseProjectsFolders": [
        "D:/work/ngconsole",
        "D:/codes/ngconsole",
        "D:/work/ngconsole_resources",
        "D:/codes/ngconsole_resources",
        "D:/work/region-front",
        "D:/work/edaas-front",
        "D:/work/new-vdi-client",
        "D:/codes/new-vdi-client",
        "D:/work/oefe-docs",
        "D:/work/idv-client",
        "D:/work/oe-dms",
        "D:/Github/face-api-demo",
        "D:/Github/demo",
        "D:/Github/sequelize-test/koa2-weibo-code",
        "D:/Github/webbo_server",
        "D:/Github/todolist-tool",
        "D:/Github/sina",
        "D:/my-dropbox/Dropbox",
        "D:/work/pmv5-fe",
    ],
    "gitProjectManager.storeRepositoriesBetweenSessions": true,
    "gitProjectManager.ignoredFolders": [
        "node_modules"
    ],
    "gitProjectManager.maxDepthRecursion": 4,
    "gitProjectManager.checkRemoteOrigin": false,
    // spell userWords
    "cSpell.userWords": [
        "MVVM",
        "edaas",
        "ngconsole",
        "todolist",
        "viewmodel",
        "zagger"
    ],
    "editor.renderWhitespace": "all",
    /* // 配置 plantuml 插件
    "plantuml.diagramsRoot": "docs/diagrams/src",
    "plantuml.exportOutDir": "docs/diagrams/out",
    "plantuml.exportFormat": "png",
    "plantuml.exportSubFolder": false,
    "plantuml.includepaths": [
        //   "docs/diagrams/style",
        // "docs/diagrams/src",
        // "/data/codes/lib/plantuml/docs/diagrams/style",
        "D:/360MoveData/Users/zagger/Downloads/C4-PlantUML-master/C4-PlantUML-master"
    ],
    "plantuml.server": "http://172.16.91.1:8002", */
    "editor.fontFamily": "Hack",
    "editor.fontSize": 15,
    /* // rest-client
    "rest-client.environmentVariables": {
        "$shared": {},
        "local": {
            "host": "http://localhost:8080",
            "token": "test token"
        },
        "prod": {
            "host": "https://172.16.201.188",
            "token": "prod token"
        }
    }, */
    "emmet.syntaxProfiles": {
        "vue-html": "html",
        "vue": "html"
    },
   /*// python
   "python.languageServer": "Pylance",
    "python.pythonPath": "C:\\Users\\zagger\\AppData\\Local\\Microsoft\\WindowsApps\\python.exe", */
    /* // vetur
    // "vetur.format.defaultFormatter.html": "js-beautify-html",
    // "vetur.format.defaultFormatter.js": "prettier",
    // "vetur.format.defaultFormatterOptions": {
    //     "js-beautify-html": {
    //         // #vue组件中html代码格式化样式
    //         "wrap_attributes": "force-aligned", //也可以设置为“auto”，效果会不一样
    //         "wrap_line_length": 200,
    //         "end_with_newline": false,
    //         "semi": false,
    //         "singleQuote": true
    //     },
    //     "prettier": {
    //         "semi": false,
    //         "singleQuote": true
    //     }
    // }, */
    "workbench.colorTheme": "One Dark Pro",
    // md format onsave
    "markdownlint.run": "onSave",
    // "javascript.updateImportsOnFileMove.enabled": "always",
    // "[json]": {
    //     "editor.defaultFormatter": "vscode.json-language-features"
    // },
    // https://github.com/tickmao/vscode-settings
    // 基于Dracula编辑器主题和material-icon-theme的图标主题的个人编辑器定制页面。
    // 字体
    // "editor.fontFamily": "'Fira Code', Source Code Pro, Menlo, Monaco, 'Courier New', monospace",
    // 软件主题配色
    // "workbench.iconTheme": "material-icon-theme", // 图标主题
    // "workbench.colorTheme": "Dracula", // 颜色主题
    // "workbench.colorCustomizations": {
    //     "[Dracula]": {
    //         // 编辑区域背景
    //         "editor.background": "#292D3E",
    //         "editor.foreground": "#c7d4dd",
    //         // 侧边栏
    //         "sideBar.background": "#292D3E",
    //         "sideBar.foreground": "#c7d4dd",
    //         "sideBar.border": "#292D3E",
    //         // 侧边栏列表
    //         "list.inactiveSelectionBackground": "#292D3E",
    //         "list.inactiveSelectionForeground": "#dfdfdf",
    //         "list.hoverBackground": "#292D3E",
    //         "list.hoverForeground": "#dfdfdf",
    //         // peek 窗口
    //         "peekView.border": "#5b99fc9c",
    //         // 顶部 tab 栏
    //         "tab.border": "#292D3E",
    //         "tab.activeBackground": "#292D3E",
    //         "tab.activeForeground": "#c7d4dd",
    //         "tab.inactiveBackground": "#292D3E",
    //         "tab.hoverBackground": "#292D3E",
    //         "tab.unfocusedHoverBackground": "#292D3E",
    //         "tab.hoverBorder": "#5b99fcb9",
    //         "tab.inactiveForeground": "#8e8e8e",
    //         "editorGroupHeader.tabsBackground": "#292D3E",
    //         "editorGroupHeader.tabsBorder":"#292D3E",
    //         "editorGroup.border": "#292D3E",
    //         "contrastBorder":"#292D3E",
    //         // 最左侧工具栏
    //         "activityBar.background": "#292D3E",
    //         "activityBar.foreground": "#c7d4dd",
    //         "activityBar.border": "#292D3E",
    //         // 状态栏
    //         "statusBar.background": "#292D3E",
    //         "statusBar.foreground": "#c7d4dd",
    //         "statusBar.border" : "#292D3E",
    //         // panel 窗口
    //         "panel.background": "#292D3E",
    //         "panel.border":"#292D3E",
    //         // 光标
    //         "editorCursor.foreground": "#84B1ED",
    //         // 当前行
    //         "editor.lineHighlightBackground": "#393C4C",
    //         //缩进参考线
    //         // "editorIndentGuide.activeBackground": "#5b99fc33",
    //         // 行号栏的当前行
    //         "editorLineNumber.activeForeground": "#dabfe0",
    //         // 行号
    //         "editorLineNumber.foreground": "#7e7d7e",
    //         // 标尺
    //         "editorRuler.foreground": "#7c5881",
    //         // 快捷提示窗口
    //         "editorSuggestWidget.highlightForeground": "#84B1ED",
    //         "editorSuggestWidget.selectedBackground": "#333f5c",
    //         // 单击一个词时，其它相同单词
    //         "editor.selectionHighlightBackground": "#70697ec9",
    //         "editor.selectionBackground": "#70697ec9",
    //         "editor.selectionHighlightBorder": "#b5f1a159",
    //         // terminal
    //         "terminalCursor.foreground": "#84B1ED",
    //         "terminal.background": "#292D3E",
    //         // 侧边栏中一块区域的标题
    //         "sideBarSectionHeader.background": "#292D3E",
    //         "sideBarSectionHeader.border": "#292D3E",
    //         // 区域获取焦点时
    //         "focusBorder": "#5b99fc36",
    //         // 标题栏颜色
    //         "titleBar.activeBackground": "#292D3E",
    //         "titleBar.activeForeground":"#c7d4dd",
    //         "titleBar.inactiveBackground": "#292D3E",
    //         "titleBar.inactiveForeground": "#c7d4dd",
    //         //滚动
    //         "scrollbar.shadow": "#292D3E",
    //         "editorOverviewRuler.border":"#292D3E",
    //     }
    // },
    // "autoDayNightThemeSwitcher.autoToggle": true,// If enabled, toggle to day and night theme automatically given the times (default is true)
    // "autoDayNightThemeSwitcher.autoToggleTimeNightBegin": "14:00",// Time when the automatic toggle to the night theme shall be done (if auto-toggle enabled, default is 19:00)
    // "autoDayNightThemeSwitcher.autoToggleTimeNightEnd": "9:00",// Time when the automatic toggle to the day theme shall be done (if auto-toggle enabled, default is 7:00)
    // "autoDayNightThemeSwitcher.dayTheme": "Solarized-light-functional",// Day theme (default is Visual Studio Light)
    // "autoDayNightThemeSwitcher.nightTheme": "Tokyo Night",// Night theme (default is Visual Studio Dark)
    // "autoDayNightThemeSwitcher.dayThemeCustomizations": {}, // Day theme color customizations (default is {})
    // "autoDayNightThemeSwitcher.nightThemeCustomizations": {},// Night theme color customizations (default is {})
    // "autoDayNightThemeSwitcher.toggleDefaultNight": true// If neither day or night theme are the current theme and toggle is triggered, switch to night theme (default is true)
    // "eslint.alwaysShowStatus": true,
    // "eslint.format.enable": true,
    // "eslint.packageManager": "yarn",
    // "eslint.run": "onSave",
    // "eslint.validate": [
    //     "vue",
    //     "javascript",
    //     "javascriptreact"
    // ],
    // "editor.codeActionsOnSave": {
    //     "source.fixAll.eslint": true
    // },
    // "vetur.validation.template": false,
    // "editor.formatOnPaste": true,
    // "editor.formatOnType": true,
    // "editor.formatOnSave": true,
    // "files.eol": "\n",
    // "[json]": {
    //     // 对json文件，使用 JSON语言功能 进行格式化
    //     "editor.defaultFormatter": "vscode.json-language-features"
    // },
    // "[jsonc]": {
    //     "editor.defaultFormatter": "vscode.json-language-features"
    // },
    // /* "[html]": {
    //     // 对html文件，使用 vscode.html-language-features(vscode内置规则) 进行格式化,不要使用 prettier
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // }, */
    // "[javascript]": {
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    // "[css]": {
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    // "[less]": {
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    // "[scss]": {
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    // "[vue]": {
    //     // 可选值： eslint ："dbaeumer.vscode-eslint"  vetur: "octref.vetur"   prettier: "esbenp.prettier-vscode"
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    // "[typescript]": {
    //     // 对ts文件进行格式化时，使用哪一种风格 (此处使用的是vscode中安装的ts插件默认风格进行格式化)
    //     "editor.defaultFormatter": "vscode.typescript-language-features"
    // },
    // "[markdown]": {
    //     "editor.defaultFormatter": "yzhang.markdown-all-in-one"
    // }
}

