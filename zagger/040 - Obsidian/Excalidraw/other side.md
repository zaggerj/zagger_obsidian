---
created: 2023-11-15T20:47
updated: 2023-11-15T20:47
---
# other side

## 英语

### 编程命名

- 命名缩写

  A
  
  常用编程变量命名英文缩写
  
  addr = address
   app = application
   arg = argument
   asm = assemble
   asyn = asynchronization
   auth = authorization / authentication
   avg = average
  
  
  B
  
  
  buf = buffer
  
  
  C
  
  
  calc = calculate
   cert = certificate
   cmd = command
   cmp = compare
   col = column
   coord = coordinates
   cur = current
  
  
  D
  
  
  db = database
   dec = decrease
   del = delete
   dest / dst = destination
   dev = device
   dict = dictionary
   diff = different
   dir = directory
   disp = display
   dlg = dialog
   doc = document
   drv = driver
  
  
  E
  
  
  env = environment
   err = error
   esc = escape
   ext = extension
   exec = execute
  
  
  F
  
  
  frm = frame
   func / fn = function
  
  
  G
  
  
  grp = group
  
  
  H
  
  
  horz = horizontal
  
  
  I
  
  
  idx = index
   img = image
   inc = increase
   info = information
   init = initial/initialize/initialization
   ins = insert
   inst = instance
   intr = interrupt
   i18n = internationalization
  
  
  L
  
  
  lang = language
   len = length
   lib = library
   lst = list
  
  
  M
  
  
  max = maximum
   mem = memory
   mid = middle
   min = minimum
   msg = message
   mul = multiply
  
  
  N
  
  
  num = number
  
  
  O
  
  
  obj = object
   ofs = offset
   org = origin
  
  
  P
  
  
  param = parameter
   pic = picture
   pkg = package
   pos = position
   prev = previous
   prg = program
   proc = process / procedure
   prop = properties
   psw = password
   ptr = pointer
   pub = public
  
  
  R
  
  
  ref = reference
   reg = register
   req = request
   resp = response
   res = result
   ret = return
   rgn = region
   rsrc = resource
  
  
  S
  
  
  scr = screen
   sec = second
   seg = segment
   sel = select
   src = source
   std = standard
   stm = stream
   str = string
   sub = subtract
   sum = summation
   svr = server
   sync = synchronization
   sys = system
  
  T
  tmp / temp = temporary
   tran / trans = translate/transation/transparent
   txt = text
  U
  upd = update
   upg = upgrade
   util = utility
  V
  var = variable
   ver = version
   vert = vertical
  
  W
  wnd = window
  
  
