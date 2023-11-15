---
created: 2023-11-15T20:49
updated: 2023-11-15T20:49
---
# mockjs

## vue+webpack(vue.config.js)

### const Mock = require("mockjs")
resp.json(Mock.mock(jsonData));

function bindDevServerAfter(app){
    // serve mock data
    app.all("*", function(req, resp, next){
        var pathname = req.path;
        if(pathname.endsWith("/")) {
            pathname = pathname.substring(0, pathname.length - 1);
        }
        var realpathname = path.join(__dirname, "./.data", pathname);
        var dirname = path.dirname(realpathname);
        var filename = path.basename(realpathname) + ".json";
        var localpath = [
            realpathname,
            dirname + "/" + req.method.toLowerCase() + "-" + filename,
            dirname + "/" + filename
        ].filter(function(pathstr){
            return fs.existsSync(pathstr) && fs.lstatSync(pathstr).isFile();
        })[0];
        if(localpath) {
            smartResponse(req, resp, localpath);
        } else {
            next();
        }
    });
}

## 直接引用

Getting Started
nuysoft edited this page on 17 Feb 2016 · 14 revisions
开始 & 安装
Node (CommonJS)
# 安装
npm install mockjs
// 使用 Mock
var Mock = require('mockjs')
var data = Mock.mock({
    // 属性 list 的值是一个数组，其中含有 1 到 10 个元素
    'list|1-10': [{
        // 属性 id 是一个自增数，起始值为 1，每次增 1
        'id|+1': 1
    }]
})
// 输出结果
console.log(JSON.stringify(data, null, 4))
Bower
# 安装
npm install -g bower
bower install --save mockjs
<script type="text/javascript" src="./bower_components/mockjs/dist/mock.js"></script>
RequireJS (AMD)
// 配置 Mock 路径
require.config({
    paths: {
        mock: 'http://mockjs.com/dist/mock'
    }
})
// 加载 Mock
require(['mock'], function(Mock){
    // 使用 Mock
    var data = Mock.mock({
        'list|1-10': [{
            'id|+1': 1
        }]
    })
    // 输出结果
    document.body.innerHTML +=
        '<pre>' +
        JSON.stringify(data, null, 4) +
        '</pre>'
})
// ==>
{
    "list": [
        {
            "id": 1
        },
        {
            "id": 2
        },
        {
            "id": 3
        }
    ]
}
JSFiddle

Sea.js (CMD)
因为 Sea.js 社区尚未提供 webpack 插件，所以 Mock.js 暂不完整支持通过 Sea.js 加载。

一种变通的方式是，依然通过 Sea.js 配置和加载 Mock.js，然后访问全局变量 Mock。

// 配置 Mock 路径
seajs.config({
    alias: {
        mock: 'http://mockjs.com/dist/mock.js'
    }
})

// 加载 Mock
seajs.use('mock', function(__PLACEHOLDER) {
    // 使用 Mock（全局变量）
    var data = Mock.mock({
        'list|1-10': [{
            'id|+1': 1
        }]
    });
    document.body.innerHTML +=
        '<pre>' +
        JSON.stringify(data, null, 4) +
        '</pre>'
})
JSFiddle

Random CLI
# 全局安装
$ npm install mockjs -g

# 执行
$ random url
# => http://rmcpx.org/funzwc

# 帮助
random -h


### [使用方法](https://github.com/nuysoft/Mock/wiki/Getting-Started)

// 引入 Mock
var Mock = require('mockjs')

var random = Mock.Random;

//扩展数据模板
random.extend({
  type: function (index:number) {
    const types = ['products', 'industryApp', 'solution', 'experts'];
    return this.pick(types[index])
  }
});

// 定义数据类型
const  menuSource:Array<any> = [];
 menuSource[0] = Mock.mock({
  "type": "@type(0)",
   'data|3-4':[{
     'id|+1': 1,
     name: "@ctitle( 4,6)",
     "childs|5-10": [{
       'id|+1': 1,
       name: "@ctitle(4,6)",
     }]
   }]
});
// 输出结果
 console.log(data);


## ngconsole实现方式总结


使用到两个插件
hm-middleware
http-proxy-middleware

### hm-middleware

https://www.npmjs.com/package/hm-middleware

http-mock-middleware 是一个 http mock 库，或者说 ajax/websocket mock 库，它接收来自 web 前端页面的 ajax/websocket 请求，将请求映射到本地 mock 文件并经过一系列插件处理后返回给 web 前端页面。http-mock-middleware 内建了多个插件以实现各种各样的功能，比如：根据 query 参数等的不同响应不同的数据，按需将请求转发给后端服务器，延迟响应，设置 cookie，主动向 websocket 客户端发送数据等。
什么是本地 mock 文件？就是用于存放对应请求的假数据文件，比如要将请求 /login 映射为本地假数据文件 .data/login.json，就称 .data/login.json 为 mock 文件。
http-mock-middleware 本身导出为一个兼容 express middleware 的函数，因此你可以很方便的集成到 webpack-dev-server, vue-cli-service, express 等现有服务器中。
https://gitee.com/mirrors/http-mock-middleware
devServer: {
        host: "0.0.0.0",
        disableHostCheck: true,
        before (app) {
            NgconsoleWebpackPlugin.bindDevServerBefore(app);
        },
        after (app, server){
            const middleware = require("hm-middleware");
            app.use(middleware({
                mockRules: {
                    "/": process.env.NGCONSOLE_DATA || ".data"
                },
                proxy: {
                    autoSave: true,
                    saveDirectory: ".data",
                    overrideSameFile: "override"
                }
            }));
        }
    },
