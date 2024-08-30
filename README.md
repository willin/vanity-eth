# Vanity-ETH

[![构建状态](https://flat.badgen.net/github/checks/willin/vanity-eth?label=build)](https://github.com/willin/vanity-eth/actions/workflows/deploy.yml?query=branch%3Amaster)
[![许可证](https://flat.badgen.net/badge/license/MIT/cyan)](https://raw.githubusercontent.com/bokub/vanity-eth/master/LICENSE)

基于浏览器的 ETH 靓号地址生成器

只需输入 [`vanity-eth.js.cool`](https://vanity-eth.js.cool) 即可使用 ⚡️

[![Vanity-ETH](https://i.imgur.com/zmSLeBP.png)](https://vanity-eth.js.cool)

## 什么是虚荣地址？

虚荣地址是您可以选择其中一部分使其看起来不那么随机的地址。

示例：

-   `0xc0ffee254729296a45a3885639AC7E10F9d54979`
-   `0x999999cf1046e68e36E1aA2E0E07105eDDD1f08E`

## 使用方法

首先，访问 [`vanity-eth.js.cool`](https://vanity-eth.js.cool)

输入您选择的短前缀和/或后缀，然后点击 _生成_ 开始。您的浏览器将生成大量随机地址，直到找到一个与您的输入匹配的地址。

一旦找到地址，您可以选择显示私钥或点击 _保存_ 按钮下载一个密码加密的密钥库文件。

根据您的计算机能力，调整工作线程的数量可以增加或减少速度。

## 安全性

如前所述，所有计算仅在您的浏览器中进行。没有任何数据会离开您的机器，甚至是您的浏览器标签页。没有数据库，没有服务器端代码。所有内容在您关闭浏览器标签页时消失。

**Vanity-ETH 不能也永远不会存储您的私钥。** 如果您对其可信度有疑虑，您有三种选择来确保您的密钥隐私：

-   加载网页后，您可以断开互联网连接并继续无缝使用它
-   或者，您可以下载 Vanity-ETH 的最新构建版本 [这里](https://git.io/veth-dl) 并在离线计算机上使用
-   代码是 100% 开源的，可以在 GitHub 上查看，允许您在使用前彻底审查它。

Vanity-ETH 使用加密安全的伪随机数生成器 (CSPRNG) 生成以太坊地址。

密钥库文件使用 AES-128-CTR 密码通过 PBKDF2-SHA256 派生函数进行加密，具有 65536 次哈希轮次。

## 性能

Vanity-ETH 的性能在不同浏览器之间可能会有显著差异。目前，Chrome 提供了最佳结果。

虽然您可以在手机或平板电脑上使用 Vanity-ETH，但它不太可能达到传统计算机的速度。

**注意：** Vanity-ETH 设计为一个用户友好的工具，直接在您的浏览器中运行，提供无需下载或安装额外软件的便捷性。然而，基于浏览器的工具具有固有的限制，可能会影响其性能和效率。一些专用的命令行工具虽然更难使用，但可能提供更好的性能。

## 兼容性

使用 Vanity-ETH 生成的任何地址都是 ERC-20 兼容的，这意味着您可以将其用于 ICO、空投，或只是从交易所提取资金。

密钥库文件 100% 兼容 MyEtherWallet、MetaMask、Mist 和 geth。

## 从源码构建 Vanity-ETH

使用 Vanity-ETH 生成的任何地址都是 ERC-20 兼容的，这意味着您可以将其用于 ICO、空投，或只是从交易所提取资金。

密钥库文件 100% 兼容 MyEtherWallet、MetaMask、Mist 和 geth。

## 从源码构建 Vanity-ETH

一个 GitHub Action 负责自动构建和部署 Vanity-ETH 到 GitHub Pages 🤖，但如果您愿意，您可以从源码构建自己的版本（您需要 Node.js 16）

```sh
git clone https://github.com/willin/vanity-eth
cd vanity-eth
npm i
npm run build
```

## License

MIT

Author: [Boris K](https://github.com/bokub)
