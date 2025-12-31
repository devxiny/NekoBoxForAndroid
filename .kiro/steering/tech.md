# 技术栈

## 构建系统
- **Gradle**: 使用 Kotlin DSL (`.gradle.kts`)
- **Android Gradle Plugin**: 8.8.1
- **Gradle 版本**: 8.10.2+
- **构建工具版本**: 35.0.1

## 编程语言
- **Kotlin**: 2.0.21 (Android UI 层)
- **Java**: 兼容 Java 8
- **Go**: 核心代理库 (libcore)

## Android 配置
- **编译 SDK**: 35
- **目标 SDK**: 35
- **最低 SDK**: 21 (Android 5.0+)
- **NDK**: 用于构建 Go 原生库

## 核心依赖

### Android 框架
- AndroidX Core KTX
- AndroidX AppCompat
- Material Design Components
- AndroidX Navigation
- AndroidX Room (数据库)
- AndroidX Work Manager

### 网络与代理
- OkHttp 5.0.0-alpha.3
- sing-box (Go 核心库)

### UI 组件
- ZXing Lite (二维码扫描)
- EditorKit (代码编辑器)
- RecyclerView FastScroll

### 数据处理
- Gson (JSON 解析)
- SnakeYAML (YAML 解析)
- Kryo (序列化)

### 其他
- Kotlin Coroutines
- Guava
- ini4j

## Go 核心库 (libcore)
- **构建工具**: gomobile-matsuri
- **核心依赖**: sing-box
- **构建标签**: `with_conntrack,with_gvisor,with_quic,with_wireguard,with_utls,with_clash_api`
- **输出**: libcore.aar (Android Archive)

## 常用命令

### 构建应用
```bash
# 构建所有变体
./gradlew assembleRelease

# 构建特定变体
./gradlew assembleOssRelease
./gradlew assembleFdroidRelease
./gradlew assemblePlayRelease
./gradlew assemblePreviewRelease

# 构建特定架构
./gradlew assembleArm64FdroidRelease
./gradlew assembleArmFdroidRelease
./gradlew assembleX64FdroidRelease
./gradlew assembleX86FdroidRelease
```

### 构建 Go 核心库
```bash
cd libcore
./build.sh
```

### 清理构建
```bash
./gradlew clean
```

### 代码检查
```bash
./gradlew lint
```

## 构建变体 (Flavors)
- **oss**: 开源版本
- **fdroid**: F-Droid 版本
- **play**: Google Play 版本（已废弃）
- **preview**: 预览版本

## 支持的 ABI
- armeabi-v7a
- arm64-v8a
- x86
- x86_64

## 代码混淆
Release 构建启用 ProGuard 混淆和资源压缩（可通过环境变量 `nkmr_minify=0` 禁用）

## 签名配置
通过 `local.properties` 或环境变量配置：
- `KEYSTORE_PASS`: Keystore 密码
- `ALIAS_NAME`: 密钥别名
- `ALIAS_PASS`: 密钥密码
