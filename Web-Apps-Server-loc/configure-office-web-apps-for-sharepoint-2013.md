---
title: SharePoint 2013 の Office Web アプリケーションを構成します。
TOCTitle: SharePoint 2013 の Office Web アプリケーションを構成します。
ms:assetid: a5276781-133b-413c-beca-b851e17c2081
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ff431687(v=office.15)
ms:contentKeyID: 48796435
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# SharePoint 2013 の Office Web アプリケーションを構成します。

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2016-12-16_

**概要:** Office Web Apps を使用するために SharePoint 2013 を構成する方法を説明します。

**対象ユーザー:** IT 担当者

この記事では、[Office Web Apps サーバーの展開](deploy-office-web-apps-server.md) がオフになる場所を取り上げます。記事では、Office Web Apps サーバー を実行するサーバーを設定します。ここでは Office Web Apps サーバー を使うために SharePoint 2013 を構成します。まず、SharePoint 2013 の Windows PowerShell コマンドレットをいくつか実行する必要があり、その後ユーザーは、ブラウザーの SharePoint 2013 ドキュメント ライブラリから Office ファイルを開くことができます。

Office Web Apps サーバー の機能がわからない場合は、[概要のトピックを確認してください](office-web-apps-server-overview.md)。

この記事の内容

  - Office Web Apps サーバーを使用するための SharePoint 2013 を構成する前に

  - Office Web アプリケーション サーバーを使用する SharePoint 2013 の構成します。

  - SharePoint 2013 で使用されている場合の Office Web Apps で発生したエラーのトラブルシューティング

  - Office Web Apps サーバーからの SharePoint 2013 の切断

## Office Web アプリケーション サーバーを使用する SharePoint 2013 を構成する前に

