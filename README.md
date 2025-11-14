# ZREBypass - 二进制/Shellcode/Webshell 免杀工具

ZREBypass 是一款专业的免杀处理工具，支持二进制文件、Shellcode 和 Webshell 的免杀处理，集成了反调试、反虚拟机、反沙箱等多种对抗技术。

## 功能特性

### 核心功能
- ✅ 二进制文件免杀处理
- ✅ Shellcode 加密与加载
- ✅ Webshell 混淆处理
- ✅ 多种加密算法支持（XOR、AES、RC4、ChaCha20）

### 对抗技术
- 🛡️ 反调试检测（IsDebuggerPresent、CheckRemoteDebuggerPresent）
- 🛡️ 反虚拟机检测（进程、注册表、MAC地址）
- 🛡️ 反沙箱检测（时间加速、资源检测、用户活动）
- 🛡️ 代码混淆与加密

## 使用方法

### 1. 二进制文件免杀

```bash
# 基础用法
zrebypass.exe -mode binary -input malware.exe -output bypass.exe

# 指定加密方法
zrebypass.exe -mode binary -input malware.exe -output bypass.exe -method aes -key mySecretKey

# 禁用某些检测
zrebypass.exe -mode binary -input malware.exe -output bypass.exe -anti-debug=false
```

### 2. Shellcode 处理

```bash
# 处理 Shellcode
zrebypass.exe -mode shellcode -input payload.bin -output loader.exe -method chacha20

# 使用自定义密钥
zrebypass.exe -mode shellcode -input payload.bin -output loader.exe -method aes -key "MyStrongPassword123"
```

### 3. Webshell 混淆

```bash
# PHP Webshell 混淆
zrebypass.exe -mode webshell -input shell.php -output obfuscated.php -method base64

# ASP Webshell 混淆
zrebypass.exe -mode webshell -input shell.asp -output obfuscated.asp -method variable
```

## 参数说明

| 参数 | 说明 | 默认值 |
|------|------|--------|
| `-mode` | 运行模式：binary/shellcode/webshell | 必填 |
| `-input` | 输入文件路径 | 必填 |
| `-output` | 输出文件路径 | 必填 |
| `-method` | 加密方法：xor/aes/rc4/chacha20 | xor |
| `-key` | 加密密钥（可选，自动生成） | 随机生成 |
| `-anti-debug` | 启用反调试 | true |
| `-anti-vm` | 启用反虚拟机 | true |
| `-anti-sandbox` | 启用反沙箱 | true |
| `-obfuscate` | 启用代码混淆 | true |

## 加密算法

### XOR
- 简单快速
- 适合快速测试
- 安全性较低

### AES-GCM
- 高安全性
- 认证加密
- 推荐用于生产环境

### RC4
- 流加密
- 速度快
- 兼容性好

### ChaCha20-Poly1305
- 现代加密算法
- 高性能
- 高安全性

## 对抗技术详解

### 反调试
- IsDebuggerPresent 检测
- CheckRemoteDebuggerPresent 检测
- 时间检测（GetTickCount）
- 异常处理检测

### 反虚拟机
- 虚拟机进程检测（VMware、VirtualBox、QEMU）
- 注册表特征检测
- MAC地址检测
- CPU核心数检测

### 反沙箱
- 时间加速检测
- 低资源配置检测
- 用户活动检测
- 沙箱特征文件检测
- 随机延迟执行

## Webshell 混淆方法

### PHP
- `base64`: Base64编码混淆
- `rot13`: ROT13编码混淆
- `variable`: 变量函数混淆
- `callback`: 回调函数混淆

### ASP
- Base64编码 + Execute执行

### JSP
- Base64编码 + 反射执行

## 项目结构

```
ZREBypass/
├── main.go              # 主程序入口
├── bypass/              # 对抗技术模块
│   ├── anti_debug.go    # 反调试
│   ├── anti_vm.go       # 反虚拟机
│   ├── anti_sandbox.go  # 反沙箱
│   └── options.go       # 配置选项
├── encoder/             # 加密编码模块
│   ├── crypto.go        # 加密算法
│   └── webshell.go      # Webshell混淆
└── loader/              # 加载器生成模块
    ├── binary_loader.go    # 二进制加载器
    └── shellcode_loader.go # Shellcode加载器
```

## 注意事项

⚠️ **免责声明**

本工具仅供安全研究和教育目的使用。使用本工具进行任何非法活动均与作者无关，使用者需自行承担法律责任。

- 请在合法授权的环境中使用
- 不得用于非法入侵或破坏
- 遵守当地法律法规


## 开发计划

- [ ] 支持更多加密算法
- [ ] 增强代码混淆能力
- [ ] 支持内存加载
- [ ] 添加进程注入功能
- [ ] 支持更多Webshell语言
- [ ] GUI界面

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License

## 联系方式

- GitHub: https://github.com/1276486/ZREBypass
