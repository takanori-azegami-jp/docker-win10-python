# DockerBuild-Win10-Python
Windows10で簡単にパイソンを実行したい時に

## 環境構築
PowerShellの管理者で実行する

1. wingetでDockerDesktopをインストール
~~~
PS C:\> winget install Docker.Desktop
~~~

2. DockerComposeはwingetにないので直接インストール
~~~
PS C:\> Invoke-WebRequest "https://github.com/docker/compose/releases/download/<font color="Red">バージョン</font>/docker-compose-Windows-x86_64.exe" -UseBasicParsing -OutFile $Env:ProgramFiles\docker\docker-compose.exe
~~~

バージョンは下記ですきなバージョンをセットする
https://github.com/docker/compose/releases

 
