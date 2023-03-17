
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

Curl request docker-compose:

<Tabs groupId="operating-systems">
  <TabItem value="linux" label="Linux" default>

```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

  </TabItem>
  <TabItem value="mac" label="Mac" default>

```shell
brew install docker-compose
```

   </TabItem>
</Tabs>

Setup permissions for docker-compose:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
sudo chmod +x /usr/local/bin/docker-compose
```

  </TabItem>
</Tabs>

Check that docker-compose is working with (should return version 1.29.2 or higher):

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
docker-compose --version
```

  </TabItem>
</Tabs>

:::tip
Shardeum Validator support on Windows will be coming in the future.
:::

## Step 2: Download and install validator

Run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
curl -O https://gitlab.com/shardeum/validator/dashboard/-/raw/main/installer.sh && chmod +x installer.sh && ./installer.sh
```

  </TabItem>
</Tabs>

The terminal will ask questions about your setup settings.

Give permission to collect validator data for bug reporting:

```shell
By running this installer, you agree to allow the Shardeum team to collect this data. (y/n)?:
```

Enter y to setup the web based dashboard:

```shell
Do you want to run the web based Dashboard? (y/n): y
```

Set a password for dashboard access:

```shell
Set the password to access the Dashboard:
```

Add a custom session port for the web based dashboard or hit enter for port 8080:

```shell
Enter the port (1025-65536) to access the web based Dashboard (default 8080):
```

Set the first p2p port (default 9001):

```shell
This allows p2p communication between nodes. Enter the first port (1025-65536) for p2p communication (default 9001):
```

Set the second p2p port (default 10001):

```shell
Enter the second port (1025-65536) for p2p communication (default 10001):
```

Add a custom path or install to root:

```shell
What base directory should the node use (defaults to ~/.shardeum):
```

Wait for the installation process to complete.

:::caution
If you are behind a router and you are using ports 9001 and 10001 for p2p communication,
make sure ports 9001 and 10001, are forwarded (be careful doing this since it will modify your firewall):

https://www.noip.com/support/knowledgebase/general-port-forwarding-guide/

Reference:

https://gitlab.com/shardeum/validator/dashboard/
:::

## Step 3: Open validator CLI

Make sure you are in the root directory by running:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd
```

  </TabItem>
</Tabs>

Go to the hidden Shardeum directory:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd .shardeum
```

  </TabItem>
</Tabs>

Start the CLI by running the following shell script:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
./shell.sh
```

  </TabItem>
</Tabs>

:::warning
If you see docker container error:

```golang
Error response from daemon: Container <container_id_hexadecimal> is not running
```

start all docker containers until the errors go away:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
docker start <container_id_hexadecimal>
```

  </TabItem>
</Tabs>
:::

:::warning
If you see docker permission error:

```golang
Got permission denied while trying to connect to the Docker daemon socket at
unix:///var/run/docker.sock:
Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/shardeum-dashboard/json":
dial unix /var/run/docker.sock:
connect:
permission denied
```

run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
sudo usermod -a -G docker $USER && newgrp docker
```

  </TabItem>
</Tabs>

if that does not work, also try:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
sudo service docker start
```

  </TabItem>
</Tabs>

then try to start the shell script again.
:::

## Step 4: Open validator GUI

While inside the shell script, run:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui start
```

  </TabItem>
</Tabs>

Go to your web browser and go to:

<Tabs groupId="validator-local-or-server">
  <TabItem value="local" label="Local" default>

```shell
https://localhost:8080/
```

  </TabItem>
  <TabItem value="server" label="Server" default>

```shell
https://<server_ip>:8080/
```

  </TabItem>
</Tabs>


:::caution
You might see a warning page when trying to access this address in your web browser.
Ignore this warning and continue to the validator dashboard. Another way to work around this warning:

<Tabs>
  <TabItem value="firefox" label="Firefox" default>

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

:::

You will be asked for your password set during setup.

![loginPage.jpg](/img/node/run/validator/loginPage.jpg)

:::danger
The login will fail even if you put no password during the setup process.
To set a new password inside the validator CLI:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli gui set password <type_new_password__here>
```

  </TabItem>
