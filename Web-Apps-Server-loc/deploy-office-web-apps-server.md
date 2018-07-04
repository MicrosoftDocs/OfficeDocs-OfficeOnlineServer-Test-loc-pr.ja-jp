---
title: Office Web Apps サーバーの展開
TOCTitle: Office Web Apps サーバーの展開
ms:assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219455(v=office.15)
ms:contentKeyID: 48796452
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps サーバーの展開

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2017-10-05_

**概要:** SharePoint 2013 および Lync Server 2013 で使用するため、オンプレミスの Office Web Apps サーバーを展開する方法を説明します。

**対象ユーザー:** IT 担当者

この記事では、企業で Office Web Apps サーバーをインストールすることについて説明します。Office または Office Web Apps の個人用コピーに関するヘルプは、<https://support.office.com> をご覧ください。

[Office Web Apps サーバー](office-web-apps-server-overview.md) の展開iには、前提条件となるソフトウェアのインストールおよび いくつかの Windows PowerShell コマンドの実行が含まれますが、全体的にそのプロセスはとても簡単に設計されています。この記事では、サーバーの準備をする手順を追って説明し、Office Web Apps サーバー ファームを構成するための Windows PowerShell コマンドを提供します。

この記事の内容

  - ビデオを見てその方法を参照します。

  - 開始する前に、これらのリソースを確認します。

  - Office Web Apps サーバー を実行するサーバーの準備

  - Office Web アプリケーション サーバー ファームを展開します。

  - 「500 Web サービスの例外」 または 「500.21 - 内部サーバー エラー」メッセージが表示される場合

## ビデオを見てその方法を参照します。

次のビデオを見て、テスト環境で Office Web Apps サーバー を設定する方法を参照してください。また、Office Web Apps サーバーを使うために SharePoint 2013 を構成する方法をプレビューで見ることもできます。

**テスト環境での Office Web アプリケーション サーバーの設定します。**

