# ubuntu 20.04 環境

## OS instal
- ISO イメージを iRAMSでマウント
- リブート
- <F12> でブートメニューを出し、マウントした仮想DVDを選択
- インストール処理
  - Integrityチェックにすごく時間がかかる (20.04.3)
  - Language: English
  - Network connection: しばらく待つとDHCPでIPアドレスが設定される
  - プロキシを設定する
    - http://USER:PASS@HOST:PORT/ 
  - ミラーサーバー: デフォルト
  - ディスクが使用中の場合エラーが出る
    - Continue
    - 目的のディスクが選択されていることを確認する
      - ディスク全体を使用
    - 確認
  - ユーザID, PASSWD 設定
  - OpenSSH: インストールする
  - パッケージは選択せず
  - インストール後、リブート
- Note
  - 最初のインストールの時、前のOS が起動してしまった。HDDではなくて、SSDにインストールされてしまった。

## sudo 設定
エディタを選択 （default の nano エディタでよければ、この操作は不要)
```
sudo update-alternatives --config editor
```

sudoers を編集する
```
sudo visudo
```

```
%sudo   ALL=(ALL:ALL) NOPASSWD: ALL
```

## user 追加
`USER` はユーザIDとする

ユーザの追加
```sh:
adduser USER
```
```sh:
useradd -d USER
```

ユーザをsudoグループに追加する。
```sh:
usermod -aG sudo USER 
```

## timezone

```sh:
sudo timedatectl set-timezone Asia/Tokyo 
```

## NTP

```sh:
sudo service systemd-timesyncd status

sudo vi /etc/systemd/timesyncd.conf
NTP=ntp2.css.fujitsu.com

sudo service systemd-timesyncd restart

timedatectl timesync-status
```

## Proxy

### 
全体に設定を効かせるときは、`.bashrc` などで環境変数を設定する。

```sh:.bashrc
export http_proxy=http://user:pass@proxy_server:port
export https_proxy=http://user:pass@proxy_server:port
```

### apt

/etc/apt/apt.conf.d/90curtin-aptproxy  に設定

```conf:/etc/apt/apt.conf.d/90curtin-aptproxy 
Acquire::http::Proxy "http://user:pass@proxy_server:port";
Acquire::https::Proxy "http://user:pass@proxy_server:port";
```

### curl

~/.curlrc に設定
```sh:.curlrc
proxy = "http://proxy_server:port"
proxy-user = "user:pass"
```
