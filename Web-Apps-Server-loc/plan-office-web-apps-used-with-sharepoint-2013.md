---
title: Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)
TOCTitle: Office Web Apps の計画
ms:assetid: 3bd0a617-5f12-4a7e-bb75-b15c86c7e504
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ff431682(v=office.15)
ms:contentKeyID: 48796422
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2016-12-16_

**概要:** Office Web Apps を社内の SharePoint 2013 と組み合わせて使用するための計画のガイダンスを示します。

**対象ユーザー:** IT 担当者

Office Web Apps を社内の SharePoint 2013 と組み合わせて使用する方法を計画するには、Office Web Apps を使用して Office ファイルを表示および編集するためのブラウザー サポート、SharePoint 認証の要件、およびライセンスの考慮事項を確認する必要があります。さらに、SharePoint 2013 ドキュメント ライブラリにある Office ファイルをユーザーが開くときに、Web ブラウザーとクライアント アプリケーションのどちらを SharePoint 2013 で使用するかを決定します。


> [!IMPORTANT]
> この記事は、<A href="content-roadmap-for-office-web-apps-server.md">Office Web Apps サーバーのコンテンツ ロードマップ</A>に含まれています。このロードマップは、Office Web Apps サーバー の展開と管理に役立つ記事、ダウンロード、ビデオなどを参照する際の出発点として使用します。<BR><STRONG>使用しているデスクトップまたはモバイル デバイスの Office Web Apps に関する情報</STRONG>をお探しの場合は、<A href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</A> で「Office Web Apps」を検索してください。



この記事の内容

  - Office Web Apps の計画について

  - Office Web Apps のブラウザー サポート

  - Office Web Apps の SharePoint 認証の要件

  - Office ファイルを編集するための Office Web Apps のライセンス

  - Office Web Apps を SharePoint 2010 と組み合わせて展開している場合の考慮事項

  - SharePoint 2013 ドキュメント ライブラリからドキュメントを開くときの既定のオープン動作

## Office Web Apps の計画について

この記事のガイダンスは、組織の事業所に Office Web Apps サーバーを展開する際に作成する計画に含まれます。たとえば、ハードウェア、ソフトウェア、および仮想化の要件、ファーム規模とトポロジ、セキュリティは、すべて Office Web Apps サーバー計画の一部です。これらの決定を行った後で、SharePoint 2013に関する Office Web Appsの機能の構成を計画できます。Office Web Apps サーバーそのものや、その要件や計画のガイダンスについては、「[Office Web Apps サーバーの概要](office-web-apps-server-overview.md)」および「[Office Web Apps サーバーの計画](plan-office-web-apps-server.md)」を参照してください。

## Office Web Apps のブラウザー サポート

Office Web Appsでのブラウザーのサポートは SharePoint 2013と同じです。詳細については、記事「[SharePoint 2013 でブラウザー サポートを計画する](https://technet.microsoft.com/ja-jp/library/cc263526\(v=office.15\))」を参照してください。

## Office Web Apps の SharePoint 認証の要件

Office Web Appsは、クレーム ベース認証を使用する SharePoint 2013 Web アプリケーションのみで使用できます。Office Web Appsの表示および編集は、クラシック モード認証を使用する SharePoint 2013 Web アプリケーションでは機能しません。クラシック モード認証を使用する SharePoint 2010 Web アプリケーションを SharePoint 2013に移行する場合は、Office Web Appsで作動するようにクレーム ベース認証に移行する必要があります。詳細については、「[SharePoint 2013 でクラシックモードからクレームベース認証に移行する](https://technet.microsoft.com/ja-jp/library/gg251985\(v=office.15\))」を参照してください。

## Office ファイルを編集するための Office Web Apps のライセンス

ボリューム ライセンス プログラムで Office 2013 のライセンスを取得しているエンタープライズ ユーザーは、社内の SharePoint 2013 で Office Web Apps の編集機能を有効にできます。これによって、自宅など Office クライアントがインストールされていない場所でも Office 編集機能を使用できるようになります。

ライセンスの詳細については、Office Web Apps サーバー をインストールすると表示されるマイクロソフト ソフトウェア ライセンス条項を参照してください。SharePoint 2013 でのライセンスの働きの詳細については、[ライセンスを構成する (SharePoint Server 2013)](https://technet.microsoft.com/ja-jp/library/jj219627\(v=office.15\))をご覧ください。

## データベース接続方式を使用して SharePoint 2010 からアップグレードする場合の考慮事項

Office Web Apps を SharePoint 2010 と共にインストールした場合、SharePoint 2013 にアップグレードした後は Office Web Apps を使用できなくなります。Office Web Apps サーバー を展開し、コンテンツ データベースがアップグレードされた後で SharePoint 2013 を Office Web Apps Server に接続する必要があります。サイト コレクションがアップグレードされるまで待つ必要はありません。Office Web Apps サーバー は SharePoint 2013 の 2010 と 2013 の両方のサイト コレクション モードをサポートしているからです。データベース接続方式の詳細については、「[SharePoint 2013 へのアップグレード プロセスの概要](https://technet.microsoft.com/ja-jp/library/cc262483\(v=office.15\))」を参照してください。

## SharePoint 2013 ドキュメント ライブラリからドキュメントを開くときの既定のオープン動作

Word、PowerPoint、Excel、および OneNote ファイルをクライアント アプリケーション (インストールされている場合) で開くか、ブラウザーで開くかを構成できます。既定では、SharePoint 2013が Office Web Apps サーバーを使用するように構成すると、Office ファイルはブラウザーで開かれます。以下の 2 つの方法で、クライアント アプリケーションがファイルを直接開くように既定の動作を変更できます。

  - **SharePoint 2013 ファーム** [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) および [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps)Windows PowerShell コマンドレットを使用して、SharePoint 2013 ファームでファイルの種類ごとに既定のオープン動作を調整できます。

  - **サイト コレクションまたはドキュメント ライブラリ** サイト コレクション管理者およびユーザーが、Office ファイルをクライアント アプリケーションで開くかどうかを指定できます (インストールされている場合)。ユーザーは、この設定をドキュメント ライブラリのプロパティで変更できます。サイト コレクション管理者は、\[サイト コレクションの管理\] でこの設定を変更するか、Install-SPFeature コマンドレットを使用して OpenInClient 機能をインストールできます。詳細については、「[Install-SPFeature](https://technet.microsoft.com/ja-jp/library/ff607825\(v=office.15\))」を参照してください。

## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[内部設置型 Office Web Apps が SharePoint 2013 で機能する方法](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  


[HTTP を使用するテスト環境で Office Web Apps Server を使用するための SharePoint 2013 の構成](configure-office-web-apps-for-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

