# 项目结构

## 根目录结构
```
NekoBoxForAndroid/
├── app/                    # Android 应用主模块
├── libcore/                # Go 核心代理库
├── buildSrc/               # 自定义 Gradle 构建逻辑
├── buildScript/            # 构建脚本
├── gradle/                 # Gradle wrapper 文件
├── .kiro/                  # Kiro AI 配置
├── build.gradle.kts        # 根项目构建配置
├── settings.gradle.kts     # Gradle 设置
├── gradle.properties       # Gradle 属性配置
├── nb4a.properties         # 应用版本和包名配置
├── local.properties        # 本地配置（签名等，不提交）
└── README.md               # 项目说明
```

## app/ 模块结构
```
app/
├── src/main/
│   ├── java/                           # Kotlin/Java 源代码
│   │   ├── io/nekohasekai/sagernet/   # 主应用代码（继承自 SagerNet）
│   │   ├── moe/matsuri/nb4a/          # NekoBox 特定代码
│   │   └── com/github/                # 第三方集成
│   ├── aidl/                          # Android 接口定义语言文件
│   ├── res/                           # Android 资源文件
│   │   ├── layout/                    # 布局文件
│   │   ├── drawable/                  # 图标和图形资源
│   │   ├── values/                    # 字符串、颜色、主题等
│   │   ├── values-zh-rCN/            # 简体中文资源
│   │   ├── values-zh-rTW/            # 繁体中文资源
│   │   ├── values-*/                  # 其他语言资源
│   │   ├── menu/                      # 菜单定义
│   │   └── xml/                       # XML 配置
│   ├── assets/                        # 应用资产文件
│   │   ├── yacd.zip                   # Web 控制面板
│   │   └── LICENSE                    # 许可证
│   └── AndroidManifest.xml            # 应用清单
├── libs/                              # 本地库文件
│   └── libcore.aar                    # Go 核心库（编译产物）
├── schemas/                           # Room 数据库 schema
├── build.gradle.kts                   # 应用模块构建配置
└── proguard-rules.pro                 # ProGuard 混淆规则
```

## libcore/ 核心库结构
```
libcore/
├── *.go                    # Go 源代码文件
│   ├── box.go             # sing-box 核心封装
│   ├── http.go            # HTTP 相关功能
│   ├── dns_*.go           # DNS 处理
│   ├── crypto.go          # 加密功能
│   └── nb4a.go            # NB4A 特定接口
├── device/                # 设备相关功能
├── ech/                   # ECH (Encrypted Client Hello) 支持
├── procfs/                # /proc 文件系统访问
├── stun/                  # STUN 协议实现
├── gomobile/              # gomobile 工具链（修改版）
├── go.mod                 # Go 模块定义
├── go.sum                 # Go 依赖校验
├── build.sh               # 构建脚本
└── libcore.aar            # 编译输出（复制到 app/libs/）
```

## buildSrc/ 自定义构建逻辑
```
buildSrc/
├── src/main/kotlin/
│   └── Helpers.kt         # 构建辅助函数
│       ├── setupApp()     # 应用构建配置
│       ├── setupCommon()  # 通用构建配置
│       └── 版本/签名配置
└── build.gradle.kts       # buildSrc 构建配置
```

## 资源文件组织
- **多语言支持**: `values-{语言代码}/strings.xml`
- **主题**: `values/themes.xml` 和 `values-night/themes.xml`
- **图标**: `drawable/` 和 `mipmap-*/`
- **布局**: `layout/` (Activity/Fragment 布局)

## 数据库
- 使用 Room 持久化库
- Schema 文件位于 `app/schemas/`
- 主要数据库：
  - `SagerDatabase`: 主应用数据库
  - `PublicDatabase`: 公共配置数据库
  - `TempDatabase`: 临时数据

## 代码包结构
- `io.nekohasekai.sagernet.*`: 核心应用逻辑（继承自 SagerNet）
- `moe.matsuri.nb4a.*`: NekoBox 特定功能和扩展
- `com.github.*`: 第三方库集成

## 配置文件
- `nb4a.properties`: 版本号、包名等元数据
- `gradle.properties`: Gradle 构建配置
- `local.properties`: 本地环境配置（不提交到版本控制）
- `repositories.gradle.kts`: Maven 仓库配置
