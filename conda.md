# Conda

## Miniconda

https://docs.conda.io/projects/miniconda/en/latest/index.html

手順 (2024-01-19時点)


These four commands quickly and quietly install the latest 64-bit version of the installer and then clean up after themselves. To install a different version or architecture of Miniconda for Linux, change the name of the .sh installer in the wget command.

これら 4 つのコマンドは、最新の 64 ビット バージョンのインストーラーを迅速かつ静かにインストールし、その後クリーンアップします。 Miniconda for Linux の別のバージョンまたはアーキテクチャをインストールするには、`wget` コマンドで `.sh` インストーラーの名前を変更します。

```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

After installing, initialize your newly-installed Miniconda. The following commands initialize for bash and zsh shells:

インストール後、新しくインストールした Miniconda を初期化します。次のコマンドは、bash シェルと zsh シェルを初期化します。

```
~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
```

