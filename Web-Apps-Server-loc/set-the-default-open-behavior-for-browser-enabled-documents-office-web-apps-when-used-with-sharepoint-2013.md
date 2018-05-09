---
title: ブラウザー対応ドキュメントの既定のオープン動作を設定する (SharePoint 2013 と組み合わせて使用する Office Web Apps)
TOCTitle: ブラウザー対応ドキュメントの既定のオープン動作を設定する
ms:assetid: e27e0bc8-5fb5-4bb1-8157-d7c90654175e
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ee837425(v=office.15)
ms:contentKeyID: 50181176
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# ブラウザー対応ドキュメントの既定のオープン動作を設定する (SharePoint 2013 と組み合わせて使用する Office Web Apps)

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2016-12-16_

**概要:** SharePoint サイト コレクションと SharePoint ドキュメント ライブラリで Office ドキュメントを表示する既定の方法を構成する方法について説明します。

**対象ユーザー:** IT 担当者

SharePoint 2013 ドキュメント ライブラリ内のドキュメントを開くには、そのタイトルをクリックするだけです。次に何が起きるか (ファイルがクライアント アプリケーションで開くのか、ブラウザーで開くのか) は、ファイルの種類、Office Web Apps サーバー ファームのセットアップ方法、ライブラリまたはサイト コレクションの OpenInClient 機能設定のセットアップ方法などのいくつかの要因によって異なります。以下のステップは、SharePoint 2013 で Office Web Apps サーバー が使用されるように構成した Office 文書の既定のオープン動作の構成方法を示しています。

## ドキュメントを SharePoint 2013 ライブラリから開く方法を設定する