</Tabs>

:::

You should see the “Overview” page for the Shardeum Validator Dashboard in your web browser:

![overviewBetanet.jpg](/img/node/run/validator/overviewBetanet.jpg)

## Step 5: Start validator

Go to the “Maintenance” page, then click the “Start Node” button in the top left white box:

![startBetanet.jpg](/img/node/run/validator/startBetanet.jpg)

(Same as running)

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli start
```

  </TabItem>
</Tabs>

Wait and refresh the page.

The node is running correctly if the “Start Node” button now says “Stop Node”. If you want to stop tne node with the CLI:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli stop
```

  </TabItem>
</Tabs>

![startedBetanet.jpg](/img/node/run/validator/startedBetanet.jpg)

## Step 6: Monitor validator

Go to “Performance” to see your node’s hardware performance here:

![performanceBetanet.jpg](/img/node/run/validator/performanceBetanet.jpg)

For more details about your node status run the following inside the CLI:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
operator-cli status
```

  </TabItem>
</Tabs>

:::danger
If your node becomes inactive, try checking its status.
:::

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
pm2 list
```

  </TabItem>
</Tabs>

Reset the validator from the list by running:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
pm2 delete [id]
```

  </TabItem>
</Tabs>

## Step 7: Connect Wallet to Betanet

[Connect to Sphinx 1.X with your wallet by clicking the button linked here](/Network/Endpoints#connect-wallet)

## Step 8: Get SHM from Betanet Faucet

[Shardeum Twitter SHM Faucet Guide for Sphinx 1.X](/Faucet/Claim#shardeum-faucet-website)

## Step 9: Stake SHM to validator

### GUI

After you start the validator, go to the “Settings” page. You will be asked to connect your wallet:

![connectWalletBetanet.jpg](/img/node/run/validator/connectWalletBetanet.jpg)

After you connect your wallet, you should see the following:

![connectedWalletOptions.jpg](/img/node/run/validator/connectedWalletOptions.jpg)

When you click "Add Stake", you will see the following:

![connectedWalletAddStake.jpg](/img/node/run/validator/connectedWalletAddStake.jpg)

```
-Stake Wallet Address [wallet connected]
-Nominee Public Key [filled in automatically while validator is running]
-Stake amount (SHM) [empty and is in units ether not wei]
```

This example has filled in 10 SHM tokens to stake.

:::tip
It is recommended to stake just 10 SHM per Validator node, 
since rewards will be the same with 10 SHM or more staked for a Validator. 
:::

Once all fields are filled, click the “Stake” button.

Your wallet will ask you to sign the transaction stake your SHM.

Once the transaction is signed and complete, you have staked your SHM tokens successfully.

:::info
If your node status is on Standby and you have 10 SHM or more staked, your validator node is setup correctly.

The network will automatically add your validator to be active in the network.

The time to be added as an active validator will vary based on network load and validators in the network.
:::

:::caution
If you have staked before, you can "Remove Stake". However, you will stop getting testnet SHM rewards when you unstake.
:::

:::danger
If you see your validator IP address as "0.0.0.0":

Go into the operator dashboard docker (may be different if you customized install location:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
cd ~/.shardeum
./shell.sh
```

  </TabItem>

</Tabs>

Get your node's external IP:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
curl https://ipinfo.io/ip
```

  </TabItem>

</Tabs>

The returned IP in the format of nnn.nnn.nnn.nnn is your EXTERNAL_IP.

Set the number above in place of EXTERNAL_IP:

<Tabs>
  <TabItem value="shell" label="Shell" default>

```shell
export APP_IP="EXTERNAL_IP"
```

  </TabItem>

</Tabs>

:::

### CLI

You can also stake and unstake from the Validator CLI if you are not able to access a web browser for the Validator GUI.

First, set your private key in your Validator CLI:

:::warning
Be very careful with your private keys. We recommend you use a private key which has testnet tokens only to be safe.
:::

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
