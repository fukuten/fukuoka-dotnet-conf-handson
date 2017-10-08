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
