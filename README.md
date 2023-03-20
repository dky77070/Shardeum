
## Shardeum介绍

Shardeum是基于EVM的L1，它使用动态分片来实现线性可扩展性，同时实现跨分片的原子可组合性。这意味着 Shardeum可以通过将每个Validator添加到网络来增加其TPS容量，以永远保持低费用。Shardeum提供了任何基于EVM的L1的最高吞吐量，而不会牺牲去中心化。开发人员可以部署 Solidity 或 Vyper 合约并与之交互，而无需特别考虑分片，因为合约会自动部署到唯一的分片，同时保留所有分片的原子可组合性。视频地址："https://drive.google.com/file/d/1mSSuEuqU1JnKAXU8Omy-WpBEV5Q_Uf08/preview"

---

## EVM介绍

EVM是以太坊虚拟机的简称。让我们从简单的语言开始介绍虚拟机。虚拟机的目的是虚拟化主机或服务器的版本（如客户端 API），并在软件程序和自动化的帮助下在全球多个（最终用户）系统上部署该版本。在Web1.0和Web2.0中，软件程序通常由中央机构的开发人员安装和维护以供专有使用。

现在让我们将以太坊网络纳入其中。借助Web3.0中的EVM，开源区块链用于借助网络协议处理跨多个系统的服务器虚拟化。该技术主要由网络上不相关的节点操作和维护，从而导致高度分散。此外，EVM得到进一步开发，可以通过其“智能合约”以前所未有的自动化水平执行和执行计算功能的任何逻辑步骤。

我们现在有一个状态机，它以令人难以置信的自动化水平跨多个系统虚拟化服务器和数千个应用程序的接口。因此，实际上，您在以太坊看到的不仅仅是一个保存账户和余额数据的去中心化分类账，还有它存储大量可扩展应用程序和位于其之上的其他 Web 3.0 商业服务的完整状态数据的能力.

## Shardeum与EVM兼容

如果您是以太坊或基于以太坊的开发人员之一，请注意Shardeum与EVM兼容。您无需更改应用程序代码即可启动您在Shardeum上构建的各种dApp。任何为在EVM中运行而编写的智能合约都可以轻松移植到Shardeum网络。您只需要在 Shardeum上部署一个用Solidity或Vyper编写的智能合约，您将再也不用担心gas费用上涨。
视频地址："https://www.youtube.com/embed/XTlT3I-Iy5o?autoplay=0&mute=0"

---

## Shardeum操作码

区块在Shardeum中的工作方式不同，因为交易是单独处理的，而不是分组到区块中。但是，仍然需要以特定的时间间隔生成区块来支持现有的智能合约，这些智能合约使用与区块相关的操作码并符合JSON RPC规范。

Shardeum使用称为周期的生命周期来安排Validator轮换和许多其他操作。例如，一个循环可能需要60秒，为每个循环生成一个循环记录。在Shardeum 中，区块号与循环生产率相关联。Shardeum决定每个周期生成10个区块。如果循环持续时间为60秒，则每6秒生成一个新区块，每个循环产生10个区块。

事务的时间戳通过确定性地将时间戳映射到区块号来选择合适的区块。如果注入的交易没有时间戳，网络将为交易确定时间戳并选择正确的区块。区块信息将与交易参数一起输入EVM。

Shardeum公开了与区块相关的公共API端点，因此JSON RPC服务器可以使用与网络相同的区块信息。

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


### 第一步: 安装


我们将在本教程中使用curl来下载文件：


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
    
将Homebrew添加到你的PATH(MacOS):
    
```shell
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"'
eval "$(/opt/homebrew/bin/brew shellenv)"
```

  </TabItem>

</Tabs>

### 更新工具包

首先确保你的下载工具是最新的：


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

### 安装docker容器

<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>
    Linux：

```shell
sudo apt install docker
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

检查docker-compose是否能使用:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
docker-compose --version
```

  </TabItem>
</Tabs>


### 第二步：下载安装Validator


<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
curl -O https://gitlab.com/shardeum/validator/dashboard/-/raw/main/installer.sh && chmod +x installer.sh && ./installer.sh
```

  </TabItem>
</Tabs>

终端将询问有关你的设置设置的问题。

授予收集Validator数据以报告错误的权限：

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


如果你在路由器后面并且使用端口9001和10001进行p2p通信，请确保转发端口9001和10001（请谨慎，因为它会修改防火墙）https://www.noip.com/support/knowledgebase/general-port-forwarding-guide/

参考:

https://gitlab.com/shardeum/validator/dashboard/


### 第三步：打开validator客户端：

确保你在根路径：

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





### 第四步： 打开validator GUI

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
---
###  当你尝试在网络浏览器中访问此地址时，您可能会看到一个警告页面。忽略此警告并继续访问验证器仪表板。解决此警告的另一种方法：
火狐浏览器：
  ```shell
  从三栏按钮（hamburger）菜单按钮，转到设置

单击左侧的“隐私和安全”。

向下滚动以找到“查看证书”并单击该按钮。

单击“服务器”选项卡，然后单击“添加例外”。

