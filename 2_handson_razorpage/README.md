# ハンズオン
今回のハンズオンはASP.NET Core 2.0 Razor Pagesです。

## ハンズオン環境
[事前準備]()に従ってハンズオン環境を整えてください。

## ASP.NET Core Razor Pagesとは？
[ASP.NET Core での Razor ページの概要 | Microsoft Docs](https://docs.microsoft.com/ja-jp/aspnet/core/mvc/razor-pages/)

## 題材
[Mac で ASP.NET Core を使用して Razor ページ Web アプリを作成する | Microsoft Docs](https://docs.microsoft.com/ja-jp/aspnet/core/tutorials/razor-pages-mac/)

## 手順
### Razor Pageのプロジェクトを作成する
コマンドプロンプトやPowershell、ターミナルなどで以下のコマンドを入力します。

```
mkdir fukuten
dotnet new razor -o RazorPagesMovie
```

### Visual Studio Codeでプロジェクトを開く
`RazorPagesMovie`ディレクトリをVisual Studio Codeで開きましょう。

### まず実行してみる
Visual Studio Codeのターミナルで以下のコマンドを入力します。

```
cd RazorPagesMovie
dotnet run
```

`dotnet run`コマンドで`Kestrel`というASP.NET Coreのビルドインサーバが起動します。  
Kestrelについてはこちらをご覧ください。  
[ASP.NET Core の kestrel web サーバーの実装 | Microsoft Docs](https://docs.microsoft.com/ja-jp/aspnet/core/fundamentals/servers/kestrel?tabs=aspnetcore2x)

ブラウザで[http://localhost:5000](http://localhost:5000)にアクセスしてみましょう。  
Kestrelを停止する場合はターミナルにて`Ctrl+C`を入力します。

### モデルの追加
1. `RazorPagesMovie`ディレクトリの配下に`Models`ディレクトリを作成します。
2. `Models`ディレクトリに`Movie.cs`ファイルを作成します。
3. `Movie.cs`ファイルに映画に関するプロパティを定義します。サンプルは以下。

```cs
using System;

namespace RazorPagesMovie.Models
{
    public class Movie
    {
        public int ID { get; set; }
        public string Title { get; set; }
        public DateTime ReleaseDate { get; set; }
        public string Genre { get; set; }
        public decimal Price { get; set; }
    }
}
```