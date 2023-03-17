
## 什么是Shardeum?

Shardeum 是基于 EVM 的 L1，它使用动态分片来实现线性可扩展性，同时实现跨分片的原子可组合性。这意味着 Shardeum 可以通过将每个验证器添加到网络来增加其 TPS 容量，以永远保持低费用。Shardeum 提供了任何基于 EVM 的 L1 的最高吞吐量，而不会牺牲去中心化。开发人员可以部署 Solidity 或 Vyper 合约并与之交互，而无需特别考虑分片，因为合约会自动部署到唯一的分片，同时保留所有分片的原子可组合性。视频地址："https://drive.google.com/file/d/1mSSuEuqU1JnKAXU8Omy-WpBEV5Q_Uf08/preview"

---

## 什么是EVM?

EVM 是以太坊虚拟机的简称。让我们从简单的语言开始介绍虚拟机。虚拟机的目的是虚拟化主机或服务器的版本（如客户端 API），并在软件程序和自动化的帮助下在全球多个（最终用户）系统上部署该版本。在 Web 1.0 和 Web 2.0 中，软件程序通常由中央机构的开发人员安装和维护以供专有使用。

现在让我们将以太坊网络纳入其中。借助 Web 3.0 中的 EVM，开源区块链用于借助网络协议处理跨多个系统的服务器虚拟化。该技术主要由网络上不相关的节点操作和维护，从而导致高度分散。此外，EVM 得到进一步开发，可以通过其“智能合约”以前所未有的自动化水平执行和执行计算功能的任何逻辑步骤。

我们现在有一个状态机，它以令人难以置信的自动化水平跨多个系统虚拟化服务器和数千个应用程序的接口。因此，实际上，您在以太坊看到的不仅仅是一个保存账户和余额数据的去中心化分类账，还有它存储大量可扩展应用程序和位于其之上的其他 Web 3.0 商业服务的完整状态数据的能力.

## Shardeum 与 EVM 兼容

如果您是以太坊或基于以太坊的开发人员之一，请注意 Shardeum 与 EVM 兼容。您无需更改应用程序代码即可启动您在 Shardeum 上构建的各种 dApp。任何为在 EVM 中运行而编写的智能合约都可以轻松移植到 Shardeum 网络。您只需要在 Shardeum 上部署一个用 Solidity 或 Vyper 编写的智能合约，您将再也不用担心 gas 费用上涨。
视频地址："https://www.youtube.com/embed/XTlT3I-Iy5o?autoplay=0&mute=0"

---


## Shardeum操作码

块在 Shardeum 中的工作方式不同，因为交易是单独处理的，而不是分组到块中。但是，仍然需要以特定的时间间隔生成块来支持现有的智能合约，这些智能合约使用与块相关的操作码并符合 JSON RPC 规范。

Shardeum 使用称为周期的生命周期来安排验证器轮换和许多其他操作。例如，一个循环可能需要 60 秒，为每个循环生成一个循环记录。在 Shardeum 中，块号与循环生产率相关联。Shardeum 决定每个周期生成 10 个区块。如果循环持续时间为 60 秒，则每 6 秒生成一个新块，每个循环产生 10 个块。

事务的时间戳通过确定性地将时间戳映射到块号来选择合适的块。如果注入的交易没有时间戳，网络将为交易确定时间戳并选择正确的块。区块信息将与交易参数一起输入 EVM。

Shardeum 公开了与区块相关的公共 API 端点，因此 JSON RPC 服务器可以使用与网络相同的区块信息。

## Block Related Opcodes

| **Stack** 	| **Name**   	| **Supported** 	| **Notes**                                                                                                                        	|
|-----------	|------------	|---------------	|----------------------------------------------------------------------------------------------------------------------------------	|
| 40        	| BLOCKHASH  	| Supported     	| Hash of the specific block, only valid for the 256 most recent blocks, excluding the current one                                 	|
| 41        	| COINBASE   	| Supported     	| Return network account address because there is no block miner in Shardeum                                                       	|
| 42        	| TIMESTAMP  	| Supported     	| Return network account address because there is no block miner in Shardeum                                                       	|
| 43        	| NUMBER     	| Supported     	| Current block's number                                                                                                           	|
| 44        	| DIFFICULTY 	| Supported     	| Current block's difficulty. Since Shardeum does not use Proof of Work for transaction consensus the difficulty value is set to 0 	|
| 45        	| GASLIMIT   	| Supported     	| Current block's gas limit                                                                                                        	|
| 46        	| CHAINID    	| Supported     	| Current network's chain id: 8080                                                                                                 	|
| 48        	| BASEFEE    	| EIP-1559      	| London hardfork, EIP-3198: Current block's base fee                                                                              	|
---