> [!VIDEO https://www.microsoft.com/ja-jp/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

## 開始する前に、これらのリソースを確認します。

はじめにこれらのリソースを参照を取得したかどうかを確認します。

  - ハードウェアとソフトウェアの要件の詳細については、「[Office Web Apps サーバーの計画](plan-office-web-apps-server.md)」を参照してください。

  - 既定では、Office Web Apps サーバー で Office ファイルを表示できますが、編集はできません。ファイルを編集するには、編集ライセンスが必要ですが、これについては、「[Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)](plan-office-web-apps-used-with-sharepoint-2013.md)」および「[ライセンスを構成する (SharePoint Server 2013)](https://technet.microsoft.com/ja-jp/library/jj219627\(v=office.15\))」を参照してください。


> [!NOTE]
> すべての Office 2013 スイート で、マウス、キーボード ショートカット、またはタッチを使用してタスクを実行できます。Office 製品およびサービスでキーボード ショートカットとタッチを使用する方法については、「<A href="https://go.microsoft.com/fwlink/p/?linkid=249150">キーボード ショートカット</A>」と「<A href="https://go.microsoft.com/fwlink/p/?linkid=253163">Office タッチ ガイド</A>」を参照してください。



## Office Web Apps サーバー を実行するサーバーの準備

Office Web Apps サーバー を実行するすべてのサーバーでこれらの手順を実行します。

**図: Office Web アプリケーション サーバーのサーバーを準備する手順**

![Office Web Apps サーバー用のサーバーを準備するための 3 つの主な手順](images/JJ219455.af2a4690-4f8b-42c3-aab5-f7066bc0a936(Office.15).gif "Office Web Apps サーバー用のサーバーを準備するための 3 つの主な手順") 

## 手順 1: Office Web Apps サーバー の前提条件となるソフトウェアをインストールする

Windows Server 2008 R2、Windows Server 2012、および Windows Server 2012 R2 では前提条件が多少異なります。お使いのオペレーティング システムに合った正しいソフトウェアをインストールするために、適切な手順を選択してください。

**Windows Server 2008 R2 上**

1.  以下のソフトウェアをインストールします。
    
      - [Windows 7 および Windows Server 2008 R2 Service Pack 1 (KB976932)](http://go.microsoft.com/fwlink/p/?linkid=252370)
    
      - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=256560)
    
      - [Windows PowerShell 3.0](https://go.microsoft.com/fwlink/p/?linkid=244693)
    
      - [Windows 7 SP1 および Windows Server 2008 R2 SP1 用のプラットフォーム更新プログラムについて (KB2670838)](https://go.microsoft.com/fwlink/p/?linkid=293629)

2.  管理者として Windows PowerShell プロンプトを開き、次のコマンド例を実行して必要な役割とサービスをインストールします。
    
        Import-Module ServerManager
    
    次に、次のコマンドを実行します。
    
        Add-WindowsFeature Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,Web-Security,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Console,Ink-Handwriting,IH-Ink-Support,NET-Framework,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-Win-CFAC
    
    メッセージが表示されたら、サーバーを再起動します。

**Windows Server 2012 上**

1.  Windows PowerShell プロンプトを管理者として開き、このコマンドを実行して必要な役割とサービスをインストールします。
    
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    
    メッセージが表示されたら、サーバーを再起動します。

**Windows Server 2012 R2 上**

1.  以下のソフトウェアをインストールします。
    
      - [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?linkid=510096)

2.  Windows PowerShell プロンプトを管理者として開き、このコマンドを実行して必要な役割とサービスをインストールします。
    
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    
    メッセージが表示されたら、サーバーを再起動します。

## 手順 2: Office Web Apps サーバーと関連する更新プログラムをインストールする

Office Web Apps サーバー を実行するすべてのサーバーで以下の手順を完了します。

1.  [ボリューム ライセンス サービス センター (VLSC)](https://go.microsoft.com/fwlink/p/?linkid=256561) から Office Web Apps サーバーをダウンロードします。Office Web Apps サーバーをダウンロードするには、Office Professional Plus 2013、Office Standard 2013、Office for Mac 2011 のためのボリューム ライセンス条項に従ったライセンスが必要です。ダウンロード ファイルは、VLSC ポータルにおいて、それらの Office 製品の下にあります。

2.  次のいずれかを実行します。
    
      - Windows Server 2012 または Windows Server 2012 R2 の場合は, .img ファイルを直接開いて、**Setup.exe** を実行します。
    
      - Windows Server 2008 R2 SP1 の場合は, .img ファイルをマウントまたは展開できるプログラムを使用します。次に、**Setup.exe** を実行します。

3.  \[**マイクロソフト ソフトウェア ライセンス条項をお読みください**\] ページで、\[**「マイクロソフト ソフトウェア ライセンス条項」に同意します**\] を選択し、\[**続行**\] を選択します。

4.  \[**ファイルの場所を選択してください**\] ページで、Office Web Apps サーバー ファイルのインストール先 (たとえば C:\\Program Files\\Microsoft Office Web Apps など) を選択して、 \[**今すぐインストール**\] を選択します。指定したフォルダーが存在しない場合は、セットアップによってフォルダーが作成されます。
    
    Office Web Apps サーバー は、システム ドライブにインストールすることをお勧めします。

5.  Office Web Apps サーバー のインストールが終了したら、\[**閉じる**\] を選択します。

6.  [Office Web Apps サーバー SP1](https://go.microsoft.com/fwlink/p/?linkid=510097) (Windows Server 2012 と Windows Server 2008 R2 SP1 の場合は推奨。Windows Server 2012 R2 の場合は必須) をダウンロードしてインストールします。
    

    > [!NOTE]
    > 後で Office Web Apps サーバー SP1 を適用する場合は、<A href="apply-software-updates-to-office-web-apps-server.md">Office Web Apps サーバーへのソフトウェアの更新プログラムの適用</A> の指示に従ってください。



7.  最新の Office Web Apps サーバー 更新プログラムを確認するには、[Office、Office サーバー、関連製品の TechNet Update center](https://go.microsoft.com/fwlink/p/?linkid=280271) の一覧を参照してください。
    

    > [!NOTE]
    > Office Web Apps サーバー SP1 をインストールしていない場合は、<A href="https://go.microsoft.com/fwlink/p/?linkid=296579">KB2810007</A> を適用します。



## 手順 3: Office Web Apps サーバー の言語パックをインストールする

Office Web Apps サーバー 2013 言語パックを使用すると、SharePoint 2013 ドキュメント ライブラリ、 Outlook Web Access (添付ファイルのプレビューとして)、および Lync 2013 (PowerPoint ブロードキャストとして ) における Web ベースの Office ファイルを複数の言語で表示できます。言語パックのしくみの詳細については、「[Office Web Apps サーバー プレビューの言語パックの計画](plan-office-web-apps-server.md)」を参照してください。

言語パックをインストールするには、次の手順を実行します。


1.  「[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?linkid=263945)」から Office Web Apps サーバーの言語パックをダウンロードします。

2.  **WebAppsServerLP\_en-us\_x64.exe** を実行します。

3.  Office Web Apps サーバー の言語パック 2013 ウィザードの \[**マイクロソフト ソフトウェア ライセンス条項をお読みください**\] ページで、\[**マイクロソフト ソフトウェア ライセンス条項」に同意します**\] を選択し、\[**続行**\] を選択します。

4.  Office Web Apps サーバー のインストールが終了したら、\[**閉じる**\] を選択します。


> [!IMPORTANT]
> <UL>
> <LI>
> <P>Office Web Apps サーバー ファームの作成後に言語パックをインストールするには、サーバーをファームから削除し、サーバーに言語パックをインストールした後、サーバーをファームに追加し直す必要があります。</P>
> <LI>
> <P>正常に動作するには、言語パックをファーム内のすべてのサーバーにインストールする必要があります。</P></LI></UL>



## Office Web アプリケーション サーバー ファームを展開します。

作成したい Office Web Apps サーバー ファームの種類に基づき、次の 3 つのセクションのうちの 1 つに従ってください。


> [!TIP]
> Windows PowerShell が実行された <STRONG>New-OfficeWebAppsFarm</STRONG> コマンドレットを認識しない場合は、<STRONG>OfficeWebApps</STRONG> モジュールをインポートする必要があります。次のコマンドを使用してください。<BR><CODE>Import-Module -Name OfficeWebApps</CODE>



## HTTP を使用する Office Web アプリケーション サーバー ファームの 1 台のサーバーを展開します。

Office Web Apps サーバー を展開するだけであれば、Office Web Apps サーバー の機能性をLync Server 2013に提供する必要はありません。ここでは、HTTP を使用する単一サーバーの Office Web Apps サーバーファームをインストールします。証明書やロード バランサーは必要ありませんが、他のサーバー アプリケーションを実行していない専用の物理サーバーまたは仮想マシン インスタンスが必要です。

この Office Web Apps サーバー ファームを使用して Office Web Apps の機能性を SharePoint 2013 に提供することができます。

**図: Office Web アプリケーション サーバーを展開する手順**

![単一サーバーの Office Web Apps サーバー ファームを展開するための 3 つの主な手順](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "単一サーバーの Office Web Apps サーバー ファームを展開するための 3 つの主な手順")

## 手順 1: Office Web Apps サーバー ファームを作成する

**New-OfficeWebAppsFarm** コマンドを使用して、次の例のような単一サーバーで構成される新しい Office Web Apps サーバー ファームを作成します。

    New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled

**パラメーター**

  - **–InternalURL** は、**http://servername** の様にOffice Web Apps サーバー を実行するサーバーの名前です。

  - **–AllowHttp** は HTTP を使用してファームを構成します。

  - **–EditingEnabled** を SharePoint 2013 で使用すると、Office Web Apps で編集できるようになります。このパラメーターを Lync Server 2013 で使用することはありません。このホストは編集をサポートしていないためです。

翻訳サービス、プロキシ サーバー、クリップ アート サポート、およびオンライン ビューアーを構成するその他のパラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

「500 Web サービスの例外」 または 「500.21 ? 内部サーバー エラー」メッセージが表示される場合

## 手順 2: Office Web Apps サーバー ファームが正常に作成されたことを確認する

ファームが作成されると、ファームの詳細が Windows PowerShell プロンプトに表示されます。 Office Web Apps サーバー が正しくインストールされて構成されたことを確認するには、以下の例のように、Web ブラウザーを使用して Office Web Apps サーバー の検出 URL にアクセスします。検出 URL は、Office Web Apps サーバー ファームを構成するときに指定した*InternalUrl* パラメーターと、その後ろに**/hosting/discovery** を付けたもので構成されます。例:

    http://servername/hosting/discovery

Office Web Apps サーバー が予期されるとおりに動作する場合は、Web ブラウザーに Web アプリ オープン プラットフォーム インターフェイス (WOPI) の検出 XML ファイルが表示されます。このファイルの先頭部分は以下のようになります。

    <?xml version="1.0" encoding="utf-8" ?> 
    - <wopi-discovery>
    - <net-zone name="internal-http">
    - <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
    <action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 

## 手順 3: ホストを構成する

ファームは、HTTP を介して Office Web Apps の機能をホストに提供する準備ができました。ホストを構成する方法の詳細については、「[SharePoint 2013 の Office Web アプリケーションを構成します。](configure-office-web-apps-for-sharepoint-2013.md)」を参照してください。

## HTTPS を使用する単一サーバー Office Web Apps サーバー ファームの展開

ほとんどの運用環境でのセキュリティ機能には、HTTPS の使用を強く推奨します。また、Office Web Apps サーバー の機能性を Lync Server 2013 に提供したい場合は、HTTPS が必要となります。これでユーザーは、ブラウザーで PowerPoint ブロードキャストを見ることができます。HTTPS を使用する単一サーバーの Office Web Apps サーバー ファームのインストール方法をここに示します。「[HTTPS を使用した Office Web Apps サーバー 通信の保護](plan-office-web-apps-server.md)」で説明しているように、サーバーに証明書をインストールしておく必要があります。

この Office Web Apps サーバー ファームを使用すると、Office Web Apps の機能性を SharePoint 2013 および Lync Server 2013 に提供できます。

**図: Office Web アプリケーション サーバーを展開する手順**

![単一サーバーの Office Web Apps サーバー ファームを展開するための 3 つの主な手順](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "単一サーバーの Office Web Apps サーバー ファームを展開するための 3 つの主な手順")

## 手順 1: Office Web Apps サーバー ファームを作成する

**New-OfficeWebAppsFarm** コマンドを使用して、次の例のような単一サーバーで構成される新しい Office Web Apps サーバー ファームを作成します。

    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled

**パラメーター**

  - **–InternalURL** は、**http://servername.contoso.com** などの Office Web Apps サーバー を実行するサーバーの完全修飾ドメイン名 (FQDN) です。

  - **–ExternalURL** は、インターネット上でアクセス可能な FQDN です。

  - **–CertificateName** は、証明書のフレンドリ名です。

  - **–EditingEnabled** はオプションで、SharePoint 2013 で使用すると、Office Web Apps で編集できるようになります。このパラメーターを Lync Server 2013 で使用することはありません。このホストは編集をサポートしていないためです。

翻訳サービス、プロキシ サーバー、クリップ アート サポート、およびオンライン ビューアーを構成するその他のパラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

「500 Web サービスの例外」 または 「500.21 ? 内部サーバー エラー」メッセージが表示される場合

## 手順 2: Office Web Apps サーバー ファームが正常に作成されたことを確認する

ファームが作成されると、ファームの詳細が Windows PowerShell プロンプトに表示されます。 Office Web Apps サーバー が正しくインストールされて構成されたことを確認するには、以下の例のように、Web ブラウザーを使用して Office Web Apps サーバー の検出 URL にアクセスします。検出 URL は、Office Web Apps サーバー ファームを構成するときに指定した*InternalUrl* パラメーターと、その後ろに**/hosting/discovery** を付けたもので構成されます。例:

    https://server.contoso.com/hosting/discovery

Office Web Apps サーバーが予期されるとおりに動作する場合は、Web ブラウザーに Web アプリ オープン プラットフォーム インターフェイス (WOPI) の検出 XML ファイルが表示されます。このファイルの先頭部分は以下のようになります。

``` 
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="xls"/><action name="view"
 
```


> [!NOTE]
> Web ブラウザーの設定によって設定によっては、検出 XML ファイルのコンテンツが表示される前に、<STRONG>すべてのコンテンツを表示</STRONG> を選択することを求めるメッセージが表示されることがあります。



## 手順 3: ホストを構成する

ファームは、HTTPS を介して Office Web Appsの機能をホストに提供する準備ができました。ホストの構成方法の詳細については、以下の記事を参照してください。

  - [SharePoint 2013 の Office Web アプリケーションを構成します。](configure-office-web-apps-for-sharepoint-2013.md)

  - [Lync Server 2013 と Office Web Apps サーバーの統合の構成](https://go.microsoft.com/fwlink/p/?linkid=256902)

## HTTPS を使用する負荷分散された複数サーバー Office Web Apps サーバー ファームの展開

Office Web Apps サーバー ファームに多数のトラフィックを見込み、内部ネットワークだけではなくインターネット上でも利用できるようにしたい場合、このタイプのトポロジーがぴったりです。 このセクションは、複数のサーバー ロード バランサーを HTTPS を使用する Office Web Apps サーバー ファームをインストールする方法を示しています。興味があれば、[このトポロジーについて読んでみてください](plan-office-web-apps-server.md)。

始める前に、「[Office Web Apps サーバーのロード バランサー要件](plan-office-web-apps-server.md)」で説明しているように、ロード バランサーが構成されていることを確認する必要があります。また、「[HTTPS を使用した Office Web Apps サーバーの通信の保護](plan-office-web-apps-server.md)」で説明しているように、ロード バランサーに証明書をインストールしておく必要があります。この Office Web Apps サーバー ファームを使用すると、Office Web Apps の機能性を SharePoint 2013 および Lync Server 2013 に提供できます。

**図: Office Web アプリケーション サーバーを展開する手順**

![複数サーバーの Office Web Apps サーバー ファームを展開するための 4 つの主な手順](images/JJ219455.4c4b31cb-961b-4efd-b755-a18bdcb5c191(Office.15).gif "複数サーバーの Office Web Apps サーバー ファームを展開するための 4 つの主な手順")

## 手順 1: 最初のサーバーで Office Web Apps サーバー ファームを作成する

**New-OfficeWebAppsFarm** コマンドを使用して、 、次の例のような最初のサーバーで新しい Office Web Apps サーバー ファームを作成します。

    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled

**パラメーター**

  - **–InternalURL** は、**http://servername.contoso.com** などの Office Web Apps サーバー を実行するサーバーの完全修飾ドメイン名 (FQDN) です。

  - **–ExternalURL** は、インターネット上でアクセス可能な FQDN 名です

  - **-SSLOffloaded** をロード バランサーの SSL ターミネーションのオフロードを有効にします。

  - **–EditingEnabled** はオプションで、SharePoint 2013 で使用すると、Office Web Apps で編集できるようになります。このパラメーターを Lync Server 2013 で使用することはありません。このホストは編集をサポートしていないためです。

翻訳サービス、プロキシ サーバー、クリップ アート サポート、およびオンライン ビューアーを構成するその他のパラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

「500 Web サービスの例外」 または 「500.21 - 内部サーバー エラー」メッセージが表示される場合

## 手順 2: ファームにサーバーを追加する

最初のサーバーが Office Web Apps サーバー を実行し始めたら、Office Web Apps サーバー ファームに追加する各サーバーで **New-OfficeWebAppsMachine** コマンドを実行します。 **–MachineToJoin**パラメーターで、 Office Web Apps サーバー ファームに既に存在するサーバーの コンピューター名を使用してください。たとえば、server1.contoso.com がファーム内に既にある場合は、次のように使用します。

    New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"

これらのパラメーターの詳細については、「[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)」を参照してください。

## 手順 3: Office Web Apps サーバー ファームが正常に作成されたことを確認する

ファームが作成されると、ファームの詳細が Windows PowerShell プロンプトに表示されます。 Office Web Apps サーバー が正しくインストールされて構成されたことを確認するには、以下の例のように、Web ブラウザーを使用して Office Web Apps サーバー の検出 URL にアクセスします。検出 URL は、Office Web Apps サーバー ファームを構成するときに指定した *InternalUrl* パラメーターと、その後ろに**/hosting/discovery** を付けたもので構成されます。例:

    https://server.contoso.com/hosting/discovery

Office Web Apps サーバー が予期されるとおりに動作する場合は、Web ブラウザーに Web アプリ オープン プラットフォーム インターフェイス (WOPI) の検出 XML ファイルが表示されます。このファイルの先頭部分は以下のようになります。

    <?xml version="1.0" encoding="UTF-8"?>
    <wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xlsb"/> 


> [!NOTE]
> Web ブラウザーの設定によっては、検出 XML ファイルのコンテンツが表示される前に、[<STRONG>すべてのコンテンツを表示</STRONG>] を選択することを求めるメッセージが表示されることがあります。



## 手順 4: ホストを構成する

ファームは、HTTPS を介して Office Web Appsの機能をホストに提供する準備ができました。ホストの構成方法の詳細については、以下の記事を参照してください。

  - [SharePoint 2013 の Office Web アプリケーションを構成します。](configure-office-web-apps-for-sharepoint-2013.md)

  - [Lync Server 2013 と Office Web Apps サーバーの統合の構成](https://go.microsoft.com/fwlink/p/?linkid=256902)

## 「500 Web サービスの例外」または 「500.21 – 内部サーバー エラー」メッセージが表示される場合

NET Framework 3.5 の機能がインストールされてから削除された場合は、OfficeWebApps コマンドレットを実行したときに「500 Web サービス例外」 または 「500.21 – 内部サーバー エラー」のメッセージが表示される場合があります。これを修正するには、管理者特権でのコマンド プロンプトから以下のサンプル コマンドを実行して Office Web Apps サーバー の正常な動作を妨げる可能性がある設定をクリーンアップします。

**Windows Server 2008 R2 の場合**

    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -iru

    iisreset /restart /noforce

**Windows Server 2012 または Windows Server 2012 R2 の場合**

    dism /online /enable-feature /featurename:IIS-ASPNET45

## 関連項目


[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps サーバーの計画](plan-office-web-apps-server.md)  
[SharePoint 2013 の Office Web アプリケーションを構成します。](configure-office-web-apps-for-sharepoint-2013.md)  


[Lync Server 2013 と Office Web Apps サーバーの統合の構成](https://go.microsoft.com/fwlink/p/?linkid=256902)  
  

[](configure-office-web-apps-for-sharepoint-2013.md)

