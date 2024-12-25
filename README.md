# BLUE DEX CLMM 套利程序

## 运行环境&部署

本机环境需要安装

1. 安装`node.js` [>安装Node链接](https://nodejs.org/zh-cn/download/package-manager)
2. 执行`npm install -g typescript`

## 启动方式

必须先配置好配置文件，在项目路径下新建一个文件`.env`示例文件如下：

```.dotenv

# 钱包私钥 需要替换
PRIVATE_KEY="你的私钥"

# Sui节点URL，替换成你的，这里仅测试
ENDPPOINT="https://fullnode.mainnet.sui.io:443"

# 目标交易POLL地址，这里举例DEEP/BLUE
POOL_ID="0x4b8271fc4819078e44ee9a0506a824b77464789d57ace355d0562a4776c51840"

# 默认偏移量,即在计算区间之上再加上G作为最终目标区间，设置为0即可，波动大换成其他正整数
G=0
```

配置文件完成后，你需要在你的钱包中充值一部分资产，具体跟你选择的Pool有关，比如DEEP/BLUE，那么你需要至少任意一种资产（DEEP或者BLUE）不小于0。

- 使用Makefile文件启动

```shell
make start
```

- 或者使用node

```shell
npm install && tsc && node dist/index.js
```

## 策略说明

最简单的策略，自动跟随价格波动进行开仓和平仓，纯粹依赖奖励，当奖励占比小于手续费占比时，就不要再使用了。

- 默认最小区间为极限
- 默认资金使用率90%
- 其他辅助逻辑一律不要了

## 更新说明
1、越是简单的东西越稳定
2、选择Dex和Pool比策略更加重要
3、程序先跑起来，后面的事后面再说。