## 部署


### 最低硬件要求

```
-250 GB SSD storage
-Quad core CPU less than 10 years old if self hosting
-Dual core CPU works if hosted with newer Xeons / EPYC
-16 GB of ram,  4+ GB of virtual memory recommended
-Hosting: 8 GB RAM + 8 GB Virtual Memory
```

## 怎样在Shardeum上运行验证机?

## 第一步: 安装


### 安装包

我们将在本教程中使用 curl 来下载文件：


<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>
    Linux：
    
```shell
sudo apt-get install curl
```

  </TabItem>
  <TabItem value="mac" label="Mac" default>
    MacOS：

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
    
将 Homebrew 添加到您的 PATH(MacOS):
    
```shell
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"'
eval "$(/opt/homebrew/bin/brew shellenv)"
```

  </TabItem>

</Tabs>

### 更新工具包

首先确保您的工具是最新的：:


<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>
    Linux：

```shell
sudo apt update
```

  </TabItem>
  <TabItem value="mac" label="Mac" default>
    MacOS:

```shell
brew update
```

  </TabItem>

</Tabs>

### 安装docker

安装 docker.io:

<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>
    Linux：

```shell
sudo apt install docker.io
```

  </TabItem>
  <TabItem value="mac" label="Mac" default>
    MacOS：

```shell
brew install docker
```

  </TabItem>

</Tabs>

检查docker是否正在使用（应返回版本20.10.12或更高版本）:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
docker --version
```

  </TabItem>

</Tabs>

### 安装docker-compose

用Curl下载docker-compose:

<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>
    Linux：

```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

  </TabItem>
  <TabItem value="mac" label="Mac" default>
    MacOS:

```shell
brew install docker-compose
```

   </TabItem>
</Tabs>

为docker-compose设置可执行权限:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
sudo chmod +x /usr/local/bin/docker-compose
```

  </TabItem>
</Tabs>

检查docker-compose是否正在使用:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
docker-compose --version
```

  </TabItem>
</Tabs>


## 第二步：下载安装验证器

运行:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
curl -O https://gitlab.com/shardeum/validator/dashboard/-/raw/main/installer.sh && chmod +x installer.sh && ./installer.sh
```

  </TabItem>
</Tabs>

终端将询问有关您的设置设置的问题。

授予收集验证器数据以报告错误的权限：

```shell
By running this installer, you agree to allow the Shardeum team to collect this data. (y/n)?:
```

输入y进入Web的仪表板：

```shell
Do you want to run the web based Dashboard? (y/n): y
```
设置仪表板访问密码：

```shell
Set the password to access the Dashboard:
```

直接按Enter进入端口8080：

```shell
Enter the port (1025-65536) to access the web based Dashboard (default 8080): 你的密码
```

设置第一个p2p端口(默认9001)：

```shell
此处按Enter键即可
```

设置第二个p2p端口(默认10001)：

```shell
此处按Enter键即可
```

添加自定义路径或安装到根目录：

```shell
此处按Enter键即可
```

等待安装完成。

- 如果您在路由器后面并且您使用端口 9001 和 10001 进行 p2p 通信，请确保转发端口 9001 和 10001（小心这样做，因为它会修改您的防火墙）https://www.noip.com/support/knowledgebase/general-port-forwarding-guide/

参考:

https://gitlab.com/shardeum/validator/dashboard/


## 第三步：打开validator客户端：

确保您在根路径：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd 
```

  </TabItem>
</Tabs>

进入到.Shardeum隐藏文件夹:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd .shardeum
```

  </TabItem>
</Tabs>

通过运行以下shell脚本启动Cli：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
./shell.sh
```

  </TabItem>
</Tabs>





## 第四步： 打开validator GUI

在shell脚本中运行:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui start
```

  </TabItem>
</Tabs>

打开你的浏览器访问:

<Tabs groupId="validator-local-or-server">
  <TabItem value="local" label="Local" default>
    本地：

```shell
https://localhost:8080/
```

  </TabItem>
  <TabItem value="server" label="Server" default>
    远程服务器：

```shell
https://<server_ip>:8080/
```

  </TabItem>
</Tabs>


尝试在 Web 浏览器中访问此地址时，您可能会看到一个警告页面。忽略此警告并继续访问验证器仪表板。解决此警告的另一种方法：

<Tabs>
  <TabItem value="firefox" label="Firefox" default>
    火狐浏览器：

```
From the three bar button (hamburger) menu button, go to Settings

