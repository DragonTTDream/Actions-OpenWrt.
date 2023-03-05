# 感谢
- 源码来源1： Lean 的 Openwrt 源码仓库 https://github.com/coolsnowwolf/lede
- 源码来源2： 天灵的源码仓库 https://github.com/1715173329/imoutowrt
- 脚本来源： P3TERX 的 使用 GitHub Actions 云编译 OpenWrt https://github.com/P3TERX/Actions-OpenWrt
- 打包脚本： Flippy 的 OpenWrt 打包脚本 Actions https://github.com/ophub/flippy-openwrt-actions
- 参考学习来源：
- huangqian8 https://github.com/huangqian8/Cloud-N1-OpenWrt
- breakings https://github.com/breakings/OpenWrt

----------------------------
- 发现的问题：breakings的DIY脚本内使用了 `$GITHUB_WORKSPACE` 变量，因此如果不克隆相应的代码将会编译失败
- 修改DIY脚本中的 `$GITHUB_WORKSPACE` 为 `$(pwd)`
- 克隆 `breakings/OpenWrt/trunk/general` 目录 `svn export https://github.com/breakings/OpenWrt/trunk/general`
- 修改后的文件保存为 `My_local_DIY.sh`
----------------------------
- 仓库内的DIY1、DIY2、feeds.conf.default、huge.config均克隆自breakings仓库
----------------------------
#### .github/workflows为学习实验留下
- UPLOAD_config.yml仅用于复制出config
- 建议使用less的语法：less 文件名，通过【pageup】和【pagedown】键进行前翻页和后翻页复制出自定义的config文件
- 其余Actions均为设计编译出N1的openwrt固件，可靠性：实验状态
----------------------------

**English** | [中文](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

# Actions-OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

A template for building OpenWrt with GitHub Actions

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository.
- Select `Build OpenWrt` on the Actions page.
- Click the `Run workflow` button.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

## Tips

- It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).
- Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Credits

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [ActionsRML/delete-workflow-runs](https://github.com/ActionsRML/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © [**P3TERX**](https://p3terx.com)
