# DockerBuild-Win10-Python
Windows10で簡単にパイソンを実行したい時に

## 環境構築
PowerShellの管理者で実行

1. wingetでDockerDesktopをインストール
~~~powershell
PS C:\> winget install Docker.Desktop
~~~

2. DockerComposeはwingetにないので直接インストール
~~~powershell
PS C:\> Invoke-WebRequest "https://github.com/docker/compose/releases/download/【バージョン】/docker-compose-Windows-x86_64.exe" -UseBasicParsing -OutFile $Env:ProgramFiles\docker\docker-compose.exe
~~~

【バージョン】は下記からお好きなバージョン（ex：v2.2.1）を選んでセット<br>
https://github.com/docker/compose/releases

## コンテナ起動
~~~powershell
PS C:\>  docker-compose up -d --build
~~~

## 参考
[dockerで簡易にpython3の環境を作ってみる](https://qiita.com/reflet/items/4b3f91661a54ec70a7dc)

