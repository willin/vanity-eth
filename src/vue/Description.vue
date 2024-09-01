<template>
    <div class="panel">
        <p>
            Vanity-ETH 是一个开源工具，它使用您的网络浏览器生成以太坊靓号地址。<br />
            输入您选择的短前缀和/或后缀，然后点击<i>生成</i>开始。
        </p>
        <div class="shortcut">
            <button type="button" class="button-large" @click="scrollDown">立即开始</button>
        </div>

        <h2>什么是靓号地址？</h2>
        <div class="p">
            靓号地址是您可以选择其中一部分使其看起来不那么随机的地址。<br />
            示例：
            <ul>
                <li>
                    <span class="monospace">0x00005De0Bf4A68318Af6E3F93b1ce36576450000</span> (`0000`前缀`0000`后缀：M1
                    Max，10 线程，加 Ultra 7，22 线程，约一周生成)
                </li>
                <li>
                    <span class="monospace">0x0009892FE190bf00A3387AD2DE4A179cdEF70000</span> (`000`前缀`0000`后缀：M1
                    Max，5 线程，约 3 小时生成)
                </li>
            </ul>
        </div>

        <h2>它是如何工作的</h2>
        <p>
            输入您选择的短前缀和/或后缀，然后点击<i>生成</i>开始。您的浏览器将生成大量随机地址，直到找到一个与您的输入匹配的地址。<br />
            一旦找到地址，您可以选择显示私钥或点击<i>保存</i>按钮下载一个密码加密的密钥库文件。<br /><br />
            根据您的计算机能力，调整工作线程的数量可以增加或减少速度。<br />
        </p>
        <h2>安全性</h2>
        <p>
            如前所述，所有计算仅在您的浏览器中进行。没有任何数据会离开您的机器，甚至是您的浏览器标签页。没有数据库，没有服务器端代码。所有内容在您关闭浏览器标签页时消失。<br /><br />
            <b>Vanity-ETH 不能也永远不会存储您的私钥。</b>
            如果您对其可信度有疑虑，您有三种选择来确保您的密钥隐私：<br />
            &nbsp;-&nbsp;加载网页后，您可以断开互联网连接并继续无缝使用它<br />
            &nbsp;-&nbsp;或者，您可以下载 Vanity-ETH 的最新构建版本
            <a href="https://github.com/willin/vanity-eth/archive/refs/heads/offline.zip" target="_blank">这里</a
            >并在离线计算机上使用<br />
            &nbsp;-&nbsp;代码是 100% 开源的，可以在
            <a href="https://github.com/willin/vanity-eth" target="_blank">GitHub</a
            >上查看，允许您在使用前彻底审查它<br />
            <br />
            Vanity-ETH 使用加密安全的伪随机数生成器 (CSPRNG) 生成以太坊地址。<br />
            密钥库文件使用 AES-128-CTR 密码通过 PBKDF2-SHA256 派生函数进行加密，具有 65536 次哈希轮次。
        </p>
        <h2>性能</h2>
        <p>
            Vanity-ETH 的性能在不同浏览器之间可能会有显著差异。目前，Chrome 提供了最佳结果。<br />
            虽然您可以在手机或平板电脑上使用 Vanity-ETH，但它不太可能达到传统计算机的速度。<br /><br />
            <b>注意：</b> Vanity-ETH
            设计为一个用户友好的工具，直接在您的浏览器中运行，提供无需下载或安装额外软件的便捷性。<br />
            然而，基于浏览器的工具具有固有的限制，可能会影响其性能和效率。一些专用的命令行工具虽然更难使用，但可能提供更好的性能。
        </p>
        <h2>兼容性</h2>
        <p>
            使用 Vanity-ETH 生成的任何地址都是 ERC-20 兼容的，这意味着您可以将其用于
            ICO、空投，或只是从交易所提取资金。<br />
            密钥库文件 100% 兼容 MyEtherWallet、MetaMask、Mist 和 geth。
        </p>
    </div>
</template>

<script>
    export default {
        data: () => ({
            scrollTimeOut: null,
        }),
        methods: {
            scrollDown() {
                this.scrollTo(document.getElementById('input-panel'), -1);
            },
            scrollTo(element, lastValue) {
                const currentValue = window.scrollY;
                const diff = element.getBoundingClientRect().top / 6;
                if (Math.abs(diff) > 1 && currentValue > lastValue) {
                    window.scrollTo(0, window.scrollY + diff);
                    this.scrollTimeOut = setTimeout(this.scrollTo, 30, element, currentValue);
                } else if (currentValue >= lastValue) {
                    document.getElementById('input').focus();
                }
            },
        },
    };
</script>

<style lang="sass" scoped>
    @import "../css/variables"
    p, .p
        margin: 15px 0 20px
        color: $text-alt
        overflow-x: hidden
        text-overflow: ellipsis
        .monospace
            font-family: $monospace-font
            font-size: 0.85em
    .shortcut
        text-align: center
        .button-large
            width: 150px
            margin: 15px 0 35px
</style>