Click on “Privacy & Security” on the left.

Scroll down to locate “View Certificates” and click that button.

Click the “Servers” tab, then click “Add Exception”.

Type: “https://localhost:8080” (or your remote/VPS server’s IP and port),
then click “Get Certificate”, then click “Confirm Security Exception”.

The result should be the server/localhost in the list, click “OK”.

Refresh the operator dashboard page and the certificate error should be gone.
```

  </TabItem>
  <TabItem value="chrome" label="Chrome" default>
    谷歌浏览器：

```
Click on the “Not secure” alert and select/click on “Certificate is not valid”.

Click on the “Details” tab, then click n “localhost” in the “Certificate Hierarchy” box and click the “Export” button.

Click on the “Details” tab, then click on
“mynode-sphinx.shardeum.local” in the “Certificate Hierarchy” box and click the “Export” button.

The result of the steps above are two certificate files save in a location to be used in the following steps.

Type: chrome://settings in address bar, hit enter.

Click on “Privacy and security” on the left menu. Then click “Security” from the list in the main window.

Scroll down to find “Manage device certificates” in the main windows and select it.

Click the “Import” button.

Follow the import prompts.

Place the ‘mynode-sphinx.shardeum.local.crt” in the “Trusted Root Cert… Auth..” folder.

Click “Yes” and then “OK”.

Click “Import” once more.

Then follow the import prompts.

Place the ‘localhost.crt” in the “Personal” folder.

Close all Chrome windows (as in Exit Chrome).

When you have successfully restarted chrome, the operator dashboard will not show with a white lock.
```

  </TabItem>

</Tabs>


### 系统会要求您提供在安装过程中设置的密码。

![loginPage.jpg](	https://docs.shardeum.org/assets/images/loginPage-b0c8345bbfd71249dde4ace04fe4dd4d.jpg)

:::danger
### 注意：如果您在设置过程中没有输入密码，登录也会失败。在验证器 CLI 中设置新密码：
在validator CLI中设置密码:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui set password <你的密码>
```

  </TabItem>
</Tabs>

:::

你应该会在 Web 浏览器中看到 Shardeum 验证器仪表板的“概述”页面：


