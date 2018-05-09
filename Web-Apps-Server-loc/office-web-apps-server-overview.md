---
title: Office Web Apps サーバーの概要
TOCTitle: '概要: Office Web Apps サーバー'
ms:assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219437(v=office.15)
ms:contentKeyID: 48796423
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps サーバーの概要

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2017-05-26_

**概要:** Office Web Apps サーバーの概要と、Office Web Apps サーバーがサポート対象のホストに提供するブラウザー ベースの Office 機能について説明します。

**対象ユーザー:** IT 担当者

Office Web Apps サーバーは、ブラウザー ベースのバージョンの Word、PowerPoint、Excel、および OneNote を提供する新しい Office サーバー製品です。単一の Office Web Apps サーバー ファームで、SharePoint 2013、Lync Server 2013、共有フォルダー、および Web サイトを通じて Office ファイルにアクセスするユーザーをサポートできます。この新しいスタンドアロンの展開モデルを使用すると、Office Web Apps サーバーファームに対する更新を、組織に展開されている他の Office サーバー製品から独立して管理できます。


> [!IMPORTANT]
> この記事は、<A href="content-roadmap-for-office-web-apps-server.md">Office Web Apps サーバーのコンテンツ ロードマップ</A>に含まれています。このロードマップは、Office Web Apps サーバー の展開と管理に役立つ記事、ダウンロード、ビデオなどを参照する際の出発点として使用します。<BR><STRONG>使用しているデスクトップまたはモバイル デバイスの Office Web Apps に関する情報</STRONG>をお探しの場合は、<A href="https://go.microsoft.com/fwlink/p/?linkid=32496">Office.com</A> で「Office Web Apps」を検索してください。



この記事の内容

  - Office Web Apps サーバーについて

  - SharePoint 2013 が Office Web Apps サーバーを使用して Office ドキュメントを表示および編集する方法

  - Lync Server 2013 が Office Web Apps サーバーを使用して PowerPoint ブロードキャストを表示する方法

  - Office Web Apps サーバーでオンライン ビューアーを使用して共有フォルダーや Web サイトの Office ファイルを表示する方法

## Office Web Apps サーバーについて

Office Web Apps サーバー は、Office ファイルのブラウザー ベースでの表示と編集のサービスを提供する Office サーバー製品です。Office Web Apps サーバー は、WOPI (Web アプリ オープン プラットフォーム インターフェイス) プロトコルをサポートする製品およびサービスと連動しています。ホストと呼ばれるこれらの製品には、SharePoint 2013 および Lync Server 2013 が含まれます。Office Web Apps サーバー ファームは、Office サービスをオンプレミスの複数のホストに提供できます。また、組織のニーズの拡大に合わせて、ファームを 1 サーバーから複数サーバーに拡張できます。Office Web Apps サーバー には、他のサーバー アプリケーションが実行していない専用サーバーが必要ですが、代わりに、仮想マシン インスタンスにOffice Web Apps サーバー をインストールすることもできます。

Office Web Apps はスタンドアロン製品となったため、組織での展開と管理が容易になりました。たとえば、SharePoint 2013 を展開する場合に、Office Web Apps (以前のバージョンでは SharePoint Server 2010 と密接に統合されていた) をサポートするために SharePoint インフラストラクチャを最適化する必要がありません。また、Office Web Apps サーバー ファームに更新を適用するときに、SharePoint または Lync Server とは別に異なる頻度で行うこともできます。また、スタンドアロン Office Web Apps サーバー ファームでは、SharePoint Server の外部 (共有フォルダーや他の Web サイトなど) に格納されている Office ファイルをユーザーが表示および編集できます。この機能はオンライン ビューアーによって提供されます。

以下の図は、Office Web Apps の以前の展開モデルと Office Web Apps の新しいスタンドアロン展開モデルの違いを示しています。

**Office Web Apps の展開モデルの違い**

![Office Web Apps サーバーの以前の展開モデルと新しいスタンドアロン展開モデルの違いを示しています](images/JJ219437.f16dd9d1-c9b7-4c8b-a8de-f1f82c0ee1e2(Office.15).gif "Office Web Apps サーバーの以前の展開モデルと新しいスタンドアロン展開モデルの違いを示しています")

## SharePoint 2013 が Office Web Apps サーバーを使用して Office ドキュメントを表示および編集する方法

SharePoint Server 2013 と連動する場合、Office Web Apps サーバー によって Word Web App、Excel Web App、PowerPoint Web App、および OneNote Web App の更新バージョンが提供されます。ユーザーは SharePoint ライブラリの Office ドキュメントを表示 (場合によっては編集) するために、コンピューターや多くのモバイル デバイス (Windows Phone、iPhone、iPad、Windows 8 タブレットなど) でサポートされる Web ブラウザーを使用します。Office Web Apps の豊富な新機能の中には、改善されたタッチ サポートや編集機能が含まれ、iPad や Windows 8 タブレットのユーザーは Office ドキュメントの編集や表示をデバイスで直接行うことができます。

以下の図では、さまざまなデバイスでの Office Web Apps の表示および編集機能を要約しています。

**Office Web Apps の表示と編集の機能**

