
### SCOOP介绍

Scoop**是一款适用于Windows平台的命令行软件（包）管理工具**。 简单来说，就是可以通过命令行工具（PowerShell、CMD等）实现软件（包）的安装管理等需求，通过简单的一行代码实现软件的下载、安装、卸载、更新等操作。


### scoop基础使用

官网安装说明书： [ScoopInstaller](https://github.com/ScoopInstaller)

1. 先决条件

   - [PowerShell](https://aka.ms/powershell)最新版本或[Windows PowerShell 5.1](https://aka.ms/wmf5download)

2. PowerShell执行策略：

   ```
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```

3. 下载安装脚本,在Powershell中执行以下命令

   ```
   irm get.scoop.sh -outfile 'install.ps1'
   ```

4. 管理员执行安装脚本

   ```
   .\install.ps1 -RunAsAdmin -ScoopDir 'D:\Base' -ScoopGlobalDir 'D:\Global' -NoProxy
   ```

   其中`-RunAsAdmin`是使用管理员角色执行脚本，`-ScoopDir`指定scoop安装目录，软件默认安装在此。`-ScoopGlobalDir`指定全局程序安装到自定义目录。

5. 安装应用程序

   ```
   scoop install xxxxx -g
   ```

   `xxxx` 为所要安装的软件名称，`-g`指定程序安装到自定义目录，不加`-g`选项则安装到默认目录-g

### 安装该软件仓库中的软件

确保你已经有 Scoop 环境后，执行以下命令订阅本软件仓库：

```powershell
scoop bucket add 20142995 https://github.com/20142995/scoop-bucket
```

执行以下命令安装本仓库中的软件：

```powershell
scoop install 20142995/<软件名> -g
```

例如

```powershell
scoop install 20142995/xray -g
.......
```

大多数情况下，是可以省略 `20142995/`，只需要执行类似 `scoop install xray -g` 的命令

### 软件自动更新

这个仓库已经添加 github ci 自动化，每隔几个小时会自动更新所有软件到最新版本

使用者可以自行在系统中加个定时任务，这样就能自动更新 scoop 软件了，当然也可以手工更新

```powershell
scoop update *
```

单个软件的更新可以使用下列命令，大多数情况下软件名不重复的话，可以省略 `20142995/`，只需要执行类似 `scoop update xray` 的命令

```powershell
scoop update 20142995/xray
.......
```
