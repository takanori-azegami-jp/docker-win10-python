# DockerBuild-Win10-Python
Windows10で簡単にパイソンを実行したい時に


## 環境構築
PowerShellの管理者で実行

1. wingetでDockerDesktopをインストール
~~~powershell
PS C:\> winget install  Docker.DockerDesktop
~~~

2. DockerComposeはwingetにないので直接インストール
~~~powershell
PS C:\> Invoke-WebRequest "https://github.com/docker/compose/releases/download/【バージョン】/docker-compose-Windows-x86_64.exe" -UseBasicParsing -OutFile $Env:ProgramFiles\docker\docker-compose.exe
~~~

【バージョン】は下記からお好きなバージョン（ex：v2.2.1）を選んでセット<br>
https://github.com/docker/compose/releases


## コンテナ起動
Dockerfile、docker-compose.ymlを配置したフォルダに移動して実行
~~~powershell
PS C:\>  docker-compose up -d --build
~~~


## コンテナ起動
Dockerfile、docker-compose.ymlを配置したフォルダに移動して実行
~~~powershell
PS C:\>  docker-compose up -d --build
~~~

## コンテナでPython実行
~~~console
$ /root/opt/HelloWorld.py
~~~

## コンテナ接続
~~~powershell
#コンテナID取得
PS C:\>  docker ps 
#コンテナに接続
PS C:\>  docker-compose exec コンテナID bash
~~~

## コンテナ削除
不要になったコンテナを削除
~~~powershell
PS C:\>  docker-compose exec コンテナID bash
~~~


 docker-compose exec python3 bash



## 参考
[dockerで簡易にpython3の環境を作ってみる](https://qiita.com/reflet/items/4b3f91661a54ec70a7dc)

