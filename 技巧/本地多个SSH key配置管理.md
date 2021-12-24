## 本地多个SSH Key配置管理

1. 生成一对密钥（for GitLab）

   ```
   ssh-keygen -t rsa -C 'yourEmail@xx.com' -f ~/.ssh/gitlab-id_rsa
   ```

2. 生成另一对密钥（for GitHub）

   ```
   ssh-keygen -t rsa -C 'yourEmail@xx.com' -f ~/.ssh/github-id_rsa
   ```

3. 在~/.ssh目录下新建名称为config的文件（无后缀名）。用于配置多个不同的host使用不同的ssh key，内容如下：

   ```
   # gitlab
   Host gitlab.com
    HostName gitlab.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/gitlab-id_rsa
   # github
   Host github.com
      HostName github.com
      PreferredAuthentications publickey
      IdentityFile ~/.ssh/github-id_rsa
   
   ```