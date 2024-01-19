# WSL + Ubuntu 環境

## VSCode
1. WSL/Ubuntu のターミナルを開く
2. ワークディレクトリに移動する
3. `code .` を実行する
   
### Python の場合
- VSCode 右下の Python 設定が、実行する環境を選んでいるか注意する (例: conda)
![alt](./images/vscode-python.png)

## SSH server
VSCode は SSH なしでも WSL に接続できるが、必要に応じて SSH server を起動する

状態を確認する (以下の場合は起動済み)
```
$ sudo service ssh status
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2024-01-18 14:52:41 JST; 18h ago
```
起動していないときは、以下のコマンドで起動する
```
sudo service ssh restart
```