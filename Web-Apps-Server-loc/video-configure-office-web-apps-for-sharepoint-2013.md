---
title: 'ビデオ: SharePoint 2013 の Office Web アプリケーションを構成します。'
TOCTitle: 'ビデオ: SharePoint 2013 の Office Web アプリケーションを構成します。'
ms:assetid: 0c02633f-3839-448b-ae83-24f24c254179
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn455088(v=office.15)
ms:contentKeyID: 59143114
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# ビデオ: SharePoint 2013 の Office Web アプリケーションを構成します。

 

_**適用先:**Office Web Apps, Office Web Apps Server, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2016-12-16_

**概要:** SharePoint 2013 と共用するための Office Web Apps サーバー ファームを構成する、9 つの手順を追って説明します。

SharePoint 2013 用の Office Web Apps の構成はとても簡単なプロセスです。このビデオでは、 Office Web Apps サーバー の設定方法およびテスト環境で Office Web Apps サーバー を使用するための SharePoint 2013 の構成方法を使用する方法をご参照いただけます。


**"SharePoint 2013 用に Office Web Apps を構成する" ビデオをご覧ください。**

> [!VIDEO https://www.microsoft.com/ja-jp/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

このビデオでは、 Office Web Apps サーバー を実行するサーバー、および SharePoint 2013 を実行するサーバーの 2 つのサーバーで実行される手順をご説明いたします。「[Office Web Apps Server のソフトウェア、ハードウェア、および構成要件](plan-office-web-apps-server.md)」で説明するように、これらの手順では別々のサーバーが必要となります。

**Office Web Apps サーバーを実行するサーバー上について、ビデオは次の方法を示します。**

1\. Windows PowerShell コマンド プロンプトを開き、Office Web Apps サーバー に必要な役割およびサービスをインストールします。「[Office Web Apps Server を実行するサーバーの準備](deploy-office-web-apps-server.md)」を参照してください。必要な役割およびサービスが見つからないとOffice Web Apps サーバー はインストールできないため、この手順が必要です。  
2\. [マイクロソフト ボリューム ライセンス サービス センター (VLSC)](http://go.microsoft.com/fwlink/p/?linkid=256561)から Office Web Apps サーバー ソフトウェアをインストールします。Office Web Apps サーバー をダウンロードするには、Office Professional Plus 2013、Office Standard 2013、または Office for Mac 2011 のボリューム ライセンス契約が必要です。ダウンロード ファイルは、VLSC ポータルにおいてそれらの Office 製品の下にあります。  
3\. [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) を使用して Office Web Apps サーバー ファームを作成します。  
4\. ブラウザー ウィンドウを開いて http://*ServerName*/hosting/discovery に移動し、Office Web Apps サーバー が正常に作成されたことを確認します。

**SharePoint 2013 を実行するサーバー上について、ビデオは次の方法を示します。**

5\. SharePoint 2013 管理シェル を開きます。  
6\. [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) を使用して、Office Web Apps サーバー と SharePoint 2013 の間のバインディングを作成します。これにより、 SharePoint 2013 を実行するサーバーと Office Web Apps サーバー を実行するサーバー間のコミュニケーションを設定します。  
7\. [Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps) を使用して、SharePoint 2013 の WOPI ゾーンを表示します。この設定では、2 つのサーバーが異なる WOPI ゾーンを使用していることが明確になります。つまり、SharePoint 2013 は internal-https、Office Web Apps サーバー は internal-http を使用します。正常に動作するために、ゾーンは Office Web Apps に合う必要があります。  
8\. [Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps) を使用して、SharePoint 2013 用に WOPI ゾーンを internal-http に変更します。  
9\. Office ドキュメントを SharePoint 2013 ドキュメント ライブラリで開いて、Office Web Apps が動作していることを確認します。

これらの各手順についての詳細は、「[Office Web Apps サーバーの展開](deploy-office-web-apps-server.md)」および「[SharePoint 2013 の Office Web アプリケーションを構成します。](configure-office-web-apps-for-sharepoint-2013.md)」の記事の中にある次のセクションを参照してください。

  - [Office Web Apps Server を実行するサーバーの準備](deploy-office-web-apps-server.md)

  - [Depl テスト環境での単一サーバー Office Web Apps Server ファームの展開](deploy-office-web-apps-server.md)

  - [Office Web Apps サーバーを使用するための SharePoint 2013 の構成の準備](configure-office-web-apps-for-sharepoint-2013.md)

  - [HTTP を使用するテスト環境で Office Web Apps サーバーを使用するための SharePoint 2013 の構成](configure-office-web-apps-for-sharepoint-2013.md)

## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)](plan-office-web-apps-used-with-sharepoint-2013.md)  
[内部設置型 Office Web Apps が SharePoint 2013 で機能する方法](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

