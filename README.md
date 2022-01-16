# DockerBuild-Win10-Python
DockerでPython実行環境を構築（Windows10）


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

## エラーがでた場合
下記エラーがでた場合、下記リンクの[2. buildkit を false に設定]をDocker Engine 設定画面まるごと変更でエラー解消<br>
[Docker Desktop3.0.0でビルド出来ない?!](https://zenn.dev/hiszuk/articles/cb30071df19a1b4f8365)
~~~powershell
------
 > [internal] load metadata for docker.io/library/python:3:
------
failed to solve with frontend dockerfile.v0: failed to create LLB definition: failed to authorize: rpc error: code = Unknown desc = failed to fetch oauth token: unexpected status: 401 Unauthorized
ERROR: Service 'python3' failed to build : Build failed
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
