---
title: "USBView のインストールと使い方"
emoji: "??"
type: "tech"
topics: ["windows", "ハードウェア", "デバイスドライバー"]
published: true
slug: "windows-installing-and-Using-usbview-ja"
---
Windows の USB ハードウェアがらみのトラブルを見極める手段として、開発者向けのツールとして有名な USBView があります。誰でも容易に使えるツールですが、インストール手順が少しだけ面倒なので紹介します。

## インストール手順

次の [**Windows のユニバーサル シリアル バス ビューアー**](https://learn.microsoft.com/ja-jp/windows-hardware/drivers/debugger/usbview?WT.mc_id=WDIT-MVP-35878) 手順を実行します。

[https://learn.microsoft.com/ja-jp/windows-hardware/drivers/debugger/usbview](https://learn.microsoft.com/ja-jp/windows-hardware/drivers/debugger/usbviewhttps://learn.microsoft.com/ja-jp/windows-hardware/drivers/debugger/usbview?WT.mc_id=WDIT-MVP-35878)

1. Windows SDK をダウンロードしてインストールを開始します。

2. インストール時に、 [Debugging Tools for Windows] ボックスのみを選択して、それ以外のすべてのボックスの選択を解除します。

3. SDK により、USBView は、x64 PC では既定で次のディレクトリにインストールされます。

C:\Program Files (x86)\Windows Kits\10\Debuggers\x64

4. 実行中のアーキテクチャに合わせた kits デバッガー ディレクトリを開き、**usbview.exe** を選択して起動します。

### Windows SDK のダウンロード

[https://developer.microsoft.com/ja-jp/windows/downloads/windows-sdk/](https://developer.microsoft.com/ja-jp/windows/downloads/windows-sdk/) のページでWindows SDK インストーラー winsdksetup.exe をダウンロードして起動し、インストールを開始します。

![画像](/images/windows-installing-and-Using-usbview-ja/792dc797-0d4b-400d-b64b-a1f1a87df007.png)
*インストーラーをダウンロードする> を選択*

### Windows SDK インストーラーの起動

ダウンロードした、winsdksetup.exe を起動すると次の画面が表示されるので、そのまま「Next」で次の項目選択に移動します。下の「Download the Windows Software Development kit - ... 」は、別のPC等へのオフラインインストーラをダウンロードする場合に選択します。

![画像](/images/windows-installing-and-Using-usbview-ja/b0513bfe-f16d-48cd-bfd3-3985180b5d81.png)
*インストーラー起動画面：「Next」で次へ*

### SDK インストール項目の選択

インストール機能の選択画面です。デフォルトでは全ての機能が有効です。

![画像](/images/windows-installing-and-Using-usbview-ja/8f48992b-da6c-4d58-8275-413529403e85.png)
*インストール機能の選択画面*

### Debugging Tools for Windows だけを残す選択

上から2番目の「Debugging Tools for Windows」だけを残して、他の選択を外して「インストール」をクリックします。他の項目を選択して残す事も可能ですが、Visual Studio をインストールしないと利用できない場合があります。

![画像](/images/windows-installing-and-Using-usbview-ja/55bd0fe7-dd34-47fd-b635-a04714247912.png)
*Debugging Tools for Windows」だけを残して選択*

### インストール完了

しばらく経つとインストールが完了して「Welcome」メッセージが表示されます。「Close」ボタンで閉じます。

![画像](/images/windows-installing-and-Using-usbview-ja/d8be38a0-2d41-44f8-87f6-266dd17ca8a6.png)
*「Close」ボタンで終了*

### インストールの確認

この手順でインストールした場合、x64版実行モジュールのインストール先は、**C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\usbview.exe** となります。

![画像](/images/windows-installing-and-Using-usbview-ja/6b5196f6-c334-4a46-86ab-1de943150403.png)
*実行モジュールのインストール先*

## USBView の起動

usbview.exe を起動した場合の表示例です。USBの各デバイスはこの様にUSB Hub を介してツリー構造で配置されます。

目的のデバイスの情報は目印となるUSBメモリーを抜き差しする等して接続点、物理ソケットとの対応を確認します。

正常なUSBデバイスをクリックして表示させると、デバイス情報、デバイスディスクリプターとエンドポイントの情報などを確認することが可能です。

![画像](/images/windows-installing-and-Using-usbview-ja/e0a9c6ef-7a35-41f6-b283-2769c9525e92.png)
*起動画面の表示例*

## 問題があるターゲットデバイス

次に示す様に 問題があるUSBターゲットデバイスが接続している場合は、黄色「!」マークで強調表示されます。

![画像](/images/windows-installing-and-Using-usbview-ja/b5c5816f-82a1-4079-b663-f1a4d628d77e.png)
*問題デバイスの発見*

## USBView ソース コード

[USBView のソースコードは、GitHub の Windows ドライバー サンプル リポジトリ](https://github.com/microsoft/Windows-driver-samples/tree/main/usb/usbview) から入手できます。

[https://github.com/microsoft/Windows-driver-samples/tree/main/usb/usbview](https://github.com/microsoft/Windows-driver-samples/tree/main/usb/usbview)

## 参考実演動画

[https://www.youtube.com/watch?v=80WIQn7SuOk](https://www.youtube.com/watch?v=80WIQn7SuOk)

以上。
