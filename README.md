# LED 弹幕灯牌

[![HarmonyOS NEXT](https://img.shields.io/badge/HarmonyOS-NEXT-000000?logo=harmonyos)](https://developer.harmonyos.com/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/shippingzhou/HarmonyOS_hos_led?style=social)](https://github.com/shippingzhou/HarmonyOS_hos_led)

**把手机屏幕变成可自定义的 LED 灯牌**，文字水平/垂直滚动，背景色和字体色自由搭配，内置多首背景音乐，所有配置本地存储，无需任何权限。

## ✨ 功能特性

- **文字滚动**：支持水平 / 垂直两种滚动方向，滚动速度可调
- **个性定制**：自由搭配背景色、字体颜色、文字大小
- **内置 BGM**：4 首背景音乐，使用 `AVPlayer` 播放 rawfile 中的音频（`fdSrc` 方式）
- **配置持久化**：文字内容、颜色、速度、历史记录全部通过 `preferences` 存储，JSON 序列化
- **历史收藏**：可保存多个灯牌配置，一键切换
- **0 权限申请**：纯本地应用，无需网络、存储、蓝牙等任何权限

## 📸 应用预览

> 
<img width="400" height="400" alt="reehole" src="https://github.com/user-attachments/assets/cc9f3c5b-e9f7-4393-85dd-054caaee8d86" />
<img width="400" height="400" alt="nspirationdrawer" src="https://github.com/user-attachments/assets/c89d82d0-a078-4ce9-a7cd-e6ba2f6b815c" />
<img width="400" height="400" alt="led" src="https://github.com/user-attachments/assets/27c3378e-ca81-4f1a-aac6-2bcb88b5271a" />


## 🛠️ 技术实现

- **开发语言**：ArkTS
- **UI 框架**：全部使用 `@kit.ArkUI`（声明式开发范式）
- **滚动核心**：基于 `Marquee` 组件，通过递增 `key` 强制重渲染实现滚动控制
- **音频播放**：`AVPlayer` + `rawfile` + `fdSrc` 文件描述符方式
- **数据存储**：`@ohos.data.preferences`（首选项），JSON 序列化存储历史记录列表
- **设置面板**：使用 `bindSheet` 弹出式面板，不跳转额外页面

## 📁 项目结构

<pre><code>```text LED/
├── AppScope/ # 应用全局配置
│ ├── app.json5
│ └── resources/ # 全局资源（图标、字符串等）
├── entry/ # 主模块
│ ├── src/
│ │ ├── main/
│ │ │ ├── ets/
│ │ │ │ ├── Common/ # 公共工具类（日志、偏好存储、全局数据）
│ │ │ │ ├── entryability/ # 应用入口 Ability
│ │ │ │ ├── entrybackupability/ # 备份能力（如有）
│ │ │ │ └── pages/ # 页面
│ │ │ │ ├── Index.ets # 主界面（弹幕灯牌核心）
│ │ │ │ ├── MyPage.ets # 我的页面（历史记录/收藏）
│ │ │ │ ├── NewLEDPage.ets # 新建/编辑灯牌页面
│ │ │ │ └── PrivacyPage.ets # 隐私政策（如需）
│ │ │ └── resources/ # 模块资源
│ │ │ ├── base/ # 基础资源（颜色、字符串、图片）
│ │ │ └── rawfile/ # 原始文件（内置 BGM 音频文件）
│ │ ├── mock/ # 本地模拟数据（如有）
│ │ ├── ohosTest/ # 鸿蒙测试用例
│ │ └── test/ # 单元测试
│ ├── build-profile.json5 # 模块构建配置
│ ├── oh-package.json5 # 模块依赖
│ └── obfuscation-rules.txt # 代码混淆规则
├── hvigor/ # 构建工具配置
├── build-profile.json5 # 项目级构建配置
├── hvigorfile.ts # 项目级构建脚本
├── oh-package.json5 # 项目依赖配置
├── oh-package-lock.json5 # 依赖锁定文件
├── code-linter.json5 # 代码检查配置
└── local.properties # 本地 SDK 路径（已忽略提交） ```</code></pre>




## ⚙️ 环境要求

- **DevEco Studio**：5.0.0 Release 或更高版本
- **HarmonyOS SDK**：API 12 或更高版本（HarmonyOS NEXT）
- **设备**：搭载 HarmonyOS NEXT 的真机或模拟器

## 🚀 安装与运行

1. 克隆仓库到本地：
   ```bash
   git clone https://github.com/shippingzhou/HarmonyOS_hos_led.git


   使用 DevEco Studio 打开项目。
等待项目同步和依赖下载完成。
连接鸿蒙设备或开启模拟器，点击运行按钮 Run 'entry'。


📖 使用说明

主界面：输入文字内容，调整背景色、字体色、滚动速度、滚动方向。
预览效果：文字会实时在屏幕上滚动，模拟 LED 灯牌效果。
保存配置：点击保存按钮，当前灯牌配置会存入历史记录。
历史记录：在“我的”页面可查看所有保存的灯牌，点击即可加载。
背景音乐：点击音乐图标可播放/切换内置 BGM，再次点击停止。


🤝 贡献指南

欢迎提出 Issue 或 Pull Request 来帮助改进项目。

Fork 本仓库
新建分支 git checkout -b feature/你的功能
提交更改 git commit -m 'Add some feature'
推送到分支 git push origin feature/你的功能
创建 Pull Request
📜 许可证

本项目基于 MIT 许可证开源，详情见 LICENSE 文件。

🙏 鸣谢

HarmonyOS NEXT 提供开发平台
音频素材来自 Pixabay 等免费版权网站