输入：“https://localhost:8080”（或您的远程/VPS 服务器的 IP 和端口），
然后单击“获取证书”，然后单击“确认安全异常”。

结果应该是列表中的服务器/本地主机，单击“确定”。

刷新操作员仪表板页面，证书错误应该消失了。
  ```
  
 chrome:
  ```shell
  单击“不安全”警报并选择/单击“证书无效”。

单击“详细信息”选项卡，然后单击“证书层次结构”框中的“本地主机”，然后单击“导出”按钮。

单击“详细信息”选项卡，然后单击
“证书层次结构”框中的“mynode-sphinx.shardeum.local”，然后单击“导出”按钮。

上述步骤的结果是两个证书文件保存在一个位置，将在以下步骤中使用。

在地址栏中输入：chrome://settings，回车。

单击左侧菜单中的“隐私和安全”。 然后从主窗口的列表中单击“安全”。

向下滚动以在主窗口中找到“管理设备证书”并选择它。

单击“导入”按钮。

按照导入提示进行操作。

将“mynode-sphinx.shardeum.local.crt”放在“Trusted Root Cert…Auth..”文件夹中。

单击“是”，然后单击“确定”。

再次单击“导入”。

然后按照导入提示进行操作。

将“localhost.crt”放在“个人”文件夹中。

关闭所有 Chrome 窗口（如退出 Chrome）。

成功重启 chrome 后，操作员仪表板将不会显示为白色锁。
  ```
---
### 系统会要求你提供在安装过程中设置的密码。

![loginPage.jpg](	https://docs.shardeum.org/assets/images/loginPage-b0c8345bbfd71249dde4ace04fe4dd4d.jpg)

```json
如果你在设置过程中没有输入密码，登录也会失败。
```
在validator CLI中设置密码:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui set password <你的密码>
```

  </TabItem>
</Tabs>



你应该会在 Web 浏览器中看到 Shardeum Validator仪表板的“概述”页面：


![overviewBetanet.jpg](	https://docs.shardeum.org/assets/images/overviewBetanet-ab6f21beccb631a1fb4a82930b95b102.jpg)

### 第五步：启动

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

### 第六步：监控validator

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
  
### 第七步：连接钱包/质押
 启动验证器后，转到“设置”页面。你将被要求连接你的钱包：
 ![performanceBetanet.jpg](https://docs.shardeum.org/assets/images/connectWalletBetanet-e844c33bd3f4aecae772648f1602a5c5.jpg)

  连接钱包后，会看到以下内容：
  ![performanceBetanet.jpg](https://docs.shardeum.org/assets/images/connectedWalletOptions-e908b5e2929d1c594b87ccee93b0e1c2.jpg)
  
当你点击“添加质押”时，会看到以下内容：
  ![performanceBetanet.jpg](https://docs.shardeum.org/assets/images/connectedWalletAddStake-bc1b9ab8875adcf3ca54a52f432dd4d4.jpg) 
  
  本例填写了 10 个 SHM 代币进行质押。

*建议每个验证者节点仅质押10个SHM，因为为验证者质押10个或更多SHM的奖励将相同*。
  
如果你看到Validator IP地址为“0.0.0.0”：

进入docker操作面板（如果是自定义安装位置，会有所不同）：

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



## Validator

### 版本

<Tabs groupId="validator-local-or-server">
  <TabItem value="local" label="Local" default>
    本地：

```shell
curl localhost:9001/nodeinfo
```

  </TabItem>
  <TabItem value="server" label="Server" default>
    远程服务器：

```shell
curl <server_ip>:9001/nodeinfo
```

  </TabItem>
</Tabs>

### 更新


<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd
cd .shardeum
./update.sh
```

  </TabItem>
</Tabs>


之后需要手动启动GUI:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui start
```

  </TabItem>
</Tabs>



### 错误日志

<Tabs>
  <TabItem value="shell" label="Shell" default>
    Shell界面：

```shell
sudo docker exec shardeum-dashboard cat cli/build/logs/exit-summary.json
```

  </TabItem>
  <TabItem value="CLI" label="CLI" default>
    Cli界面：
1.进入.shardeum:
```shell
cd .shardeum
```
2.运行.shell.sh:    
```shell
./shell.sh
```
3.在Validator CLI运行的情况下，通过输入以下内容导航到cli/build/logs目录：
```shell
cd cli/build/logs
```
4.通过输入以下内容查看exit-summary.json文件的内容：
```shell
cat exit-summary.json
```

  </TabItem>
</Tabs>

## CLI和GUI

### 版本

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli version
```

  </TabItem>

</Tabs>


### 更新

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli update
```

  </TabItem>
</Tabs>

### 命令帮助

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli help
```

  </TabItem>
</Tabs>

## 卸载Validator

如果你的Validator已过时并且想清理上次安装，

可以在根目录中删除Validator文件夹：
  
```shell
rm -rf .shardeum
```

还可以删除Shardeum Validator使用的docker容器和图像。

  
```json
   注意这些命令将删除计算机上的所有docker镜像和容器！
``` 


删除所有 docker 容器：

```shell
docker rm -vf $(docker ps -aq)
```

删除所有docker镜像：

```shell
docker rmi -f $(docker images -aq)
```