既定では、SharePoint 2013 を Office Web Apps サーバー を使用するように構成した場合は、Word、PowerPoint、Excel、OneNote ファイルをクリックするとブラウザーで開かれます。PDF ドキュメントは Word Web App Web App で開きます。代わりに、クライアント アプリケーション (または既定の PDF リーダー) でファイルを開くように既定の動作を変更する方法が 2 つあります。

  - **SharePoint 2013 ファーム** [New-SPWOPIBinding](new-spwopibinding.md) コマンドレットと [Set-SPWOPIBinding](set-spwopibinding.md)Windows PowerShell コマンドレットを使用して SharePoint 2013 ファームでファイルの種類ごとに既定のオープン動作を調整できます。これらのコマンドレットは、「[PDF ドキュメントの動作の調整](http://go.microsoft.com/fwlink/p/?linkid=330246)」に使用することもできます。

  - **サイト コレクションまたはドキュメント ライブラリ**   サイト コレクション管理者およびユーザーは、SharePoint 2013 の OpenInClient 機能を使用して Office ファイルをクライアント アプリケーションで開くか、ブラウザーで開くかを指定できます。ユーザーは、この設定をドキュメント ライブラリのプロパティで変更できます。サイト コレクション管理者は、この設定を \[サイト コレクションの管理\] で変更することも、[Enable-SPFeature](https://technet.microsoft.com/ja-jp/library/ff607803\(v=office.15\)) コマンドレットを使用して OpenInClient 機能を有効にすることによって変更することもできます。OpenInClient 機能を有効にするためのさまざまな方法については次のセクションを参照してください。

通常は、OpenInClient 機能によって、SharePoint 2013 と Office Web Apps サーバー の間に設定された WOPI バインドが無効になります。つまり、SharePoint 2013 ライブラリまたはサイト コレクションの OpenInClient 機能が有効になっている場合は、SharePoint 2013 サーバーで Office Web Apps サーバー が使用されるように構成してあっても、ドキュメントはクライアント アプリケーションで開きます。


> [!NOTE]
> ブラウザー対応ドキュメントの既定のオープン動作を構成しても、SharePoint 2013 内の [<STRONG>チェックアウト</STRONG>] 機能と [<STRONG>送信</STRONG>] 機能を使用してドキュメントをダウンロードできるかどうかには影響しません。SharePoint 2013 でチェックアウト、ダウンロード、およびアクセス許可の表示を構成する方法については、「<A href="https://technet.microsoft.com/ja-jp/library/cc262939(v=office.15)">SharePoint 2013 でのサイトとコンテンツのアクセス許可の計画</A>」を参照してください。



## ドキュメント ライブラリまたはサイト コレクションの OpenInClient 機能を設定する

SharePoint 2013 の OpenInClient 機能を設定するには、次の手順のいずれかを使用します。


> [!NOTE]
> これらの手順の一部では、SharePoint 2013 管理シェル を使用して SharePoint コマンドレットを実行します。Windows PowerShell コンソールの使用を選択する場合は、<STRONG>Add-PSSnapin</STRONG> コマンドレットを使用して Microsoft.SharePoint.PowerShell スナップインを追加する必要があります。Windows PowerShell とSharePoint 2013を併用する方法の詳細は、「<A href="use-windows-powershell-to-administer-sharepoint-2013.md">Windows Powershell を使用して SharePoint 2013 を管理する</A>」を参照してください。




> [!NOTE]
> Office 2013 スイート 内のタスクは、マウス、キーボード ショートカット、またはタッチを使用して実行できます。Office 製品およびサービスでキーボード ショートカットとタッチを使用する方法については、「<A href="http://go.microsoft.com/fwlink/p/?linkid=249150">キーボード ショートカット</A>」と「<A href="http://go.microsoft.com/fwlink/p/?linkid=253163">Office タッチ ガイド</A>」を参照してください。



 **サイト コレクションの OpenInClient 機能を設定する**

1.  SharePoint サイト コレクションで、\[**設定**\] アイコン \> \[**サイトの設定**\] の順に選択します。

2.  \[サイトの設定\] ページの \[**サイト コレクションの管理**\] で、\[**サイト コレクションの機能**\] を選択します。

3.  \[**機能**\] ページで、\[**既定でクライアント アプリケーションでドキュメントを開く**\] 機能に対して、\[**アクティブ化**\] を選択して OpenInClient 機能を有効にする (ドキュメントはクライアント アプリケーションで開く) か、\[**非アクティブ化**\] を選択して OpenInClient 機能を無効にします (ドキュメントはブラウザーで開く)。

 **Windows PowerShell を使用してサイト コレクションの既定のオープン動作を設定する**

1.  まず、次のメンバーシップがあることを確認します。
    
      - SQL Server インスタンスに対する **securityadmin** 固定サーバー ロール。
    
      - 更新するすべてのデータベースに対する **db\_owner** 固定データベース ロール。
    
      - Windows PowerShell コマンドレットを実行するサーバーでの Administrators グループ。
    
    また、「[about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)」を確認して、その他の必要なメンバーシップを追加します。
    
    管理者は **Add-SPShellAdmin** コマンドレットを使用して、SharePoint 2013のコマンドレットを使用する権限を付与できます。
    

    > [!NOTE]
    > アクセス許可がない場合は、セットアップ管理者または SQL Server 管理者に連絡してアクセス許可を要求してください。Windows PowerShell アクセス許可の追加情報については、「<A href="use-windows-powershell-to-administer-sharepoint-2013.md">アクセス許可</A>」と「<A href="https://technet.microsoft.com/ja-jp/library/ff607596(v=office.15)">Add-SPShellAdmin</A>」を参照してください。



2.  昇格された SharePoint 2013 管理シェル を開く
    
    **Windows Server 2008 で**
    
    1.  \[**スタート**\] メニューの \[**すべてのプログラム**\] を選択します。
    
    2.  \[**Microsoft SharePoint 2013 製品**\] を選択します。
    
    3.  \[**SharePoint 2013 管理シェル**\] を選択し、そのショートカット メニューを表示します (右クリック)。
    
    4.  ショートカット メニューで、\[**管理者として実行**\] を選択します。
    
    **Windows Server 2012 で**
    
    1.  画面の端から内側へスワイプしてチャームを表示し、\[**検索**\] を選択してコンピューターにインストールされているすべてのアプリケーションを表示します。
    
    2.  \[**SharePoint 2013 管理シェル**\] を選択 (右クリック) してアプリ バーを表示します。
    
    3.  アプリ バーで、\[**管理者として実行**\] を選択します。

3.  Windows PowerShell コマンド プロンプトで、以下のいずれかのコマンドを入力します。
    
      - 特定のサイト コレクションに対して OpenInClient 機能を有効にする (ドキュメントをクライアント アプリケーションで開くため) には、次のコマンドを入力します。
        
            Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        ここで、*\<SiteCollURL\>* は、サイト コレクションの URL です。
    
      - すべてのサイト コレクションに対して OpenInClient 機能を有効にする (ドキュメントをクライアント アプリケーションで開くため) には、次のコマンドを入力します。
        
            Get-SPSite -limit ALL |foreach{ Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
    
      - 特定のサイト コレクションに対して OpenInClient 機能を無効にする (ドキュメントをブラウザーで開くため) には、次のコマンドを入力します。
        
            Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        ここで、*\<SiteCollURL\>* は、サイト コレクションの URL です。
    
      - すべてのサイト コレクションに対して OpenInClient 機能を無効にする (ドキュメントをブラウザーで開くため) には、次のコマンドを入力します。
        
            Get-SPSite -limit ALL |foreach{ Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }

 **ドキュメント ライブラリ設定ページを使用してドキュメント ライブラリを表示する既定の方法を設定する**

1.  ドキュメント ライブラリ ページで、\[**ライブラリ**\] タブを選択します。

2.  \[**設定**\] グループで、\[**ライブラリの設定**\] を選択します。

3.  \[**ドキュメント ライブラリの設定**\] ページで、\[**詳細設定**\] を選択します。

4.  \[**詳細設定**\] ページの \[**ブラウザーでドキュメントを開く**\] で、以下のいずれかのオプションを選択します。
    
      - \[**クライアント アプリケーションで開く**\]   このライブラリでドキュメントを選択すると、対応するクライアント アプリケーションが使用可能であれば、そのドキュメントは開きます。
    
      - \[**ブラウザーで開く**\]   このライブラリでドキュメントを選択すると、ドキュメントはそのドキュメントの種類に適した Web アプリ内の Web ブラウザーで開かれます。Web アプリでドキュメントが開かれている時、クライアント アプリケーションでドキュメントを開くかどうか決めることができます。
    
      - \[**既定のサーバーを使用する**\]    このライブラリでドキュメントを選択すると、そのドキュメントは SharePoint 2013 を実行しているサーバーに指定された既定の表示方法で開きます。

 **Windows PowerShell を使用して IRM で保護されたドキュメント ライブラリの既定のオープン動作を設定する**

1.  まず、次のメンバーシップがあることを確認します。
    
      - SQL Server インスタンスに対する **securityadmin** 固定サーバー ロール。
    
      - 更新するすべてのデータベースに対する **db\_owner** 固定データベース ロール。
    
      - Windows PowerShell コマンドレットを実行するサーバーでの Administrators グループ。
    
    また、「[about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)」を確認して、その他の必要なメンバーシップを追加します。
    
    管理者は **Add-SPShellAdmin** コマンドレットを使用して、SharePoint 2013のコマンドレットを使用する権限を付与できます。
    

    > [!NOTE]
    > アクセス許可がない場合は、セットアップ管理者または SQL Server 管理者に連絡してアクセス許可を要求してください。Windows PowerShell アクセス許可の追加情報については、「<A href="use-windows-powershell-to-administer-sharepoint-2013.md">アクセス許可</A>」と「<A href="https://technet.microsoft.com/ja-jp/library/ff607596(v=office.15)">Add-SPShellAdmin</A>」を参照してください。



2.  昇格された SharePoint 2013 管理シェル を開く
    
    **Windows Server 2008 で**
    
    1.  \[**スタート**\] メニューの \[**すべてのプログラム**\] を選択します。
    
    2.  \[**Microsoft SharePoint 2013 製品**\] を選択します。
    
    3.  \[**SharePoint 2013 管理シェル**\] を選択し、そのショートカット メニューを表示します (右クリック)。
    
    4.  ショートカット メニューで、\[**管理者として実行**\] を選択します。
    
    **Windows Server 2012 で**
    
    1.  画面の端から内側へスワイプしてチャームを表示し、\[**検索**\] を選択してコンピューターにインストールされているすべてのアプリケーションを表示します。
    
    2.  \[**SharePoint 2013 管理シェル**\] を選択 (右クリック) してアプリ バーを表示します。
    
    3.  アプリ バーで、\[**管理者として実行**\] を選択します。

3.  Windows PowerShell コマンド プロンプトで、次のコマンドを入力します。
    
        Get-SPWeb -site <SiteCollURL> | % {$_.Lists} | where {$_.IrmEnabled -eq $true} | % {$_.DefaultItemOpen =[Microsoft.Sharepoint.DefaultItemOpen]::<DefaultItemOpenSetting>; $_.Update()}
    
    各部分の意味は次のとおりです。
    
      - *\<SiteCollURL\>* は、ドキュメント ライブラリが存在するサイト コレクションの URL です。
    
      - *\<DefaultItemOpenSetting\>* は、既定のオープン動作を指定する **DefaultItemOpen** 列挙値です。ドキュメントに関連するクライアント アプリケーションで (使用可能な場合) ドキュメントを開くには、**PreferClient** を使用します。ドキュメントをブラウザーで開くには、**Browser** を使用します。

## 関連項目


[Get-SPWOPIBinding](get-spwopibinding.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Windows Powershell を使用して SharePoint 2013 を管理する](use-windows-powershell-to-administer-sharepoint-2013.md)  
[Office Web Apps サーバー](office-web-apps-server.md)  


[Get-SPWeb](https://technet.microsoft.com/ja-jp/library/ff607807\(v=office.15\))  
[Get-SPSite](https://technet.microsoft.com/ja-jp/library/ff607950\(v=office.15\))  
[Get-SPFeature](https://technet.microsoft.com/ja-jp/library/ff607945\(v=office.15\))