- 命名技巧

  总的来说，就是英文字母大小写、数字、下划线（_）按照一定的规则搭配，自己比较喜欢的是帕斯卡（pascal）命名法和下划线命名法则。
  
  
  1 三种流行的命名法则
  
  目前，业界共有四种命名法则：驼峰命名法、匈牙利命名法、帕斯卡命名法和下划线命名法，其中前三种是较为流行的命名法。
  
  
  (1)驼峰命令法。 正如它的名称所表示的那样，是指混合使用大小写字母来构成变量和函数的名字。例如，下面是分别用骆驼式命名法和下划线法命名的同一个函数：
  printEmployeePaychecks()；
  print_employee_paychecks()；
  
  第一个函数名使用了驼峰命名法，函数名中的每一个逻辑断点都有一个大写字母来标记。第二个函数名使用了下划线法，函数名中的每一个逻辑断点都有一个下划线来标记。
  
  驼峰命名法近年来越来越流行了，在许多新的函数库和Microsoft Windows这样的环境中，它使用得当相多。另一方面，下划线法是C出现后开始流行起来的，在许多旧的程序和UNIX这样的环境中，它的使用非常普遍。
  
  (2)匈牙利命名法。 广泛应用于象Microsoft Windows这样的环境中。Windows 编程中用到的变量(还包括宏)的命名规则为匈牙利命名法，这种命名技术是由一位能干的 Microsoft 程序员查尔斯-西蒙尼(Charles Simonyi) 提出的。
  
  匈牙利命名法通过在变量名前面加上相应的小写字母的符号标识作为前缀，标识出变量的作用域、类型等。这些符号可以多个同时使用，顺序是先m_(成员变量)、再指针、再简单数据类型、再其它。这样做的好处在于能增加程序的可读性，便于对程序的理解和维护。
  
  例如：m_lpszStr, 表示指向一个以0字符结尾的字符串的长指针成员变量。
  匈牙利命名法关键是：标识符的名字以一个或者多个小写字母开头作为前缀；前缀之后的是首字母大写的一个单词或多个单词组合，该单词要指明变量的用途。
  
  (3)帕斯卡(pascal)命名法。 与驼峰命名法类似，二者的区别在于：驼峰命名法是首字母小写，而帕斯卡命名法是首字母大写，如：
  DisplayInfo();
  stringUserName;
  二者都是采用了帕斯卡命名法。
  
  (4)三种命名规则的小结 ：MyData就是一个帕斯卡命名的示例；myData是一个驼峰命名法,它第一个单词的第一个字母小写,后面的单词首字母大写,看起来像一个骆驼；iMyData是一个匈牙利命名法,它的小写的i说明了它的型态，后面的和帕斯卡命名相同，指示了该变量的用途。
  2 命名的基本原则
  
  (1)标识符的命名要清晰、明了，有明确含义，同时使用完整的单词或大家基本可以理解的缩写，避免使人产生误解——尽量采用采用英文单词或全部中文全拼表示，若出现英文单词和中文混合定义时，使用连字符“_”将英文与中文割开。较短的单词可通过去掉“元音”形成缩写；较长的单词可取单词的头几个字母形成缩写；一些单词有大家公认的缩写。例如：temp->tmp、flag->标志寄存器、statistic->stat、increment->inc、message->msg等缩写能够被大家基本认可。
  
  
  (2)命名中若使用特殊约定或缩写，则要有注释说明。应该在源文件的开始之处，对文件中所使用的缩写或约定，特别是特殊的缩写，进行必要的注释说明。
  
  (3)自己特有的命名风格，要自始至终保持一致，不可来回变化。 个人的命名风格，在符合所在项目组或产品组的命名规则的前提下，才可使用。(即命名规则中没有规定到的地方才可有个人命名风格)。
  
  (4)对于变量命名，禁止取单个字符(如i 、j 、k... )，建议除了要有具体含义外，还能表明其变量类型、数据类型等，但i 、j 、k 作局部循环变量是允许的。 变量，尤其是局部变量，如果用单个字符表示，很容易敲错(如i写成j)，而编译时又检查不出来，有可能为了这个小小的错误而花费大量的查错时间。
  
  (5)除非必要，不要用数字或较奇怪的字符来定义标识符。
  
  (6)命名规范必须与所使用的系统风格保持一致，并在同一项目中统一。
  
  (7)在同一软件产品内，应规划好接口部分标识符(变量、结构、函数及常量)的命名，防止编译、链接时产生冲突。对接口部分的标识符应该有更严格限制，防止冲突。 如可规定接口部分的变量与常量之前加上“模块”标识等。
  
  (8)用正确的反义词组命名具有互斥意义的变量或相**作的函数等。
  下面是一些在软件中常用的反义词组。
  add / remove       begin / end        create / destroy
  insert / delete       first / last         g et / release
  increment / decrement                 put / get
  add / delete         lock / unlock      open / close
  min / max          old / new         start / stop
  next / previous      source / target     show / hide
  send / receive       source / destination
  cut / paste          up / down
  
  示例：
  int  min_sum;
  int  max_sum;
  int  add_user( BYTE *user_name );
  int  delete_user( BYTE *user_name );
  
  (9)除了编译开关/ 头文件等特殊应用，应避免使用_EXAMPLE_TEST_ 之类以下划线开始和结尾的定义。
  3 变量名的命名规则
  
  (1)变量的命名规则要求用“匈牙利法则”。（比较难以掌握）
  
  即开头字母用变量的类型，其余部分用变量的英文意思、英文的缩写、中文全拼或中文全拼的缩写,要求单词的第一个字母应大写。
  即： 变量名=变量类型+变量的英文意思(或英文缩写、中文全拼、中文全拼缩写)
  对非通用的变量，在定义时加入注释说明，变量定义尽量可能放在函数的开始处。
  见下表：
  bool 用b开头 b标志寄存器
  int 用i开头 iCount
  short int 用n开头 nStepCount
  long int 用l开头 lSum
  char  用c开头 cCount
  unsigned char 用by开头
  float 用f开头 fAvg
  double 用d开头 dDeta
  unsigned int(WORD) 用w开头 wCount
  unsigned long int(DWORD) 用dw开头 dwBroad
  字符串 用s开头 sFileName
  用0结尾的字符串 用sz开头 szFileName
  
  (2)指针变量命名的基本原则为：
  对一重指针变量的基本原则为：“p”+变量类型前缀+命名，如一个float*型应该表示为pfStat。对二重指针变量的基本规则为：“pp”+变量类型前缀+命名。对三重指针变量的基本规则为：“ppp”+变量类型前缀+命名。
  
  (3)全局变量用g_开头,如一个全局的长型变量定义为g_lFailCount。
  
  即：变量名=g_+变量类型+变量的英文意思(或缩写)。此规则还可避免局部变量和全局变量同名而引起的问题。
  
  
  (4)静态变量用s_开头,如一个静态的指针变量定义为s_plPerv_Inst。
  
  即： 变量名=s_+变量类型+变量的英文意思(或缩写)
  
  
  (5)对枚举类型(enum)中的变量，要求用枚举变量或其缩写做前缀。 并且要求用大写。如：
  enum cmEMDAYS
  {
  EMDAYS_MONDAY;
  EMDAYS_TUESDAY;
  ……
  };
  
  (6)对struct、union变量的命名要求定义的类型用大写。 并要加上前缀，其内部变量的命名规则与变量命名规则一致。
  
  结构一般用S开头，如：
  struct ScmNPoint
  {
  int nX;//点的X位置
  int nY; //点的Y位置
  };
  
  联合体一般用U开头，如:
  union UcmLPoint
  {
  LONG lX;
  LONG lY;
  }
  
  (7)对常量(包括错误的编码)命名，要求常量名用大写，常量名用英文表达其意思。
  
  当需要由多个单词表示时，单词与单词之间必须采用连字符“_”连接。
  
  如：#define CM_FILE_NOT_FOUND CMMAKEHR(0X20B) 其中CM表示类别。
  
  (8)对const 的变量要求在变量的命名规则前加入c_。 即：c_+变量命名规则；示例：const char* c_szFileName;
  4 函数的命名规范
  
  (1)函数的命名应该尽量用英文(或英文缩写、中文全拼、中文全拼缩写)表达出函数完成的功能——函数名应准确描述函数的功能。遵循动宾结构的命名法则，函数名中动词在前,并在命名前加入函数的前缀，函数名的长度不得少于8个字母。函数名首字大写，若包含有两个单词的每个单词首字母大写。如果是OOP 方法，可以只有动词(名词是对象本身)。示例：
  
  LONG GetDeviceCount(……);
  void print_record( unsigned int rec_ind ) ;
  int  input_record( void ) ;
  unsigned char get_current_color( void ) ;
  
  (2)避免使用无意义或含义不清的动词为函数命名。 如使用process、handle等为函数命名，因为这些动词并没有说明要具体做什么。
  
  (3)必须使用函数原型声明。 函数原型声明包括：引用外来函数及内部函数，外部引用必须在右侧注明函数来源： 模块名及文件名；内部函数，只要注释其定义文件名——和调用者在同一文件中(简单程序)时不需要注释。
  应确保每个函数声明中的参数的名称、类型和定义中的名称、类型一致。
  5 函数参数命名规范 (1)参数名称的命名参照变量命名规范。
  (2)为了提高程序的运行效率，减少参数占用的堆栈，传递大结构的参数，一律采用指针或引用方式传递。
  (3)为了便于其他程序员识别某个指针参数是入口参数还是出口参数，同时便于编译器检查错误，应该在入口参数前加入const标志。
  如：……cmCopyString(const CHAR * c_szSource, CHAR * szDest)
  6 文件名(包括动态库、组件、控件、工程文件等)的命名规范 文件名的命名要求表达出文件的内容，要求文件名的长度不得少于5个字母，严禁使用象file1,myfile之类的文件名。
  
  