![overviewBetanet.jpg](	https://docs.shardeum.org/assets/images/overviewBetanet-ab6f21beccb631a1fb4a82930b95b102.jpg)

## 第五步：启动

进入“Maintenance”页面,然后点击左上角白框的“Start Node”按钮：

![startBetanet.jpg](https://docs.shardeum.org/assets/images/startBetanet-30512f936b2c976db151e6aea9361704.jpg)

(运行界面像这样)

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli start
```

  </TabItem>
</Tabs>

等待并刷新页面。

如果“Start Node”按钮现在显示为“Stop Node”，则节点运行正常。如果要使用CLI停止节点：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli stop
```

  </TabItem>
</Tabs>

![startedBetanet.jpg](https://docs.shardeum.org/assets/images/startedBetanet-d4270a56e8d10fa33e85947984929a3b.jpg)

## 第六步：监控validator

去“Performance”页面查看节点的硬件性能:

![performanceBetanet.jpg](https://docs.shardeum.org/assets/images/startedBetanet-d4270a56e8d10fa33e85947984929a3b.jpg)

有关节点状态的更多详细信息，请在CLI中运行以下命令：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli status
```

  </TabItem>
</Tabs>

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
pm2 list
```

  </TabItem>
</Tabs>

通过运行以下命令从列表中重置validator:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
pm2 delete [id]
```

  </TabItem>
</Tabs>

## 第七步：把你的钱包连接到Betanet

[Connect to Sphinx 1.X with your wallet by clicking the button linked here](/Network/Endpoints#connect-wallet)

## 第八步：从Betanet领水

[Shardeum Twitter SHM Faucet Guide for Sphinx 1.X](/Faucet/Claim#shardeum-faucet-website)

## 第九步：在validator中质押SHM

### GUI

启动验证器后，转到“设置”页面。你将被要求连接你的钱包：

![connectWalletBetanet.jpg](https://docs.shardeum.org/assets/images/connectWalletBetanet-e844c33bd3f4aecae772648f1602a5c5.jpg)

连接上钱包后，你会看到这个：

![connectedWalletOptions.jpg](https://docs.shardeum.org/assets/images/connectedWalletOptions-e908b5e2929d1c594b87ccee93b0e1c2.jpg)

添加质押时, 你会看到这个:

![connectedWalletAddStake.jpg](https://docs.shardeum.org/assets/images/connectedWalletAddStake-bc1b9ab8875adcf3ca54a52f432dd4d4.jpg)

```
-Stake Wallet Address [wallet connected]
-Nominee Public Key [filled in automatically while validator is running]
-Stake amount (SHM) [empty and is in units ether not wei]
```

本例填写了10个SHM代币进行质押。

*建议每个validator节点仅质押10个SHM，因为为validator质押10个或更多SHM的奖励相同*


 填写完所有字段后，单击“质押”按钮。

你的钱包会要求你签署你的 SHM 交易股份。

交易签署并完成后，您就成功抵押了您的 SHM 代币。
  

 *如果您之前已经抵押，您可以“移除抵押”。但是，当您取消质押时，您将停止获得测试网 SHM 奖励*。

  
  
如果您看到您的验证器 IP 地址为“0.0.0.0”：

进入docker操作面板（如果您自定义安装位置，可能会有所不同）：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd ~/.shardeum
./shell.sh
```

  </TabItem>

</Tabs>

获取节点的外部IP：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
curl https://ipinfo.io/ip
```

  </TabItem>

</Tabs>

返回的IP格式为xxx.xxx.xxx.xxx就是你的EXTERNAL_IP。

设置上面的数字代替 EXTERNAL_IP：

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
export APP_IP="EXTERNAL_IP"
```

  </TabItem>

</Tabs>


### CLI

如果您无法访问Validator GUI的Web浏览器，您也可以从Validator CLI抵押和取消抵押。

首先，在您的Validator CLI中设置您的私钥：

---
*小心使用您的私钥。我们建议您使用仅包含测试网令牌的私钥以确保安全*。
---
```shell
export PRIV_KEY=<private_key>
```

make sure your private key is stored in your Validator CLI by running:

```shell
echo $PRIV_KEY
```

add stake with:

```shell
operator-cli stake 10
```

check your stake amount with:

```shell
operator-cli stake_info <wallet_address>
```

remove stake with:

```shell
operator-cli unstake
```

## Validator

### Version

:::warning
New validator versions will be released over time. 
It is necessary to keep your validator updated 
by checking the minimum version required and your current version periodically.
:::

Run:

<Tabs groupId="validator-local-or-server">
  <TabItem value="local" label="Local" default>

```shell
curl localhost:9001/nodeinfo
```

  </TabItem>
  <TabItem value="server" label="Server" default>

```shell
curl <server_ip>:9001/nodeinfo
```

  </TabItem>
</Tabs>

### Update

Run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd
cd .shardeum
./update.sh
```

  </TabItem>
</Tabs>

:::caution
You might manually have to start the GUI afterwards with:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui start
```

  </TabItem>
</Tabs>

:::

### Exit Error Logs

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
sudo docker exec shardeum-dashboard cat cli/build/logs/exit-summary.json
```

  </TabItem>
  <TabItem value="CLI" label="CLI" default>

Navigate to the .shardeum directory by entering:
```shell
cd .shardeum
```
Execute the shell.sh script by entering: 
```shell
./shell.sh
```
With the Validator CLI running, navigate to the cli/build/logs directory by entering:
```shell
cd cli/build/logs
```
View the contents of the exit-summary.json file by entering:
```shell
cat exit-summary.json
```

  </TabItem>
</Tabs>

## CLI And GUI

### Version

Run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli version
```

  </TabItem>

</Tabs>


### Update

Run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli update
```

  </TabItem>
</Tabs>

### Commands

To see all CLI commands, run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli help
```

  </TabItem>
</Tabs>

## Uninstall Validator

Useful if your validator is outdated and you want to clean your last installation.

You can delete the validator folder while in your root directory with:

```shell
rm -rf .shardeum
```

You can also delete docker containers and images that the Shardeum validator was using.

:::danger
These commands will delete all docker images and containers on your computer!

Delete all docker containers:

```shell
docker rm -vf $(docker ps -aq)
```

Delete all docker images:

```shell
docker rmi -f $(docker images -aq)
```

:::
