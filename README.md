<h1 align="center">Build-your-own-kernel</h1>

<p align="center">
  <b>基于 GKI 的 SukiSU Ultra 内核</b><br>
  <sub>参考大佬成果并在其基础上优化，自用内核工程</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/github/license/Celestials316/Build-your-own-kernel?style=flat-square">
  <img src="https://img.shields.io/github/stars/Celestials316/Build-your-own-kernel?style=social">
</p>

---

## ✨ 项目介绍

本项目是一个基于 **GKI 架构 + KernelSU（SukiSU Ultra 分支）** 的定制内核工程。  
参考了多位大佬的公开项目并结合实际需求进行了修改与整合，最终形成了当前的自用内核构建环境。

---

## ⚙️ 特性一览

- 支持构建kernelsu的分支 **SukiSU Ultra**
- 可选启用 **SUSFS** (susfs4ksu) 功能增强隐藏能力
- 支持 GitHub Actions 云端自动构建
- 精简 defconfig，删除多余模块
- 可通过 AnyKernel3 封装快速刷入
- **支持手动启用自定义内核配置** - 通过逗号分隔的方式指定额外的 CONFIG 选项

---

## 📦 使用方法

### 1. 克隆仓库

```bash
git clone https://github.com/Celestials316/Build-your-own-kernel.git
```
### 2. 使用 GitHub Actions 编译并刷入

#### 2.1 触发工作流
在 GitHub 仓库页面，进入 **Actions** 标签，选择 **A内核编译** 工作流，点击 **Run workflow** 按钮。

#### 2.2 配置构建选项
- **选择内核版本**：选择要编译的 Android 内核版本
- **选择SukiSU功能分支**：Stable 或 Dev 分支
- **自定义内核内部版本后缀**：可选，留空则自动生成
- **启用额外ZRAM算法**：默认启用
- **启用KPM功能**：默认关闭
- **启用SUSFS功能**：默认启用
- **手动启用额外内核配置**：可选，输入逗号分隔的 CONFIG 选项
  - 示例：`CONFIG_PID_NS,CONFIG_USER_NS,CONFIG_IPC_NS`
  - 该功能会自动在 defconfig 中搜索并启用指定配置
  - 如果配置项已存在但被禁用，会自动改为启用
  - 如果配置项不存在，会自动添加

#### 2.3 等待编译完成
工作流会自动编译内核并打包为 AnyKernel3 格式的刷机包。

---

## 🙏 鸣谢 Thanks

- [KernelSU](https://github.com/tiann/KernelSU)
- [SukiSU-Ultra](https://github.com/ShirkNeko/SukiSU-Ultra)
- [susfs4ksu](https://github.com/ShirkNeko/susfs4ksu)
- 各位热心提供内核适配经验的大佬们！
- GitHub Actions 社区编译脚本模板贡献者
