---
title: "Windows 7 活用法"
emoji: "??"
type: "tech"
topics: ["windows", "windows 7", "windows update", "デバイスドライバー"]
published: true
slug: "windows-how-to-use-windows-7-ja"
---
サポートがとっくに終了している Windows 7 ですが、インストールメディアがあれば、今でも再インストール可能で Windows Update も配布されているため、古い環境のリファレンスとして使う方もいる様です。この手順では Windows 7 SP1 を最終版に更新し SHA-2(sha256) 署名のドライバーが認識されるため、CPUアーキテクチャ(ia32/x64)が一致すれば、以前利用出来なかった、Windows 8 以降のドライバーをインストールすることも可能になります。

そういうことで、Windows 7 を新規インストールするか、または運用中の Windows 7 を最終版に更新して、Windows Updateを使えるようにする手順を紹介します。

この手順に従っても、**Windows 7 のサポートが切れている事実は何も変わらないので、試す方は自己責任で、くれぐれもセキュリティに配慮してのご利用をお願いします。**

なおこの記事は、以前 Microsoft コミュニティで公開していた、**今どきの Windows 7 の Windows Update** の更新版です。

## 事前準備

新規インストール直後の Windows 7 と SP1 環境では、ブラウザが標準IEや最近のものだと全く使えません。試行錯誤の結果、[**Opera の Download サイト**](https://www.opera.com/ja/download) からダウンロード入手できる、Opera 36 (XP/Vista) 用を使ってうまくいくことを確認しています。これを最初に、更新対象の Windows 7 PCとは別のマシンでダウンロードし、その exe ファイルをコピー、起動して、更新対象マシンにインストールしておきます。

![画像](/images/windows-how-to-use-windows-7-ja/c4006b1c-c2f5-46ad-a999-67a1f89ca585.png)

次に更新対象の Windows 7 マシンが SP1 未適用の場合は、先に前述の Operaを起動して下記サイトからダウンロード、インストールして、SP1に更新しておきます。以降も同じですが、入手するコンポーネントの **マシン・アーキテクチャに十分に注意します。**

また、Operaを起動しての操作は最初のうち、次の様な「証明書が無い」などの警告が多数出ますが、全て無視して操作を続けます。

[https://www.catalog.update.microsoft.com/Search.aspx?q=KB976932](https://www.catalog.update.microsoft.com/Search.aspx?q=KB976932)

SP1環境（適用済）の場合は当然、この SP1 のインストールは不要です。

![画像](/images/windows-how-to-use-windows-7-ja/6e2aa87b-6237-47d8-9a66-544bdaf3159e.png)

## 手順１

[KB4474419](https://www.catalog.update.microsoft.com/search.aspx?q=KB4474419) と [KB4490628](https://www.catalog.update.microsoft.com/search.aspx?q=KB4490628) を入れます。順不同です。インストール後は再起動しておきます。

この二つで SHA-2 証明書が入るので、リモートデスクトップが使える様になり、またSHA-2 証明書が必要な Visual Studio 等のプログラムがインストール出来る様になり、WIndows 8以降用のドライバーもインストール可能になります。   しかし Windows Update の実行はエラーとなります。

## 手順２

この後、 [KB4536952](https://www.catalog.update.microsoft.com/search.aspx?q=KB4536952) を入れます。

## 手順３

最後に [KB4534310](https://www.catalog.update.microsoft.com/search.aspx?q=KB4534310) を入れ、完了したら再起動します。再起動後、**Windows  7 のサポートが切れていますというメッセージが出ますが、これはここまでの手順がうまく行っているという合図です。**

Windows 7 用の Windows Update が2021年6月末に発生した問題の様に止まっていなければ、これで Windows 7 SP1 新規インストールマシンで次に示すように、Windows Update が完璧に利用出来る様になります。

![画像](/images/windows-how-to-use-windows-7-ja/0cd4361a-d927-468d-971c-f4ace03815b0.png)

Windows Update 後の再起動が終わると、今度は最新版の Microsoft Edge がお出迎えするので、少し感動です。

## 手順４ TLS1.1 / 1.2 優先順位設定

ここまで更新して来た Windows 7 SP1 では、2023年から必要になった TLS 1.1 および TLS 1.2 のレジストリ設定によるプロトコル優先順位の設定がされていません。

詳細は、[**Windows の WinHTTP で TLS 1.1 および TLS 1.2 を既定のセキュリティ で保護されたプロトコルとして有効にするための更新プログラム**](https://support.microsoft.com/ja-jp/topic/windows-%E3%81%AE-winhttp-%E3%81%A7-tls-1-1-%E3%81%8A%E3%82%88%E3%81%B3-tls-1-2-%E3%82%92%E6%97%A2%E5%AE%9A%E3%81%AE%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3-%E3%81%A7%E4%BF%9D%E8%AD%B7%E3%81%95%E3%82%8C%E3%81%9F%E3%83%97%E3%83%AD%E3%83%88%E3%82%B3%E3%83%AB%E3%81%A8%E3%81%97%E3%81%A6%E6%9C%89%E5%8A%B9%E3%81%AB%E3%81%99%E3%82%8B%E3%81%9F%E3%82%81%E3%81%AE%E6%9B%B4%E6%96%B0%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0-c4bd73d2-31d7-761e-0178-11268bb10392) に記載されています。

この記事記載の [KB3140245](https://catalog.update.microsoft.com/search.aspx?q=kb3140245) は [手順３](#手順３)で導入した、 Windows 7 用 Windows Update の品質ロールアップで導入済です。従って追加手順として、前記記事のリンク先「Easy Fix DefaultSecureProtocols レジストリ サブキーを自動的に追加するには、ここをクリック します。... 」に従います。これを設定する事で、最新のTLS 優先順位のレジストリが設定されます。そして、MediaCreationTool22H2.exe などを実行してもエラーが出ない様になります。

わかり易く言うとこの修正は、以下からMicrosoftEasyFix51044.msi を入手して実行することで完了します。

[https://download.microsoft.com/download/0/6/5/0658B1A7-6D2E-474F-BC2C-D69E5B9E9A68/MicrosoftEasyFix51044.msi](https://download.microsoft.com/download/0/6/5/0658B1A7-6D2E-474F-BC2C-D69E5B9E9A68/MicrosoftEasyFix51044.msi)

以上。