![さまざまなデバイスでの Office Web Apps の表示および編集の機能をまとめた図。タッチ スクリーン向けに最適化された機能が強調表示されています。](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "さまざまなデバイスでの Office Web Apps の表示および編集の機能をまとめた図。タッチ スクリーン向けに最適化された機能が強調表示されています。")


> [!NOTE]
> PowerPoint ブロードキャストは SharePoint 2013 から削除されました。これは OneDrive および Lync Server 2013 で使用できます。



Office Web Apps の新機能の詳細については、「[内部設置型 Office Web Apps が SharePoint 2013 で機能する方法](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)」を参照してください。

## Lync Server 2013 が Office Web Apps サーバーを使用して PowerPoint ブロードキャストを表示する方法

Lync Server 2010 では、PowerPoint プレゼンテーションは 2 つの方法のいずれかで表示されます。Lync 2010 を実行するユーザーの場合、PowerPoint プレゼンテーションは、PowerPoint 97-2003 形式で、埋め込みの PowerPoint Viewer を使用して表示されます。Lync Web App を実行するユーザーの場合、PowerPoint プレゼンテーションは動的 HTML ファイルに変換されてから、カスタマイズされた DHTML ファイルと Silverlight の組み合わせを使用して表示されます。この方法は通常は有効ですが、いくつかの制限がありました。

  - 埋め込み PowerPoint Viewer (より優れた表示機能を提供) を使用できるのは Windows プラットフォームのみです。

  - 多くのモバイル デバイス (広く普及している携帯電話の一部を含む) では Silverlight はサポートされていません。
    
    PowerPoint Viewer でも DHTML/Silverlight の方法でも、最新版の PowerPoint で提供されるすべての機能 (画面切り替えや埋め込みビデオなど) がサポートされるわけではありません。

このような問題に対処するため、また PowerPoint プレゼンテーションを提供または表示するユーザーのエクスペリエンスを改善するために、Lync Server 2013は Office Web Apps サーバーを使用して PowerPoint プレゼンテーションを処理します。この新しい方法により、特に以下の機能が実現されています。

  - 高解像度表示、および PowerPoint 機能 (アニメーション、画面切り替え、埋め込みビデオなど) の十分なサポート。

  - このようなプレゼンテーションにアクセスできるモバイル デバイスが増加しています。Lync Server 2013は、カスタマイズされた DHTML と Silverlight ではなく標準 DHTML と JavaScript を使用して PowerPoint プレゼンテーションをブロードキャストするためです。

  - 適切な権限を持つユーザーが、PowerPoint プレゼンテーションを、プレゼンテーションそのものとは別にスクロール表示できます。たとえば、Ken Myer が自分のスライド ショーを提示しているときに、Pilar Ackerman は必要なスライドをスクロールして表示できます。Ken のプレゼンテーションにはまったく影響しません。

Office Web Apps サーバー を使用するように Lync Server 2013 を構成する方法の詳細については、「[Lync Server 2013 と Office Web Apps サーバーの統合の構成](https://go.microsoft.com/fwlink/p/?linkid=25690)」を参照してください。

## Office Web Apps サーバーでユーザーがオンライン ビューアーを使用して共有フォルダーや Web サイトの Office ファイルを表示する方法

オンライン ビューアーにより、ユーザーは Web ブラウザーを使用して、組織の Web サイトまたは共有フォルダーに格納されている Excel、PowerPoint、および Word ファイルを表示できます。ユーザーは、Office ファイルを Web ブラウザーで表示でき、別のアプリケーションを開く必要はありません。さらに、オンライン ビューアーでは、Office 2013をユーザーのコンピューターにインストールする必要もありません。また、リンク (すなわち Web ページへの URL の埋め込み) に必要なコードも生成されます。オンライン ビューアーはイントラネットでもインターネットでも使用できます。

Office Web Apps サーバー で提供されるページ (http://\<Office Web Apps サーバー名\>/op/generate.aspx) を使用して、UNC または URL アドレスの公開ドキュメントへのリンクを生成できます。生成された URL をユーザーが選択すると、オンライン ビューアーにより、Office Web Apps サーバー がファイルをその場所から取得し、Office Web Apps を使用して表示できます。ユーザーは、Word、Excel、または PowerPoint ファイルを Office 機能を備えたブラウザーで表示できます。Word 文書の書式やレイアウトは維持され、Excel ブックのデータはフィルター処理や並べ替えを行うことができます。PowerPoint プレゼンテーションではアニメーションが再生されます。ただし、オンライン ビューアーではファイルを表示できますが、編集はできないことに注意してください。また、認証を必要とするファイルをオンライン ビューアーで開くことはできません。

オンライン ビューアーの詳細については、「[オンライン ビューアーの計画](plan-office-web-apps-server.md)」を参照してください。


> [!NOTE]
> Microsoft では、URLの作成のインターネット専用バージョンを <A href="http://go.microsoft.com/fwlink/?linkid=256548%26clcid=0x41">Office.com</A> で提供しています。



## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps サーバーの計画](plan-office-web-apps-server.md)  
[Office Web Apps サーバーの展開](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

