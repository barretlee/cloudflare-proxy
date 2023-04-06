# cloudflare-proxy

> 好多调用 ChatGPT 的客户端都是直接使用的 api.openai.com，这个接口很显然是访问不通的，好在有些良心作者还提供了一个自定义 API 域名的入口，在 Cloudflare Worker 上写了一个简单的代理，用起来顺手多了，省得我一直在本机挂全局代理。—— [Barret李靖](https://twitter.com/Barret_China/status/1642725620798087168)

<img src="https://user-images.githubusercontent.com/2698003/229402093-8e4f55e8-95e5-4adc-92dd-2fb6bfacce42.png" width="800" />


代理请求到 ChatGPT API，代码部署步骤：

1. 注册并登录到 Cloudflare 账户
2. 创建一个新的 Cloudflare Worker
3. 将 [cloudflare-worker.js](./cloudflare-worker.js) 复制并粘贴到 Cloudflare Worker 编辑器中
4. 保存并部署 Cloudflare Worker
5. 在 Worker 详情页 -> Trigger -> Custom Domains 中为这个 Worker 添加一个自定义域名

为啥需要第五步？因为直接使用 Cloudflare 的域名，依然无法访问。

<img src="https://user-images.githubusercontent.com/2698003/229402115-f7463a82-dd03-45e1-820c-1ab29acf1048.png" width="400" />

### 使用说明

ChatGPT 的 API 默认是非流式输出的，如果想让他变成流式输出，需要将 `payload.stream` 设置为 true，大部分的客户端都已经加上了这个参数。

https://github.com/barretlee/cloudflare-proxy/blob/a7cf8ecfd3eed5c4d76f82f4f4387ed4ef39c6f3/cloudflare-worker.js#L36-L50

### License

[MIT](./LICENSE)
