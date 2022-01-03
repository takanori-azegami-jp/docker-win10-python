# DockerBuild-Win10-Python
Windows10で簡単にパイソンを実行したい時に


## 環境構築
PowerShellの管理者で実行

1. wingetでDockerDesktopをインストール<br>
PowerShellでエラーになる場合はコマンドプロンプトから実行
~~~powershell
PS C:\> winget install  Docker.DockerDesktop
~~~

2. Docker-Composeはwingetにないので直接インストール
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


## コンテナ接続
~~~powershell
#コンテナID取得
PS C:\>  docker ps 
#コンテナに接続
PS C:\>  docker exec -it コンテナID bash
~~~

## コンテナでPython実行
~~~console
$ python /root/opt/HelloWorld.py
~~~


## コンテナとイメージの削除
不要になったコンテナとイメージを削除
~~~powershell
#コンテナ削除
PS C:\> $ docker ps
PS C:\> $ docker rm コンテナID
#イメージを削除
PS C:\> $ docker images
PS C:\> $ docker rmi イメージID
~~~


## 参考
[dockerで簡易にpython3の環境を作ってみる](https://qiita.com/reflet/items/4b3f91661a54ec70a7dc)