いくつかの点を開始する前に確認します。

  - SharePoint 2013 をインストールします。「[SharePoint 2013 をインストールする](https://technet.microsoft.com/ja-jp/library/cc303424\(v=office.15\))」ガイドをご覧ください。

  - すべての SharePoint 2013 Web アプリケーションでクレームベース認証を使用していることを確認します。クラシック モード認証を使用する SharePoint 2013 Web アプリケーションでは、Office Web Apps の表示と編集が機能しません。[Office Web Apps の SharePoint 認証の要件](plan-office-web-apps-used-with-sharepoint-2013.md)」を参照してください。

  - ユーザーが Web ブラウザーで Office ドキュメントを (読み取るだけでなく) 編集できるようにするには、編集ライセンスが必要です。また、 Office Web Apps サーバー ファームで編集を有効にする必要があります。ライセンス要件の詳細については、「[Office ファイルを編集するための Office Web Apps のライセンス](plan-office-web-apps-used-with-sharepoint-2013.md)」を参照してください。

  - システム アカウントを使用して SharePoint 2013 にログオンすると、SharePoint 2013 と Office Web Apps サーバー 間の接続をテストできなくなります。接続をテストするには、別のアカウントでログオンします。

  - メモリが不足していると、Office Web Apps 内の Office ドキュメントのプレビューで問題が生じることがあります。「[Web サーバー、アプリケーション サーバー、および単一サーバー インストールのハードウェア要件](https://technet.microsoft.com/ja-jp/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)」に記載されている SharePoint 2013 を確認してください。 Office Web Apps サーバー にも同じ要件が適用されます。

## Office Web アプリケーション サーバーを使用する SharePoint 2013 を構成します。

HTTP または HTTPS を使用するかどうかに応じて、次のセクションのいずれかを選択します。 HTTP は、テスト環境に対してのみ推奨されます。本番環境では、より安全な HTTPS プロトコルが好ましい選択です。

## HTTP を使用するテスト環境

以下の手順を開始する前に、[テスト環境での単一サーバー Office Web Apps Server ファームの展開](deploy-office-web-apps-server.md) に記載された手順に従ってOffice Web Apps サーバー がセットアップされていることを確認して下さい。Office Web Apps サーバー ファームが内部 URL と HTTP を使用するように構成されている必要があります。 テスト環境で Office Web Apps サーバー を使用するための [ビデオ: SharePoint 2013 の Office Web アプリケーションを構成します。](video-configure-office-web-apps-for-sharepoint-2013.md)Office Web Apps サーバー セットアップ方法 と SharePoint 2013 構成方法をご覧ください。

## 手順 1: 管理者特権の SharePoint 2013 管理シェルを開く

お使いのサーバー オペレーティング システムに対応する手順を選択してください。

**Windows Server 2008 R2 内**

1.  \[**スタート**\] \> \[**すべてのプログラム**\] \> \[**Microsoft SharePoint 2013 製品**\] の順にクリックします。

2.  \[**SharePoint 2013 管理シェル**\] を右クリックし、\[**管理者として実行**\] をクリックします。

**Windows Server 2012 内**

1.  Windows ロゴ キー + Q を押すか、または画面の端から内側へスワイプしてチャームを表示し、\[**検索**\] を選択してコンピューターにインストールされているすべてのアプリケーションを表示します。

2.  \[**SharePoint 2013 管理シェル**\] を右 クリックしてアプリ バーを表示します。

3.  アプリケーション バーで、\[**管理者として実行**\] をクリックします。

## 手順 2: SharePoint 2013 と Office Web Apps サーバーの間のバインドを作成する

次のコマンドを実行します。\<WacServerName\> は、内部 URL に設定した URL の完全修飾ドメイン名 (FQDN) です。ここが Office Web Apps サーバー トラフィックのエントリ ポイントになります。このテスト環境では –AllowHTTP パラメーターを指定して、SharePoint 2013 が HTTP を使用して Office Web Apps サーバー ファームからの検出情報を受信できるようにする必要があります。 –AllowHTTP を指定し忘れると、SharePoint 2013 は Office Web Apps サーバー ファームとの通信に HTTPS を使おうとして、このコマンドが失敗します。

    New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP

このコマンドを実行した後、Windows PowerShell コマンド プロンプトに表示されるバインドの一覧を参照する必要があります。

ヘルプ情報については、「[New-SPWOPIBinding](new-spwopibinding.md)」を参照してください。

## 手順 3: SharePoint のバインドの WOPI ゾーンを表示する

Office Web Apps サーバー はゾーンの概念を使用して、ホスト (ここでは SharePoint 2013) との通信に使用する URL (内部または外部) とプロトコル (HTTP または HTTPS) を判断します。既定では、SharePoint Server 2013 は **internal-https** ゾーンを使用します。次のコマンドを実行し、カスタマイズ ゾーンを確認します。

    Get-SPWOPIZone

このコマンドで表示される WOPI ゾーン は **internal-http** である必要があります。正しく表示されている場合は、手順 5 に進みます。そうでない場合は、次の手順を参照してください。

ヘルプ情報については、「[Get-SPWOPIZone](get-spwopizone.md)」を参照してください。

## 手順 4: WOPI ゾーンを internal-http に変更する

手順 3. の実行結果が **internal-https** だった場合は、次のコマンドを実行してゾーンを **internal-http** に変更します。この変更を行うのは、SharePoint 2013 のゾーンと Office Web Apps サーバー ファームのゾーンが一致している必要があるからです。

    Set-SPWOPIZone -zone "internal-http"

**Get-SPWOPIZone** を再度実行し、新しいゾーンが **internal-http** になっていることを確認します。

ヘルプ情報については、「[Set-SPWOPIZone](set-spwopizone.md)」および「[Get-SPWOPIZone](get-spwopizone.md)」を参照してください。

## 手順 5: SharePoint 2013 で AllowOAuthOverHttp の設定を True に変更する

テスト環境で Office Web Apps を SharePoint 2013 と共に HTTP 経由で使用するには、AllowOAuthOverHttp を **True** に設定する必要があります。この設定を行わないと Office Web Apps は機能しません。現在の状態を確認するには、次のコマンドを実行します。

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

このコマンドを実行して \[**False**\] が返された場合は、次のコマンドを実行して値を \[**True**\] に設定します。

    $config = (Get-SPSecurityTokenServiceConfig)

    $config.AllowOAuthOverHttp = $true

    $config.Update()

次のコマンドをもう一度実行して、AllowOAuthOverHttp が \[**True**\] に設定されたことを確認します。

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

ヘルプ情報については、「[Get-SPSecurityTokenServiceConfig](https://technet.microsoft.com/ja-jp/library/ff607642\(v=office.15\))」を参照してください。

## 手順 6: Office Web Apps が動作することを確認する

Office Web Apps を使用してドキュメントの編集したり表示することができないため、SharePoint 2013 ではシステム アカウントとしてログインしていないことを確認します。Office ドキュメントが含まれている SharePoint 2013 ドキュメント ライブラリへ移動し、 Word、PowerPoint、Excel または OneNote のファイルを表示します。ブラウザーでドキュメントが開かれ、Office Web Apps を使用してファイルが表示されます。

この手順が失敗する場合は、「Office Web Apps のエラーのトラブルシューティング」を参照してください。

## 本番環境では HTTPS を使用します。

以下の手順を開始する前に、「[HTTPS を使用する単一サーバー Office Web Apps Server ファームの展開](deploy-office-web-apps-server#https-を使用する単一サーバー-office-web-apps-サーバー-ファームの展開)」または「[HTTPS を使用する負荷分散された複数サーバー Office Web Apps Server ファームの展開](deploy-office-web-apps-server#https-を使用する負荷分散された複数サーバー-office-web-apps-サーバー-ファームの展開)」に記載された手順に従って Office Web Apps サーバー がセットアップされていることを確認してください。

## 手順 1: SharePoint 2013 管理シェルを開く

お使いのサーバー オペレーティング システムに対応する手順を選択してください。

**Windows Server 2008 R2 内**

1.  \[**スタート**\] \> \[**すべてのプログラム**\] \> \[**Microsoft SharePoint 2013 製品**\] の順位選択します。

2.  \[**SharePoint 2013 管理シェル**\] を右クリックしてショートカット メニューを表示し、\[**管理者として実行**\] をクリックします。

**Windows Server 2012 内**

1.  Windows ロゴ キー + Q を押すか、または画面の端から内側へスワイプしてチャームを表示し、\[**検索**\] をクリックしてコンピューターにインストールされているすべてのアプリケーションを表示します。

2.  \[**SharePoint 2013 管理シェル**\] を右 クリックしてアプリ バーを表示します。

3.  アプリケーション バーで、\[**管理者として実行**\] をクリックします。

## 手順 2: SharePoint 2013 と Office Web Apps サーバーの間のバインドを作成する

次のコマンドを実行します。\<WacServerName\> は、内部 URL に設定した URL の完全修飾ドメイン名 (FQDN) です。ここが Office Web Apps サーバー トラフィックのエントリ ポイントになります。

    New-SPWOPIBinding -ServerName <WacServerName> 

ヘルプ情報については、「[New-SPWOPIBinding](new-spwopibinding.md)」を参照してください。

## 手順 3: SharePoint 2013 の WOPI ゾーンを表示する

Office Web Apps サーバー はゾーンの概念を使用して、ホスト (ここでは SharePoint 2013) との通信に使用する URL (内部または外部) とプロトコル (HTTP または HTTPS) を判断します。既定では、SharePoint Server 2013 は **internal-https** ゾーンを使用します。次のコマンドを実行し、これが現在のゾーンになっているかどうかを確認します。

    Get-SPWOPIZone

表示された WOPI ゾーンを書き留めます。

ヘルプ情報については、「[Get-SPWOPIZone](get-spwopizone.md)」を参照してください。

## 手順 4: 必要に応じて、WOPI ゾーンを変更します。

使用する環境によっては、WOPI ゾーンを変更する必要があります。SharePoint ファームが内部と外部にある場合は、外部を指定します。SharePoint ファームが内部のみの場合は、内部を指定します。

手順 3. の実行結果が **internal-https** で、SharePoint ファームが内部のみの場合は、この手順を省略できます。SharePoint ファームが内部と外部にある場合は、次のコマンドを実行してゾーンを **external-https** に変更する必要があります。

    Set-SPWOPIZone -zone "external-https"

ヘルプ情報については、「[Set-SPWOPIZone](set-spwopizone.md)」を参照してください。

## 手順 6: Office Web Apps が動作することを確認する

Office Web Apps を使用してドキュメントの編集したり表示することができないため、SharePoint 2013 ではシステム アカウントとしてログインしていないことを確認します。 Office ドキュメントが含まれている SharePoint 2013 ドキュメント ライブラリへ移動し、Word、PowerPoint、Excel、または OneNote のファイルを表示します。ブラウザーでドキュメントが開かれ、 Office Web Apps を使用してファイルが表示されます。

この手順が失敗する場合は、「Office Web Apps のエラーのトラブルシューティング」を参照してください。

## SharePoint 2013 と共に使用している Office Web Apps のエラーのトラブルシューティング

SharePoint 2013 と共に使用している Office Web Apps が正常に機能しない場合は、以下から該当する現象を見つけて、その見出しを展開し、トラブルシューティングの方法を確認してください。

## 問題: SharePoint ライブラリで 「新しいドキュメント」リンクを選択すると、新しい Office ドキュメントを作成するオプションが表示される代わりに、ドキュメントをアップロードするように求めるメッセージが表示されます。Office ドキュメントを選択 (シングルクリック) すると、ファイルがクライアント アプリケーションで開きます。Office ドキュメントのプレビューは表示されません。

以下に示すトラブルシューティングの方法を試してください。

**新しいドキュメントの作成に使われる SharePoint Web アプリケーションでクレーム ベース認証が使用されていることを確認する**

クレーム ベース認証を使用する Web アプリケーションでなければ Office Web Apps でファイルを開けません。Web アプリケーションの認証プロバイダーを確認するには、次の手順を実行します。

1.  SharePoint 2013 サーバーの全体管理 で、\[**Web アプリケーションの管理**\] をクリックします。

2.  確認したい Web アプリケーションを選択して、リボンの \[**認証プロバイダー**\] をクリックします。

認証プロバイダーが \[**クレーム ベース認証**\] と表示されていない場合は、Office Web Apps が Web アプリケーションと連携して正しく機能しません。この問題を解決するには、Web アプリケーションを削除し、クレーム ベース認証を使用して作成し直すか、またはWeb アプリケーションの認証方式を変更します。詳細については、「[Office Web Apps の SharePoint 認証の要件](plan-office-web-apps-used-with-sharepoint-2013.md)」を参照してください。

**SharePoint 2013 と、Office Web アプリケーション サーバーのファームで WOPI ゾーンが一致するかどうかを確認します。**

これを行うには、SharePoint Server で以下のコマンドを実行します。

    Get-SPWopiZone 

結果は次のいずれかになります。

  - internal-https

  - internal-http

  - external-https

  - external-http

次に、SharePoint Server で以下のコマンドを実行します。

    Get-SPWOPIBinding

出力の中で **WopiZone: *ゾーン*** を見つけます。Get-SPWopiZone の実行結果が Get-SPWOPIBinding によって返されたゾーンと一致しない場合は、SharePoint Server で **Set-SPWOPIZone -Zone** コマンドレットを実行して、Get-SPWOPIBinding の実行結果と一致するように WOPI ゾーンを変更する必要があります。これらのコマンドレットの使い方については、「[Get-SPWOPIBinding](get-spwopibinding.md)」、「[Set-SPWOPIBinding](set-spwopibinding.md)」、および「[Get-SPWOPIZone](get-spwopizone.md)」を参照してください。

## 問題: Office Web Apps で Office 文書を編集しようとすると、\[申し訳ございません。この文書を開いて編集することはできません。\] というエラー が表示される。

Active Directory (AD) セキュリティ グループのメンバーであるユーザーは、ブラウザーで文書を編集できない場合があります。これを解決するには、User Profile Service アプリケーション (UPA) が正しく構成されており、ユーザーやグループ メンバーと完全に同期していることを確認してください。詳細については、サポート技術情報の記事「[SharePoint 2013 で、セキュリティ グループのメンバーであるユーザーが Office Web Apps 2013 ファイルを編集できない](http://support.microsoft.com/kb/2908321?ln=ja-jp)」を参照してください。

## 問題: Office Web Apps で Office ドキュメントを表示しようとすると、「申し訳ございません。何らかの問題が発生しました。」というエラーが表示される。

ドキュメントの編集も表示もできないため、システム アカウントでログインしていないことを確認します。別のユーザーとしてログインし、もう一度 Office Web Apps にアクセスします。

## 問題: Office Web Apps で Office ドキュメントを表示しようとすると、「申し訳ございません。問題が発生したため、このドキュメントを開くことができません。」 というエラーが表示される。

HTTP を使用するテスト環境で Office Web Apps をセットアップした場合は、「手順 5: SharePoint 2013 で AllowOAuthOverHttp の設定を True に変更する」で説明しているように AllowOAuthOverHttp が \[**True**\] に設定されていることを確認します。

[New-OfficeWebAppsHost](new-officewebappshost.md) コマンドレットを使用して許可リストにドメインを追加した場合は、許可リストにあるホスト ドメインから Office Web Apps にアクセスしているか確認します。許可リストのホスト ドメインを表示するには、Office Web Apps サーバー で管理者として Windows PowerShell プロンプトを開き、[Get-OfficeWebAppsHost](get-officewebappshost.md) コマンドレットを実行します。 許可リストにドメインを追加するには、[New-OfficeWebAppsHost](new-officewebappshost.md) コマンドレットを使用します。

## 問題: Office Web Apps で Office ドキュメントを表示しようとすると、「申し訳ございません。サービスがビジー状態のため、このドキュメントを Word Web App で開くことができません。しばらくしてから、もう一度お試しください。」というエラーが出る。

  - ドメイン コントローラーに Office Web Apps サーバー をインストールしていませんか。Office Web Apps サーバー はドメイン コントローラーでは実行できません。Office Web Apps サーバー は、ドメインに含まれる別のサーバーにインストールする必要があります。詳細については、「[Office Web Apps Server のソフトウェア、ハードウェア、および構成の要件](plan-office-web-apps-server.md)」を参照してください。

  - SharePoint 2013 ビルド 15.0.4420.1017 以降が動作していることを確認してください。ビルド番号を確認するには、SharePoint 2013 サーバーで以下の手順を実行します。
    
    1.  \[**スタート**\] \> \[**すべてのプログラム**\] \> \[**Microsoft SharePoint 2013 製品**\] \> \[**SharePoint 2013 サーバーの全体管理**\] の順にポイントします。
    
    2.  \[**システム設定**\] \> \[**このファームのサーバーの管理**\] の順に選択します。
    
    \[**構成データベースのバージョン**\] が **15.0.4420.1017** 以降であることを確認します。そうでない場合は、「[Office、Office サーバー、および関連製品の Update Center](http://go.microsoft.com/fwlink/p/?linkid=160585)」で詳細を参照してください。

## 問題: ユーザーが生成した URL を使用して Office Web Apps で Office ドキュメントを表示しようとすると、「ファイルが見つかりません。元のファイルの URL が無効であるか、ドキュメントが公開されていません。URL が正しいことを確認し、ドキュメントの所有者にお問い合わせください。」 というエラーが出る。

ユーザーが生成した URL から、10 MB より大きなファイル サイズのドキュメントを開こうとしていませんか? ドキュメントが 10 MB を超えていないことを確認してください。

## 問題: SharePoint 2013 で Office ドキュメントのプレビューが表示されない。代わりに、「このコンテンツはフレーム内で表示できません」というエラーが表示される。

メモリが不足していると、Office ドキュメントのプレビューで問題が生じることがあります。「[Web サーバー、アプリケーション サーバー、および単一サーバー インストールのハードウェア要件](https://technet.microsoft.com/ja-jp/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)」に記載されている SharePoint 2013 のメモリ要件を確認してください。Office Web Apps サーバー にも同じ要件が適用されます。

## 問題: 「データ接続の設定では常に接続ファイルを使うようになっていますが、{0:ExcelWebApp} は外部の接続ファイルをサポートしていません。次の接続の更新に失敗しました: データ接続」 というエラーが出る。

このエラーは、データ接続情報が格納されている Office データ接続 (ODC) ファイルを Office Web Apps サーバーがサポートしていないために発生します。この問題を解決するには、次の手順を実行します。

1.  Excel クライアント アプリケーションでブックを開きます。

2.  \[**データ**\] \> \[**接続**\] をクリックします。

3.  メッセージに表示されているデータ接続を選択し、\[**プロパティ**\] をクリックします。

4.  \[**定義**\] タブをクリックします。

5.  \[**常に接続ファイルのチェック ボックスを使用する**\] のチェックボックスをオフにします。

6.  ブックを再度 SharePoint ドキュメント ライブラリにアップロードします。

ブラウザー ウィンドウでデータ モデルまたは Power View ビューが含まれるブックを操作できるようにするには、ブックが表示されるように SharePoint Server で Excel Services を構成します。これを行うには、SharePoint Server がインストールされているサーバーで SharePoint 管理者が New-SPWOPISupressionSetting コマンドレットを実行する必要があります。詳細については、「[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)」および「[SharePoint Server 2013 で Excel Services を管理する](https://technet.microsoft.com/ja-jp/library/ee681487\(v=office.15\))」を参照してください。

## Office Web Apps サーバーからの SharePoint 2013 の切断

何らかの理由で Office Web Apps サーバー から SharePoint 2013 の接続を切断する場合は、次のコマンドを使用します。

    Remove-SPWOPIBinding -All:$true

ヘルプ情報については、「[Remove-SPWOPIBinding](remove-spwopibinding.md)」を参照してください。

## 関連項目


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIZone](set-spwopizone.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps サーバーの展開](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

