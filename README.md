# Node Version Manager

nvm安装加速教程以及镜像。

本仓库镜像站点：[https://gitlab.com/mirrorx/nvm](https://gitlab.com/mirrorx/nvm)

## 安装/更新

### 脚本方式安装（简单）

```sh
export NVM_SOURCE=https://gitlab.com/mirrorx/nvm.git
curl -o- https://gitlab.com/mirrorx/nvm/-/raw/master/install.sh | bash
```
```sh
export NVM_SOURCE=https://gitlab.com/mirrorx/nvm.git
wget -qO- https://gitlab.com/mirrorx/nvm/-/raw/master/install.sh | bash
```

执行上面任一脚本后，脚本会自动把仓库检出到`~/.nvm`，然后尝试将下面的配置加入到配置文件(`~/.bash_profile`, `~/.zshrc`, `~/.profile`, 或 `~/.bashrc`)。

```sh
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # 加载 nvm
```

### 检验安装是否成功

执行以下命令:

```sh
command -v nvm
```

如果结果显示`nvm`则表示已经安装成功.

### Git方式安装

如果已经安装`git`(v1.7.10+):

1. 克隆仓库到你的用户目录下
  - `cd ~/` 然后执行 `git clone https://gitlab.com/mirrorx/nvm.git .nvm`
1. `cd ~/.nvm`进入目录后切换到 `git checkout v0.38.0`
1. 执行`. ./nvm.sh`激活`nvm`

最后把下面内容加入到`~/.bashrc`, `~/.profile`, 或 `~/.zshrc`文件：

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # 加载 nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # 加载 nvm bash_completion
```

### 手动安装

```sh
export NVM_DIR="$HOME/.nvm" && (
  git clone https://gitlab.com/mirrorx/nvm.git "$NVM_DIR"
  cd "$NVM_DIR"
  git checkout `git describe --abbrev=0 --tags --match "v[0-9]*" $(git rev-list --tags --max-count=1)`
) && \. "$NVM_DIR/nvm.sh"
```

然后添加下面内容到`~/.bashrc`, `~/.profile`, 或 `~/.zshrc`：

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # 加载 nvm
```

### 手动升级

如果已经安装`git`(v1.7.10+):

```sh
(
  cd "$NVM_DIR"
  git fetch --tags origin
  git checkout `git describe --abbrev=0 --tags --match "v[0-9]*" $(git rev-list --tags --max-count=1)`
) && \. "$NVM_DIR/nvm.sh"
```

## 一些操作

### 设置默认node

```sh
nvm alias default node
```

#### 设置node安装镜像

```sh
export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node
nvm install node

NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node nvm install 4.2
```
