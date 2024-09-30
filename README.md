# web-test
hell0

1
2
3

## 


在电脑上切换 GitHub 账户以提交代码，可以按照以下步骤进行：

### 1. 配置 Git 用户信息

首先，需要确保 Git 配置了正确的用户信息。可以通过以下命令查看当前配置：

```bash
git config --global user.name
git config --global user.email
```

如果要更改当前项目的用户信息，可以在项目目录下运行以下命令：

```bash
git config user.name "你的用户名"
git config user.email "你的邮箱"
```

### 2. 使用 SSH 密钥（如果使用 SSH）

如果你使用 SSH 进行 GitHub 认证，可以为不同的账户生成不同的 SSH 密钥：

1. 生成新的 SSH 密钥（例如，针对第二个账户）：

   ```bash
   ssh-keygen -t rsa -b 4096 -C "你的邮箱"
   ```

   在提示中，选择一个不同的文件名（例如 `id_rsa_github_second`）。

2. 添加 SSH 密钥到 SSH 代理：

   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa_github_second
   ```

3. 将公钥添加到 GitHub 账户中。可以通过以下命令查看公钥：

   ```bash
   cat ~/.ssh/id_rsa_github_second.pub
   ```

4. 登录到 GitHub，进入 **Settings > SSH and GPG keys**，添加新的 SSH 密钥。

### 3. 配置 SSH 配置文件

在 `~/.ssh/config` 文件中，可以为不同的账户配置不同的设置。示例如下：

```plaintext
# 第一个账户
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_github

# 第二个账户
Host github-second
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_github_second
```

### 4. 使用不同的账户推送代码

在使用不同账户的项目中，确保使用配置的 Host 名称。例如：

```bash
git remote set-url origin git@github-second:username/repo.git
```

### 5. 提交代码

完成上述步骤后，你可以正常提交代码：

```bash
git add .
git commit -m "你的提交信息"
git push origin master
```

### 6. 切换账户

在不同项目中，可以重复上述步骤，确保每个项目使用正确的 Git 用户信息和 SSH 密钥。

这样，你就可以在同一台电脑上轻松切换不同的 GitHub 账户了！如果有任何问题，欢迎随时询问。



### 
```
$  ~/Desktop/wangrong/web3 git:(main) ssh-keygen -t rsa -b 4096 -C "897100547@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/haotian.chen/.ssh/id_rsa): id_rsa_github_second
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in id_rsa_github_second
Your public key has been saved in id_rsa_github_second.pub
The key fingerprint is:
SHA256:kcyfoYrzFcArOE9j7PW0as6d4mQ/KdAz9jNaXiF7/TA 897100547@qq.com
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|     . o .       |
|      o = .      |
|   o   o + o     |
|  o *.o S +      |
|   *.==+ = o     |
|    =o++*.o E    |
|     *+B*+   +   |
|     +B+=+    .  |
+----[SHA256]-----+
```
