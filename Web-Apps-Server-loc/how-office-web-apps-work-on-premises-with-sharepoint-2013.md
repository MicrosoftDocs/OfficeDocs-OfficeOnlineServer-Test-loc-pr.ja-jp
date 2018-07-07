---
title: 内部設置型 Office Web Apps が SharePoint 2013 で機能する方法
TOCTitle: SharePoint 2013 と内部設置型  Office Web Apps
ms:assetid: 8480064e-14a4-4b46-ad6b-0c836b192af2
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ff431685(v=office.15)
ms:contentKeyID: 48796432
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# 内部設置型 Office Web Apps が SharePoint 2013 で機能する方法

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2016-12-16_

**概要:** Office Web Apps、Office Web Apps サーバー、およびそれらの内部設置型における SharePoint 2013 との連動方法について説明します。

**対象ユーザー:** IT 担当者

SharePoint Server 2013 と連動する場合、Office Web Apps サーバー によって Word Web App、Excel Web App、PowerPoint Web App、およびOneNote Web App の更新バージョンが提供されます。ユーザーは、コンピューターや多くのモバイル デバイス (Windows Phone、iPhone、iPad、Windows 8 タブレット、Android デバイスなど) でサポートされる Web ブラウザーを使用して、SharePoint ライブラリの Office ドキュメントを表示 (場合によっては編集) できます。


**図: さまざまなデバイスでの Office Web Apps の表示および編集の機能**

![さまざまなデバイスでの Office Web Apps の表示および編集の機能をまとめた図。タッチ スクリーン向けに最適化された機能が強調表示されています。](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "さまざまなデバイスでの Office Web Apps の表示および編集の機能をまとめた図。タッチ スクリーン向けに最適化された機能が強調表示されています。")

## Office Web Apps サーバー は、スタンドアロン サーバーとしてインストールされました。

Office Web Apps は、SharePoint 2013 を実行するサーバーにはインストールできません。かわりに、Office Web Apps サーバー を実行する 1 つ以上の物理または仮想サーバーを展開できます。その後、SharePoint 2013 ファームが Office Web Apps サーバー ファームを使用するように構成して、SharePoint ライブラリで Office ファイルを作成したり開いたりするユーザーに Office Web Apps の機能を提供します。詳細については、「[Office Web Apps サーバーの概要](office-web-apps-server-overview.md)」を参照してください。

## SharePoint 2013 を使用する場合の Office Web Apps のライセンスのオプション

Office Web Apps ライセンスには以下の 2 つのオプションがあります。

  - **表示のみ** 既定では、Office Web Apps は表示専用です。表示のみの機能は無料で提供されます。

  - **表示と編集**Office Web Apps の編集機能を SharePoint 2013 で使用するには、編集ライセンスを購入する必要があります。 Office Web Apps サーバー ファームを作成するときに編集を有効にします。

ボリューム ライセンス プログラムで Office 2013 のライセンスを取得している組織は、社内の SharePoint 2013 で Office Web Apps の編集機能を有効にできます。これによってユーザーは、自宅など Office クライアントがインストールされていない場所でも Office 編集機能を使用できるようにできます。Office Web Apps の編集ライセンスを個別に購入することはできません。

ライセンスの詳細については、Office Web Apps サーバー をインストールすると表示されるマイクロソフト ソフトウェア ライセンス条項を参照してください。

SharePoint 2013 では、Office Web Apps を使用するための新しいライセンス契約が提供されます。SharePoint ライセンスを有効にしてから Office Web Apps の編集を有効にすると、適切なライセンスを持つユーザーのみがブラウザーで実際に Office ファイルを編集できます。Office Web Apps の編集ライセンスがユーザーに適用されない場合は、表示しかサポートされません。

SharePoint 2013 でのライセンスのしくみの詳細については、「[ライセンスを構成する (SharePoint Server 2013)](https://technet.microsoft.com/ja-jp/library/jj219627\(v=office.15\))」を参照してください。 編集を有効にする EditingEnabled パラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) 」および「[Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps)」を参照してください。

SharePoint 2013 のリンク機能で送信されるファイルは、編集ライセンスがない場合や、Office Web Apps サーバー ファームで編集が無効になっている場合でも、Office Web Apps で編集できます。

## Office Mobile Viewer を使用して SharePoint サイト上のファイルにアクセスする

Office Web Apps サーバー が Office Mobile Viewer を提供することで、SharePoint Server サイトにアクセスするモバイル ユーザーは Office Web Apps を利用できるようになります。既定では Office Mobile Viewer は有効になっていますが、SharePoint Server のサイト管理者によって無効にすることができます。有効であるとき、ユーザーは、モバイル デバイスのブラウザーで SharePoint Server サイトに移動でき、 SharePoint Server ライブラリで開きたいドキュメントをタップすると、そのドキュメントはモバイル ブラウザーで開きます。

モバイル デバイスの SharePoint ライブラリについての詳細は、「[What's new for mobile devices in SharePoint 2013](https://technet.microsoft.com/ja-jp/library/fp161352\(v=office.15\))」および「[モバイル デバイスと SharePoint Server 2013 の概要](https://technet.microsoft.com/ja-jp/library/fp161351\(v=office.15\))」を参照してください。モバイル デバイスでの Office Mobile Viewer の使用方法の詳細は、「[Android、iPhone、または Windows Phone で Office Web Apps を使う](http://go.microsoft.com/fwlink/p/?linkid=271045)」を参照してください。SharePoint 2013 の Office Mobile Viewer を無効にするには、[Remove-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps) コマンドレットを使用します。

## SharePoint での Excel Web App と Excel Services の相違点

SharePoint の Excel Web App と Excel Services には多くの共通点がありますが、同じではありません。 Excel Services は Enterprise エディション の SharePoint Server 2013 でのみ使用できます。Excel Web App は、SharePoint Server 2013 および SharePoint Foundation 2013 で使用できます。どちらのアプリケーションでも、ブラウザー ウィンドウでワークブックを表示することができ、データの操作や参照を行うことができます。

SharePoint の Excel Web App と Excel Services には明らかな違いがあります。例えば、Excel Services では外部データ接続、データ モデル、およびデータ モデルを使用するアイテム (ピボットグラフ レポート、ピボットテーブル レポート、タイムライン コントロールなど) を操作する機能がサポートされています。. Excel Services は Excel Web App より多くのビジネス インテリジェンス機能を備えていますが、Excel Services ではブラウザー ウィンドウでワークブックの作成や編集を行うことはできません。

Excel Web App と Excel Servicesの相違点に関する詳細は、「[SharePoint Server 2013 の Excel Services の概要](https://technet.microsoft.com/ja-jp/library/ee424405\(v=office.15\))」および 「[SharePoint の Excel Services と Excel Web App の比較](http://go.microsoft.com/fwlink/p/?linkid=255460)」を参照してください。

組織において、ブラウザーでブックを表示するために Excel Web Appではなく Excel Servicesの使用することにした場合、Windows PowerShell の **New-SPWOPISuppressionSettings** コマンドレットを使用して、Excel ブックに対して Excel Web App をオフにすることができます。詳細については、「[New-SPWOPISuppressionSetting](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps)」を参照してください。

## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)](plan-office-web-apps-used-with-sharepoint-2013.md)  
  

[](plan-office-web-apps-used-with-sharepoint-2013.md)

