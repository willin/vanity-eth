<template>
    <div class="panel">
        <p v-if="error === 'workers_unsupported'">
            您的浏览器不支持多线程计算。<br />
            请使用其他浏览器。
        </p>

        <div v-if="error === 'insecure_location'">
            <h3>安全警告</h3>

            您正在从未知网站使用 Vanity-ETH，这可能会窃取您的私钥。<br />
            为了安全起见，请在 <a href="https://vanity-eth.js.cool" target="_blank">vanity-eth.js.cool</a> 上使用
            Vanity-ETH，或 下载最新版本
            <a href="https://github.com/willin/vanity-eth/archive/refs/heads/offline.zip" target="_blank">这里</a>
            离线使用。
        </div>
        <p v-else v-html="error.replace('\n', '<br>')"></p>
    </div>
</template>

<script>
    export default {
        props: {
            error: {
                type: String,
                required: true,
            },
        },
    };
</script>

<style lang="sass" scoped>
    @import "../css/variables"
    .panel
        background-color: $error
        color: $text-opposite
        a, a:visited, a:hover
            text-decoration: underline
            color: $text-opposite
</style>