- 常用英文词汇

  https://segmentfault.com/a/1190000020073758?utm_source=tag-newest
  文中的单词并没有给出其词性，很多词性的变化需要读者具备一定的英语语法知识，以便在特定情况下灵活运用。
  
  数字
  数字部分包含英文的数字表示、数字运算符、数字单位
  
  infinite: 无限的
  
  英文数字
  
  zero: 零
  one: 一
  two: 二
  three: 三
  four: 四
  five: 五
  six: 六
  seven: 七
  eight: 八
  nine: 九
  ten: 十
  eleven: 十一
  twelve: 十二
  thirteen: 十三
  fourteen: 十四
  fifteen: 十五
  sixteen: 十六
  seventeen: 十七
  eighteen: 十八
  nineteen: 十九
  twenty: 二十
  thirty: 三十
  forty: 四十
  fifty: 五十
  eighty: 八十
  ninety: 九十
  hundred: 百
  thousand: 千
  million: 百万
  billion: 十亿
  
  计数单位
  
  pixel: 像素
  percent: 百分比
  
  // 中文数字
  ten: 十
  hundred: 百
  thousand: 千
  ten thousand: 万
  billion: 亿
  trillion: 兆
  
  // 存储容量
  byte: 字节 B
  kilobyte: 千字节 KB
  megabyte 兆字节 MB
  gigabyte 吉字节 GB
  trillionbyte 太字节 TB
  
  进制
  
  decimal: 十进制
  hex: 十六进制
  binary: 二进制
  octal: 八进制
  
  运算符
  
  add: 加
  subtract: 减
  multiply: 乘
  divide: 除
  and: 与
  or: 或
  not: 非
  intersection: 交集
  compose: 并集
  键盘符号
  punctuator: 标点符号
  identifier: 标识符
  
  // Unique graphic character allocations
  // 独特的图形字符分配
  // --------------------------------------------------------
  exclamation mark: ! 感叹号
  quotation mark: " 双引号
  percent sign: % 百分号
  ampersand: & and符号
  apostrophe: ' 撇号
  ellipse/apostrophe: …… 省略号
  left parenthesis: ( 左括号
  right parenthesis: ) 右括号
  asterisk: * 星号
  plus sign: + 加号
  comma: , 逗号
  slight-pause mark: 、 顿号
  hyphen-minus: - 连字符(-) 或者 减号(-)
  full stop: . 句号
  middle dot: ・ 中间点
  interpunct: · 间隔号
  hyphenation point: · 连字点
  solidus: / 斜线
  colon: : 冒号
  semicolon: ; 分号
  less-than sign: < 小于符号
  equals sign: = 等于符号
  greater-than sign: > 大于符号
  question mark: ? 问号
  low line: _ 下划线
  digital 0: 0 数字 0
  latin capital letter A:  A 大写拉丁字母
  latin small letter A: A 小写拉丁字母
  
  // Alternative graphic character allocations
  // 可选的图形字符分配
  // --------------------------------------------------------
  number sign: # 数字符号
  pound sign: £ 英镑符号
  dollar sign: $ 美元符号
  currency sign:  货币符
  
  // IRV(International Reference Version) graphic character allocations
  // IRV图形字符分配
  // --------------------------------------------------------
  number sign: # 数字符号
  dollar sign: $ 美元符号
  commercial at: @ 
  left square bracket: [ 左方括号
  reverse solidus: \ 反斜线
  right square bracket: ] 右方括号
  circumflex accent: ^ 抑扬音符号
  grave accent: ` 沉音符
  left curly bracket: { 左花括号
  vertical line: | 垂直线
  right curly bracked: } 右花括号
  tilde: ~ 波浪符
  说明：由于标点符号中英文语言环境同一个符号也不同叫法别名，因此上面列举的词汇只能说涉及到了部分，并没有把所有 Dialect(方言) 包含进来。
  注：· 符号在不同的上下文中有不同的叫法，比如“间隔号”、“中间点”、“项目符号”、“连子点”等，虽然肉眼看起来没有什么大的区别，但是在计算机中的Unicode编码是不一样的，更多参见间隔符
  时间、日期
  下面虽然列举了很多时间相关的词汇，但是在实际前端开发过程中用到的就年、月、日和时、分、秒、毫秒。
  
  time: 时间
  date: 日期
  workday: 工作日
  weekend: 周末
  season: 季节
  anniversary: 周年
  century: 世纪；百年
  quarter: 一刻钟
  holiday: 节日；假日
  morning: 上午
  noon/midday: 中午
  afternoon: 下午
  night: 晚上
  midnight: 半夜
  yesterday: 昨天
  today: 今天
  tomorrow: 明天
  clock: 时钟
  now: 现在；如今；立刻
  nowadays: 现今；时下
  present: 现在（的）
  former: 从前的；前任的
  before: 在...之前
  after: 在...之后
  future: 将来
  permanent: 永久的；不变的
  period: 周期；期间；一段时间
  during: 在...的期间；在...期间的某个时候
  term: 学期；期限
  early: 早期的，提早；在初期
  ahead: 在前的；领先的；提前的
  later: 后来；稍后；随后
  start/begin: 开始
  end: 结束
  pause: 暂停
  suspend: 推迟；使暂停
  timeout: 超时；暂时休息；工间休息
  interval: 间隔
  overtime: 超时的；加班的，加班时间
  
  时间
  
  year: 年
  month: 月
  day: 日
  week: 周
  hour: 小时
  minute: 分
  seconds: 秒
  millisecond: 毫秒
  
  星期
  
  Monday: 星期一
  Tuesday: 星期二
  Wednesday: 星期三
  Thursday: 星期四
  Friday: 星期五
  Saturday: 星期六
  Sunday: 星期日
  
  月份
  
  January: 一月
  February: 二月
  March: 三月
  April: 四月
  May: 五月
  June: 六月
  July: 七月
  August: 八月
  September: 九月
  October: 十月
  November: 十一月
  December: 十二月
  
  季节
  
  spring: 春季
  summer: 夏季
  autumn: 秋季
  winter: 冬季
  地理位置
  map: 地图
  location: 地理位置
  place: 地方
  earth: 地球
  province: 省
  city: 市
  district: 区
  area: 区域、范围
  region: 地区、范围、部位
  address: 地址
  edges: 边界
  boundary: 边界；范围；分界线
  coordinate: 坐标
  east: 东
  south: 南
  west: 西
  north: 北
  方位
  direction: 方向
  position: 位置
  top: 上
  right: 右
  bottom: 下
  left: 左
  opposite: 对面的
  center: 中间（水平）
  middle: 中间（垂直）
  排版
  abstract: 摘要
  annex: 附录
  suffix: 后缀；词尾
  prefix: 前缀
  titl: 标题
  summary: 总结；概要
  specifications: 规范
  headline: 大标题；内容提要；栏外标题
  preface: 前言；引语；序言
  chapter: 章；篇；回
  section: 章节；部分
  abbreviation: 缩写；缩写词
  
  font: 字体
  color: 颜色
  heading: 标题
  align: 对齐
  align left/align center/align right: 左对齐/居中对齐/右对齐
  align top/align middle/align bottom: 顶对齐/垂直居中/底部对齐
  text: 文本
  zoom: 放大
  size: 大小
  opacity: 透明度
  position: 位置
  rotation: 旋转
  fill: 填充
  shadow: 阴影
  blur: 模糊
  filter: 滤镜
  radius: 圆角
  unite: 合并
  subtract: 差集
  intersect: 交集
  exclude: 排除
  join: 合并
  insert image: 插入图片
  code: 插入代码
  highlight: 高亮
  strikethrough: 删除线
  underscore: 下划线
  italic: 斜体
  bold: 粗体
  horizontal line: 水平分隔线
  attach file: 附加文件
  checklist: 清单列表
  bullet: 项目符号
  indention: 缩进
  形状
  figure: 图形
  stroke: 描边
  fill: 填充
  border: 边框
  line: 线
  rectangle: 矩形
  ellipse: 椭圆
  sphere: 球
  triangle: 三角形
  sector: 扇形
  annulus: 圆环
  trapezium: 梯形
  polygon: 多边形
  arch: 弓形
  circle: 圆、循环、周期
  star: 星形、评分
  cylinder: 圆柱
  circle cone: 圆锥
  love: 爱心
  语法
  grammar: 语法
  syntax: 句法
  morphology: 词法
  structure: 结构
  sentence: 句子
  clause: 从句
  phrase: 词组
  word: 单词
  adjective: 形容词
  verb: 动词
  noun: 名词
  abstract noun: 抽象名词
  pronouns: 代词
  determiner: 限定词
  conjunction: 连词
  interjection: 感叹词
  adverb: 副词
  preposition: 介词；前置词
  derivative: 派生词
  numeral: 数词
  auxiliary: 助动词
  tense: 时态
  passive: 被动语态
  gerund: 动名词
  antonym: 反义词
  article: 冠词
  antecedent: 先行词
  regular/irregular verbs: 规则╱不规则动词
  transitive/intransitive verbs: 及物╱不及物动词
  subject: 主语
  object: 宾语
  predicate: 谓语；表语
  adverbial: 状语
  complement: 补语
  appositive: 同位语
  adjunct: 修饰语
  affix: 词缀
  acronym: 首字母缩略词
  abbreviation: 缩写词
  常用颜色
  pink: 粉红
  violet: 紫罗兰
  magenta: 洋红(玫瑰红)
  purple: 紫色
  blue: 纯蓝
  azure: 蔚蓝色
  cyan: 青色
  green: 纯绿
  lime: 闪光绿
  ivory: 象牙色
  yellow: 纯黄
  olive: 橄榄
  gold: 金色
  orange: 橙色
  snow: 雪白色
  red: 纯红
  brown: 棕色
  white: 纯白
  sliver: 银灰色
  gray: 灰色
  black: 纯黑
  JavaScript语言相关
  type: 数据类型
  primitive type: 原始类型
  object: 对象
  array: 数组
  string: 字符串
  boolean: 布尔值
  symbol: 符号
  undefined: 未定义
  null: 空
  function: 函数
  array function: 箭头函数
  curried function: 柯里函数
  callback: 回调函数
  class: 类
  module: 模块
  import: 导入
  export: 导出
  constructor: 构造函数
  prototype: 原型
  reference: 引用
  closure: 闭包
  destructure: 解构
  variable: 变量
  property: 属性
  attribute: 特性
  iterator: 迭代器
  generator: 生成器
  yield: 产出
  observable: 可观赛的
  hosit: 提升
  operator: 运算符
  equal: 相等
  statement: 语句
  block: 块
  comment: 注释
  whitespace: 空格
  event: 事件
  listener: 监听器
  accessor: 访问器
  decorator: 装饰器
  proxy: 代理
  reflect: 反射
  promise: 承诺
  test: 测试
  fetch: 拿；取
  descriptor: 描述符号
  sync: 同步
  async: 异步
  await: 等候
  find: 查找
  every: 所有
  some: 部分
  foreach: 为每一个
  map: 遍历
  filter: 过滤
  pad: 填充
  index: 索引
  data: 数据
  slice: 把...分成部分
  splice: 拼接，接合
  reduce: 归纳
  push: 推
  pull: 拉
  pop: 弹出
  split: 分离
  join: 连接
  flatten: 变平
  replace: 替换
  search: 搜索
  scope: 作用域
  timeout: 超时
  interval: 间隔
  value: 值
  define: 定义
  math: 数学
  sum: 求和
  configurable: 可配置
  enumerable: 可枚举
  writable: 可写
  local: 局部的
  global: 全局的
  not: 非
  or: 或
  xor: 异或
  and: 且
  regexp: 正则表达式
  match: 匹配
  pattern: 模式
  greed: 贪婪
  color: 颜色
  rest: 剩余
  assign: 赋值
  tag: 标签
  buffer: 缓冲区
  super: 极好的
  extend: 扩展
  readonly: 只读
  override: 重写
  dynamic: 动态的；多态
  default: 默认的
  implement: 实现；执行
  strict: 严格的
  deprecate: 不推荐；反对
  tab: 制表符
  space: 空格
  indentation: 缩进
  public: 公共的
  private: 私有的
  namespace: 命名空间
  member: 成员
  method: 方法
  parameter/argument: 参数
  instance: 实例
  ternary: 三目运算
  literary: 字面量
  template: 模板
  character: 字符
  markup: 标记
  syntax: 语法
  equality: 相等
  conditional statements: 条件判断语句
  true: 是
  false: 否
  type-checker: 类型检查
  compile-time: 编译时
  lexical scope: 词法作用域
  static scope: 静态作用域
  loop: 循环
  notation: 符号
  operand: 操作数；运算对象
  ordinary object: 普通对象
  standard object: 标准对象
  built-in object: 内置对象
  exotic object: 外来对象
  last-in/first-out manner: 后进先出的方式
  reserved word: 保留单词
  signature: 签名
  enumerable: 可枚举的
  iterable: 可迭代的
  
  // 简写
  ajax
  json
  常用简写
  简写后面用 ”*“ 号标注的为推荐使用简写，可以放心大胆在项目中使用。
  
  hd -> head
  hdr -> header
  bd -> body
  ft -> foot
  ftr -> footer
  tbl -> table
  el -> element **
  cnt -> content
  cmp -> component
  btn -> button **
  sel -> select *
  opt -> option *
  chk -> checkbox
  lbl -> label
  wiz -> wizard *
  bg -> background **
  cur -> current **
  prev -> previous **
  idx -> index
  len -> length **
  pg -> page
  vm -> view page
  repo -> repository *
  org -> organization *
  ref -> reference *
  res -> response **
  req -> request **
  msg -> message **
  str -> string **
  ch -> chracter *
  lbl -> label
  img -> image **
  buf -> buffer *
  usr -> user
  args -> arguments *
  no -> number
  err -> error *
  tmp/temp -> temporary **
  rst -> result
  bdr -> border
  fn/func -> function **
  nav -> navigator *
  val -> value
  params -> parameter *
  dev -> development *
  prod -> product *
  util -> utility *
  hoc -> high order component *
  cb -> callback *
  lib -> library *
  prop(s) -> property(ies) *
  attr(s) -> attribute(s) *
  arr -> array *
  conf -> config *
  dlg -> dialog
  e/ev/evt -> event **
  pkg -> package *
  tpl -> template *
  addr -> address
  desc -> descending
  aesc -> aescending
  expr -> expression **
  src -> source **
  hoz -> horizontal
  vert -> vertical
  abbr -> abbreviate
  env -> envirnment **
  sec -> seconds *
  ms -> millisecond **
  bool -> boolean *
  dbl -> double
  常用词汇及其变体
  active -> inactive -> deactive
  load -> preload -> unload
  coming -> incoming
  with -> without
  sync -> async
  allowed -> unallowed
  going -> ingoing -> ongoing
  online -> offline
  visible -> invisible
  finite -> infinite
  able -> enabled -> unable -> disabled
  login -> logout
  singin -> signout
  check -> uncheck
  select -> unselect
  inlet -> outlet
  regular -> irregular
  implicit -> explicit
  import -> export
  micro -> macro
  专用名词缩写
  GUI -> Graphical User Interface 图形用户界面
  OEM -> Original Equipment manufacturer 原始设备制造商
  CMS -> Content Manager System 内容管理系统
  PWA -> Progressive Web App 渐近式Web应用
  SDK -> Software Development Kit 软件开发工具包
  IDE -> Integrated Development Envirnment 集成开发环境
  SOA -> Service-Oriented Architecture 面向服务架构
  ORM -> Object Relation Mapping 对象关系映射
  MVC -> Model View Controller
  OOP -> Object Oriented programing 面向对象编程
  BEM -> Block Element Modifier 块-元素-修饰符
  BFC -> Block Format Context 
  SKU -> Stock Keeping Unit 库存单位
  AJAX -> Asynchronous JavaScript and 
  HOC -> High Order Component 高阶组件
  I18N -> Internationalization 国际化
  GUID -> Globally Unique Identifier 全球唯一标识符
  UI组件相关
  参考Element、Antd、Bootstrap和Material Design
  
  // 通用
  Head: 标题
  Label: 标签
  Button: 按钮
  Icon: 图标
  Link: 文字链接
  Input: 输入框
  Checkbox: 筛选框
  Radio: 单选框
  Select: 下拉选择框
  Switch: 开关
  Upload: 文件上传
  Form: 表单
  Radio: 音频
  Video: 视频
  Canvas: 画布
  
  // 布局
  Layout: 布局
  Grid: 网格；栅格
  Container: 布局容器
  
  // 导航
  Affix: 固钉
  Breadcrumb: 面包屑
  Dropdown: 下拉菜单
  Menu: 导航菜单
  Pagination: 分页
  PageHeader: 页头
  Steps: 步骤条
  NavMenu: 导航菜单
  Minimap: 小地图
  
  // 数据录入
  AutoComplete: 自动完成
  Cascader: 级联选择框
  DatePicker: 日期选择框
  TimePicker: 时间选择框
  DateRangePicker: 日期区间选择框
  ColorPicker: 颜色选择框
  InputNumber: 数字输入框
  Mentions: 提及
  Rate: 评分
  Slider: 滑动输入条；滑块
  TreeSelect: 树选择器
  Transfer: 穿梭框
  Wizard: 向导
  
  // 数据展示
  Avatar: 头像
  Badge: 徽标数
  Comment: 评论
  Collapse: 折叠面板
  Carousel: 走马灯；轮播
  Card: 卡片
  Panel: 面板
  Calender: 日历
  Descriptions: 描述列表
  Empty: 空状态
  List: 列表
  Popover: 气泡卡片
  Statistic: 统计数值
  Tree: 树形控件
  Tooltip: 文字提示
  Timeline: 时间轴
  Tag: 标签
  Tabs: 标签页
  InfiniteScroll: 无限滚动
  Chips: 芯片
  Dialog: 对话框
  
  // 反馈
  Alert: 警告提示
  Drawer: 抽屉
  Modal: 对话框
  Message: 全局提示
  MessageBox: 弹框
  Notification: 通知提醒框
  Progress: 进度条
  Popconfirm: 气泡确认框
  Result: 结果
  Spin: 加载中
  Skeleton: 骨架屏
  
  // 其它
  Anchor: 锚点
  BackTop: 回到顶部
  Divider: 分隔线
  ConfigProvider: 全局化配置
  
  // Button 尺寸
  // --------------------------------------------------------
  mini: 微型的；袖珍的
  tiny: 微小的；很少的
  micro: 极小的；基本的；微小的；微观的
  small: 小
  medium: 中等
  large: 大
  fixed: 固定宽度的
  
  // Button 外观
  // --------------------------------------------------------
  default: 默认的
  plain: 朴素的
  primary: 主要的
  info: 信息的
  warning: 警告的
  error: 错误的
  danger: 危险的
  gray: 灰色的
  link: 带链接的
  outline: 带轮廓的
  dashed: 带虚线的
  round: 带圆角的
  circle: 圆形的
  ghost: 幽灵的
  
  // 表单控件验证状态
  // --------------------------------------------------------
  valid: 有效的
  invalid: 无效的
  pending: 验证中
  required: 必填的
  dirty: 脏的
  pristine: 干净的
  代码常用词汇
  下面列出开发过种中经常使用的动词、名词、介词、形容词。这些词汇通常可以相互组合在特定上下文中适当变动可以覆盖工作中的绝大多数场景。
  
  // 动词
  on: 监听、正在进行中
  get: 取
  set: 设置
  fetch: 获取
  find: 查找
  add: 添加
  create: 创建
  remove: 移除
  delete: 删除
  update: 更新
  upgrade: 升级
  downgrade: 使降级
  sync: 同步
  toggle: 切换
  pull: 拉
  push: 推
  show: 显示
  hide: 隐藏
  resolve: 解析；分解
  parse: 解析
  lock: 锁定
  link: 连接
  merge: 合并
  close: 关闭
  clone: 克隆
  clear: 清除
  format: 格式化
  convert: 转变
  cancel: 取消
  accept: 承认；同意
  check: 检查，核对
  concat: 合并数组、字符串
  join: 合并
  split: 分开
  spread: 展开
  search: 搜索
  sort: 排序
  assign: 分配，指定
  handle: 处理
  trigger: 触发
  login: 登入
  logout: 登出
  register: 注册
  sign: 签名
  throw: 抛出
  load: 加载
  preload: 加载
  copy: 复制
  paste: 粘贴
  connect: 连接
  change: 改变
  select: 选择
  validate: 验证
  submit: 表单提交
  commit: 提交
  match: 匹配
  scroll: 滚动
  write: 写
  read: 读
  enable: 启用
  disable: 禁用
  limit: 限制
  bootstrap: 启动
  init: 初始化
  install: 加载
  upload: 上传
  inject: 注入
  provide: 提供
  exit: 退出
  access: 访问
  flush: 刷新/使暴露
  refresh: 刷新
  release: 发布
  preview: 预览；试映
  publish: 出版；发行
  navigate: 导航；浏览
  redirect: 重定向
  back: 返回
  switch: 切换
  launch: 加载
  browse/visit: 浏览
  append: 追加
  insert: 插入
  swap: 交换
  map: 遍历
  extract: 提取；选取
  provide: 提供
  inject: 注入
  observe: 观察
  render: 渲染
  debug: 调试
  align: 对齐
  popup: 弹出
  transfer: 转让、迁移
  attach: 附加
  build: 构建
  diagnose: 诊断，断定
  ignore: 忽略
  deploy: 部署；展开
  send/sent: 送；寄出
  defer: 推迟
  delegate: 委托
  destroy: 销毁
  dispatch: 派发；分派
  trace: 追踪
  
  // 名词
  avatar: 头像
  brand: 品牌
  record: 记录
  issue: 问题
  project: 项目
  repo(repository): 仓库；知识库
  ecosystem: 生态系统
  assets: 资产
  resource: 资源
  toolkit: 工具包、工具箱
  workbench: 工作台
  item: 项目；条款
  option: 选项
  field: 字段
  type: 类型
  status: 状态
  property: 属性
  attribute: 特性
  parameter/argument: 参数
  length: 长度
  size: 尺寸
  shape: 形状
  label: 标签
  value: 值
  view: 视图
  page: 页面
  env(envirnment): 环境
  context: 上下文
  count: 总数；计数
  amount: 数量；数额
  sum: 合计；金额
  num(number): 号码
  total: 总数
  money: 钱；货币
  filter: 过滤器
  pipe: 管道
  stream: 流
  buffer: 缓冲器
  comment: 评论
  ref(reference): 引用
  res(response): 响应
  req(request): 请求
  entity: 实体
  event: 事件
  setup 设置
  prefix 前缀
  suffix 后缀
  wizard 小部件
  model 模型
  flag 标志
  factory 工厂
  service 服务
  constant: 常量
  var(iable): 变量
  collection: 集合
  array: 数组
  raw: 原始值
  platform 平台
  capital: 大写字母
  uppercase/lowercase: 大/小写
  letter: 字母
  entrance: 入口
  path: 路径
  route: 路由
  router: 路由器
  config: 配置
  middleware: 中间件
  success: 成功
  error: 错误
  fail(ure): 失败
  frontend: 前端
  backend: 后端
  local: 本地
  sever: 服务器
  production: 线上；产品
  border: 边框
  outline: 轮廓
  precision: 精度
  separator: 分隔符
  mask: 遮罩
  metadata: 元数据
  location: 位置
  sandbox: 沙箱
  scope: 作用域
  queue: 队列
  heap: 堆
  notice: 通知
  bubble: 气泡
  hooks: 钩子
  cell: 单元格
  row: 行
  column: 列
  group: 组
  cursor: 游标
  pattern: 模式
  abstract: 抽象
  compose: 复合；并集
  callback: 回调函数
  priority: 优先级
  grade/rank/hierarchy 等级、层级
  table,chart, graph, diagram: 表格，图表，曲线图，图表
  system: 系统、体系
  guards: 保障、守卫
  segment/fragment: 片段、碎片
  shaking: 抖动
  mix: 混淆
  dependence: 依赖
  injection: 注入
  markup: 标记
  email: 电子邮件
  version: 版本
  detail: 详情
  stub: 存根
  score: 成绩
  breakpoint: 断点
  record: 记录
  pointer: 指针
  thumbnail: 缩略图
  gallery: 画廊
  viewport: 视口
  strategy: 策略
  outlet: 出口
  inlet: 入口
  gist: 主旨；要点；依据
  licence: 许可证
  copyright: 版权
  order: 命令
  input: 输入
  output: 输出
  effect: 影响；效果；作用
  position: 位置
  corner: 角落
  animation: 动画
  dot: 点
  palette: 调色板；颜料
  album: 相册
  photo: 照片
  host: 主机
  session: 会话
  cookie: 饼干；小甜点
  domain: 域名
  certificates: 证书
  coercion: 强制
  payload: 载物
  thread: 线程
  process: 进程
  timestamp: 时间缀
  conflicts: 冲突
  terminal: 终端
  portrait: 肖像
  auxiliary: 附属物
  backup: 备份
  bitmap: 位图
  breakpoint: 断点
  concurrency: 并发
  lock: 锁
  digest: 摘要
  exception: 异常
  genericity: 泛型
  handle: 句柄
  macro: 宏
  manifest: 清单
  modifier: 修饰字；修饰符
  override: 覆写
  overload: 重载
  procedure: 过程
  protocol: 协议
  recursion: 递归
  marquee: 跑马灯
  
  // 形容词
  native: 原生的
  hybrid: 混合的
  basic: 基础的
  complex: 复杂的
  empty: 空的
  online: 在线的
  offline: 离线的
  public: 公共的
  private: 私有的
  static: 静态的
  dynamic: 动态的
  shared: 共享的
  safe: 安全的
  relative: 相对的
  absolute: 绝对的
  original: 原始的
  infinite: 无限的
  partial: 局部的
  ascending: 按升序
  descending: 按降序
  primary: 原始的，第一的
  secondary: 第二的
  tertiary: 第三的
  deprecated: 弃用的
  concrete: 具体的
  abstract: 抽象的
  explicit: 显示的；明确的
  implicit: 含蓄的；暗示的
  mutable: 可变的
  业务常用词汇
  # 电商
  coupons: 优惠券
  couponsCode: 优惠码
  discount: 折扣
  points: 积分
  memeber: 会员
  vip: 会员
  membership: 会员
  delivery: 运费
  domain: 域名
  dashboard: 仪表盘
  store: 门店
  shop: 店铺
  product: 产品
  goods: 商品
  order: 订单
  setting: 设置
  manager: 管理
  channel: 渠道
  notFound: 404页面
  feedback: 反馈
  scratch: 刮刮卡
  client: 客户端
  market: 市场
  promotion: 促销
  popularize: 推广
  tool: 工具
  banner: 广告
  friendlink：友情链接
  partner： 合作伙伴
  vote: 投票
  技术文章阅读常用词汇
  
  // 副词
  approximately: 大约；近似地；近于
  indirectly: 间接地；迂回地
  inevitably:不可避免地；必然地
  repeatedly: 反复地；再三地
  defiantly: 挑战地；对抗地
  
  // 形容词
  general: 一般的；普通的；大体的
  partial: 局部的
  well-formed：符合语法规则的
  appropriate: 适当的；恰当的；合适的
  reasonable: 合理的；公道的
  non-trivial: 非平凡的
  conditional: 有条件的；假定的
  disheartened: 沮丧的；灰心的
  unmotivated: 对（工作等）不感兴趣的；没有理由的
  terse: 简洁的；精练的；扼要的
  chaotic: 混沌的；混乱的，无秩序的
  effective: 有效的
  discursive: 离题的；东拉西扯的；无层次的
  impressive: 感人的；令人钦佩的；给人以深刻印象的
  error-prone: 于出错的
  weird: 怪异的；不可思议的；超自然的
  hypothetical: 假设的；假定的
  tricky:  狡猾的；机警的；棘手的
  analogous: 类似的
  haunted: 闹鬼的；反复出现的；受到困扰的
  assigned: 指定的；已分配的
  predictable: 可预言的
  
  // 名词
  dependencies: 依赖性；相关性
  compatibility: 兼容性
  consistency: 一致性
  consensus: 一致；舆论；合意
  profile: 轮廓；外形；简况
  utilities: 实用程序
  assumption: 假定；设想
  coercion:强制；强迫
  paradigm: 范例
  formula: 公式
  truth: 真值
  falsey: 假值
  strategy: 战略；策略
  precedence: 优先；居先
  interlude: 插曲
  mechanism: 机制；原理，途径；进程；机械装置；技巧
  piece: 片段
  lookup: 查找；检查
  multiplication: 乘法
  analogy: 类比；类推；类似
  coordinate: 坐标
  realm: 领域；范围；王国
  accent: 口音；重音；强调；特点；重音符号
  radix: 基数；根
  bullets: 项目符号
  reconciliation: 调度；和解
  security: 安全性
  registry: 注册
  bot: 网上机器人；自动程序
  inline: 内联
  capacity: 容量
  achievement: 成就；完成；成绩
  reactivity: 响应式
  extensions: 扩展程序
  
  // 动词
  persuade: 说服；劝说
  tackle: 应付；处理（难题或局面）
  indulge: 沉溺；沉迷
  initialize: 初始化
  evaluate: 评价；估价；求...的值
  vanish: 消失；突然不见
  plug-n-play: 即插即用
  commence: 开始；着手
  comprehend: 理解；包含；由...组成
  release: 释放；发布
  pin: 钉住；压住
  extract: 抽出
  
  // 短语
  write up: 写文章赞扬；提高资产等的账面价值；详细记载；补写
  
  // 感叹词
  lo and behold: 你瞧
  
  
- approach途径

	- The same approach

- in place to
- breakdown分为细目

	- For a full breakdown of each method available

- essential本质的，极其重要的
- implicit含蓄的
- desirable值得做的
- hex十六进制
- Identical 一样的相同的

	- The two parties fought the last election on almost identical manifestos.
	- 两个政党以几乎完全相同的竞选宣言参加了上次竞选。
	- -p, --print "script"
	- Identical to -e but prints the result.

- Evaluate估计; 评价; 评估;

	- We need to evaluate how well the policy is working.
	- 我们需要对这一政策产生的效果作出评价
	- -e, --eval "script"
	- Evaluate the following argument as JavaScript.

- Preload预载; 预装

	- Construction Method for Controlled Water Test to Preload Large Oil Tank Subgrade
大型油罐地基充水预压工法简介

## 数学

## 计算机学科

### 计算机网络

### 编辑原理

### 操作系统

### 算法原理

### 软件工程

### 软件测试原理

## 后端工具

## 测试

### firebug/firebug-lite

### web inspector

### YSlow/Smushit

### SuperPreview/JsBeautifer

### Fiddler/WireShark/tcpdump

## 性能

### WebPageTest

### ShowSlow

### YSlow

### 34Rule

### PageSpeed

### HttpWatch

### DynaTrace's Ajax

### 压缩

### css sprites

### 合并 减少http请求

### 缓存

### CDN

### 避免重定向

## 安全

### 同源策略

### CSRF/XSS

### ADsafe/Caja/FBJS/Sandbox

### 点击劫持

### SQL注入

## 工作流程

### JSLint/CSSLint/YUICompressor

### JSMin/TPacker-minifier

### Ant/Make

### JSDoc/YUIDoc

### LAMP

## 移动端

### JqueryMobile/html5/css3

### iPhone/iPad/iOs/android

### responsive UI Design

## 博客

### [技术方案：docsify + vuep + gitalk](https://lhammer.cn/You-need-to-know-css/#/zh-cn/introduce?v=1)

网易严选设计规范http://www.zcool.com.cn/work/ZMjAxNjc4ODQ=.html

同类型：
https://github.com/chokcoco/CSS-Inspiration

## md文档教程

