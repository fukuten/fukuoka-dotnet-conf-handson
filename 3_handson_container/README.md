# ハンズオン
今回のハンズオンは前回作成したASP.NET Core 2.0 Razor PagesのアプリケーションをDockerコンテナにしてみます。

## ハンズオン環境
[事前準備](../1_preparation/README.md)に従ってハンズオン環境を整えてください。

## 題材
まだ[ASP.NET Core 2.0 Razor Pages]()のハンズオンが済んでいない方は先にそちらのハンズオンを実施してください。

## 手順
### アプリケーションの発行
下記コマンドでDockerで実行するための実行ファイルを作成します。  
このコマンドで`bin/Debug/netcoreapp2.0/publish`に実行ファイルが生成されます。

```shell
cd RazorPagesMovie
dotnet publish
```

次に`MvcMovie.db`を`bin/Debug/netcoreapp2.0/publish`にコピーします。

### Dockerfileの作成
`RazorPagesMovie`ディレクトリに`Dockerfile`を作成します。  
Dockerfileには下記の内容を貼り付けてください。

```dockerfile
# ベースのイメージ(ASP.NET Core 2.0)
FROM microsoft/aspnetcore:2.0

# コンテナ内の実行ディレクトリ
WORKDIR /app

# 環境変数(本番環境)
ENV ASPNETCORE_ENVIRONMENT=Production

# 実行ファイルのコピー
COPY ./bin/Debug/netcoreapp2.0/publish .

# ポートフォワード
EXPOSE 80

# docker runで実行されるコマンド
ENTRYPOINT [ "dotnet", "RazorPagesMovie.dll" ]
```

#### コンテナのベースイメージ
[microsoft/aspnetcore - Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)

タグは`2.0`を使用します。

### Dockerイメージの作成
下記コマンドでDockerイメージを作成します。

```shell
cd RazorPagesMovie
docker build -t fukutenrazorapp .
```

### コンテナの実行
下記コマンドでコンテナを作成し、アプリケーションを実行します。

```shell
docker run --rm -p 8000:80 fukutenrazorapp
```

### アプリケーションへのアクセス
[http://localhost:8000/](http://localhost:8000/) にアクセスし、アプリケーションが正しく実行されることを確認します。  
また [http://localhost:8000/movies](http://localhost:8000/movies) にて、データのCRUD操作ができることも確認しましょう。

以上でDockerコンテナのハンズオンは終わりです。