￼



### http-proxy-middleware

function proxyMiddleware(options){
    let useProxy = true;
    accessable("http://172.16.203.254/users/sign_in", "http://172.16.203.12/zentao/my/").then(function(){
        useProxy = false;
    }, function(){});
    return function(req, resp, next){
        let proxyHost = req.get("X-Mock-Proxy");
        if(!proxyHost) {
            return next();
        }
        let proxyUri = useProxy ? options.vdiProxy : false;
        let proxyMiddleware = proxyCache[proxyHost];
        if(!proxyMiddleware) {
            proxyMiddleware = proxyCache[proxyHost] = createProxyMiddleware("/", {
                target: `https://${proxyHost}`,
                secure: false,
                changeOrigin: true,
                logLevel: "debug",
                agent: proxyUri ? new ProxyAgent(proxyUri) : undefined
                , onProxyRes: function onProxyRes (proxyRes, req, res) {
                    let original_cookie = proxyRes.headers['set-cookie'];
                    if (!original_cookie) return;
                    let modified_cookie = original_cookie.map(str => {
                        return str.replace(/(;\s*)?SameSite=None/, '')
                                  .replace(/(;\s*)?secure/, '');
                    });
                    if (modified_cookie.every((str, i) => str === original_cookie[i])) return;
                    console.log(original_cookie);
                    console.log(modified_cookie);
                    proxyRes.headers['set-cookie'] = modified_cookie;
                }
            });
        }
        proxyMiddleware(req, resp, next);
    }
}

function accessable(...urls) {
    return Promise.race(urls.map(url => {
        let httplib = url.indexOf("https://") === 0 ? https : http;
        return new Promise(function(resolve, reject) {
            let obj = urllib.parse(url);
            httplib.request({
                method: "GET",
                path: obj.path,
                host: obj.host,
                timeout: 3000
            }, function(){
                resolve();
            }).on("error", reject).end();
        });
    }));
}

## edaas-front实现方式总结

### const Mock = require("mockjs")

### 使用

。。。
devServer: {
        after: bindDevServerAfter
    }
};

function bindDevServerAfter(app){
    // serve mock data
    app.all("*", function(req, resp, next){
        var pathname = req.path;
        if(pathname.endsWith("/")) {
            pathname = pathname.substring(0, pathname.length - 1);
        }
        var realpathname = path.join(__dirname, "./.data", pathname);
        var dirname = path.dirname(realpathname);
        var filename = path.basename(realpathname) + ".json";
        var localpath = [
            realpathname,
            dirname + "/" + req.method.toLowerCase() + "-" + filename,
            dirname + "/" + filename
        ].filter(function(pathstr){
            return fs.existsSync(pathstr) && fs.lstatSync(pathstr).isFile();
        })[0];
        if(localpath) {
            smartResponse(req, resp, localpath);
        } else {
            next();
        }
    });
}

function smartResponse(req, resp, file) {
    let directives = [];
    let pos1 = 0, pos2 = 0, line;
    let regexp = /^\s*\/\//;
    let text = fs.readFileSync(file, "utf-8");
    while(pos2 < text.length) {
        pos2 = text.indexOf("\n", pos1);
        line = text.substring(pos1, pos2);
        if(regexp.test(line)) {
            directives.push(line.substring(2));
            pos1 = pos2 + 1;
        } else {
            break;
        }
    }
    let actions = directives.reduce(function(actions, text){
        let pos = text.indexOf(":");
        let key = text.substring(0, pos).trim();
        let value = text.substring(pos + 1).trim();
        try {
            value = JSON.parse(value);
        } catch(e) {
            // ignore
        }
        actions[key] = value;
        return actions;
    }, {code: 200, delay: false, stop: false, error: false});
    let jsonData;
    try {
        jsonData = JSON.parse(text.substring(pos1));
    } catch(e) {
        actions.code = 500;
        actions.error = "parse json file " + file + " error: " + e.message;
    }
    let doResponse = function(){
        if(actions.stop) {
            return resp.socket.destroy();
        }
        resp.status(actions.code);
        if(actions.error) {
            resp.end(actions.error);
        } else {
            resp.set("Content-Type", "application/json");
            resp.json(Mock.mock(jsonData));
        }
    };
    setTimeout(doResponse, actions.delay || 0);
}


