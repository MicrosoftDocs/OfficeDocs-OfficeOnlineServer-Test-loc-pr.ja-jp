---
title: Windows Powershell を使用して SharePoint 2013 を管理する
TOCTitle: Windows Powershell を使用して SharePoint 2013 を管理する
ms:assetid: ae4901b4-505a-42a9-b8d4-fca778abc12e
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ee806878(v=office.15)
ms:contentKeyID: 48796440
ms.date: 12/19/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Windows Powershell を使用して SharePoint 2013 を管理する

 

_**適用先:**SharePoint Foundation 2013, SharePoint Server 2013 Enterprise, SharePoint Server 2013 Standard_

_**トピックの最終更新日:**2016-12-16_

**概要:** Windows PowerShell の基本的なコマンドレットと概念について説明し、SharePoint 2013 で Windows PowerShell を使用する方法を説明します。

この記事の内容

  - 概要

  - SharePoint 2013 製品向けの Windows PowerShell にアクセスする

  - 権限

  - スクリプトと実行ポリシー

  - Windows PowerShell について学ぶ

## 概要

Windows PowerShell は、管理者に利用可能なアプリケーション プログラミング インターフェイス (API) へのフル アクセスを提供するコマンド ライン シェルおよびスクリプト言語です。管理者は SharePoint 2013と直接やり取りして、Web アプリケーション、サイト コレクション、サイト、リストなどを操作できます。さらに、コマンドレットをスクリプト化することもできます

Windows PowerShell 3.0 は、SharePoint 2013をインストールするための前提条件です。Microsoft SharePoint 製品準備ツールを実行すると、これがインストールされます (まだインストールされていない場合)。Windows PowerShell の既定のインストール パスは、\<%SystemRoot%\>\\System32\\WindowsPowerShell\\v1.0\\PowerShell.exe です。

Windows PowerShell 3.0 の新機能の一覧については、「[Windows Management Framework 3.0](http://go.microsoft.com/fwlink/p/?linkid=272782)」を参照してください。

Windows PowerShell の構文の理解に役立つ対話形式のツールとガイドについては、「[Windows PowerShell for SharePoint Command Builder](http://go.microsoft.com/fwlink/p/?linkid=229854)」と「[Windows PowerShell Command Builder ファースト ステップ ガイド](http://www.microsoft.com/download/en/details.aspx?id=27588)」を参照してください。

コマンドライン管理タスクを実行するときには Windows PowerShell を使用することが推奨されています。Stsadm コマンドライン ツールは推奨されていませんが、製品の以前のバージョンとの互換性をサポートするために含まれています。

## SharePoint 2013向けの Windows PowerShell にアクセスする

SharePoint 2013のインストール後は、SharePoint 2013 管理シェルで Windows PowerShell のコマンドレットを利用できます。SharePoint 管理シェルでは、SharePoint 2013の多くの部分を管理できます。新しいサイト コレクション、Web アプリケーション、ユーザー アカウント、サービス アプリケーション、プロキシなどを作成できます。SharePoint 管理シェルでコマンドを入力すると、Microsoft .NET Framework に基づいた SharePoint オブジェクトが返されます。それらのオブジェクトは、後続のコマンドへの入力として適用したり、後で使用できるようにローカル変数に格納することができます。

SharePoint 管理シェルを使用する場合は、コマンドレットが含まれるスナップインを登録する必要はありません。SharePoint 2013 コマンドレット用の Microsoft.SharePoint.PowerShell.dll モジュールの登録は、*%CommonProgramFiles%*\\Microsoft Shared\\Web Server Extensions\\15\\Config\\PowerShell\\Registration にある SharePoint.ps1 ファイル内の `Add-PSSnapin Microsoft.SharePoint.PowerShell` という行によって自動で行われます。Windows PowerShell コンソールを使用する場合は、このスナップインを手動で登録する必要があります。

SharePoint 管理シェルと Windows PowerShell コンソールのどちらを使用するにしても、追加のスナップインを読み込むことができます。詳細については、「[プロファイルの力](http://go.microsoft.com/fwlink/p/?linkid=183166)」を参照してください。

**SharePoint 管理シェルにアクセスするには**

1.  SharePoint 管理シェル を起動します。
    
      - Windows Server 2008 R2 の場合:
        
          - \[**スタート**\] ボタンをクリックし、\[**Microsoft SharePoint 2013 製品**\]、\[**SharePoint 管理シェル**\] の順にクリックします。
    
      - Windows Server 2012 の場合:
        
          - \[**スタート**\] 画面の \[**SharePoint 管理シェル**\] をクリックします。
            
            \[**SharePoint 管理シェル**\] が \[**スタート**\] 画面に表示されない場合:
        
        <!-- end list -->
        
          - \[**コンピューター**\] を右クリックし、\[**すべてのアプリ**\]、\[**SharePoint 管理シェル**\] の順にクリックします。
    
    Windows Server 2012 の操作方法の詳細については、「[Windows Server 2012 の一般的な管理タスクとナビゲーション](http://technet.microsoft.com/ja-jp/library/hh831491.aspx)」を参照してください。


> [!NOTE]
> SharePoint 2013 管理シェルと Windows PowerShell コンソールでは、スレッド モデルの使用方法を定義する <CODE>ReuseThread</CODE> オプションの使用も異なります。SharePoint 2013 管理シェルでの使用方法は、SharePoint.ps1 ファイル内の <CODE>{Host.Runspace.ThreadOptions = "ReuseThread"}</CODE> という行で定義されています。詳細については、<A href="http://go.microsoft.com/fwlink/p/?linkid=183145">PSThreadOptions</A> を参照してください。



## 権限

## 社内

**Add-SPShellAdmin** コマンドレットを使用して、SharePoint 2013のコマンドレットを実行する権限をユーザーに付与するためには、まず以下の最小要件をすべて満たしていることを確認します。

  - SQL Server インスタンスに対する **securityadmin** 固定サーバー ロールのメンバーシップが必要です。

  - 更新するすべてのデータベースに対する **db\_owner** 固定データベース ロールのメンバーシップが必要です。

  - Windows PowerShell コマンドレットを実行するサーバーの Administrators グループのメンバーである必要があります。


> [!NOTE]
> これらの権限がない場合は、セットアップ管理者または SQL Server 管理者に連絡して、これらの権限を要求してください。



Windows PowerShell の権限に関する追加情報については、「権限」および「[Add-SPShellAdmin](https://technet.microsoft.com/ja-jp/library/ff607596\(v=office.15\))」を参照してください。

**SharePoint\_Shell\_Access** ロールまたは **WSS\_Admin\_WPG** ローカル グループのメンバーシップがない場合は、**Add-SPShellAdmin** コマンドレットを使用して、SharePoint ファームのすべてのフロントエンド Web サーバーの **WSS\_Admin\_WPG** グループおよび **SharePoint\_Shell\_Access** ロールに追加します。SQL Server データベースに **SharePoint\_Shell\_Access** ロールがない場合、**Add-SPShellAdmin** コマンドレットを実行したときに、このロールが自動的に作成されます。**Add-SPShellAdmin** を実行すると、ユーザーは複数サーバーのファーム環境で SharePoint Windows PowerShell コマンドレットを実行できるようになります。


> [!NOTE]
> SharePoint 2013をインストールすると、インストールを実行するユーザー アカウントに Windows PowerShell のコマンドレットを実行するための適切な権限が付与されます。Windows PowerShell のコマンドレットを実行するユーザーが追加されていない場合は、<STRONG>Add-SPShellAdmin</STRONG> コマンドレットを使用してユーザーを追加できます。



アクセスを許可するすべてのデータベースに対して **Add-SPShellAdmin** コマンドレットを実行する必要があります。データベースを指定しない場合は、ファーム構成データベースが使用されます。データベースを指定した場合は、指定したファーム構成データベースに加えて、ファーム コンテンツ データベースが対象に含まれます。

すべての **SPShellAdmin** コマンドレットの一覧を表示するには、Windows PowerShell コマンド プロンプトで、「`Get-Command -Noun SPShellAdmin`」と入力します。

## SharePoint Online

次の管理権限を持っていることを確認します。

  - Windows PowerShell コマンドレットを実行する SharePoint Online サイトのグローバル管理者ロールが割り当てられている必要があります。詳細については、「[既定の管理者ロールとユーザー グループ](http://go.microsoft.com/fwlink/p/?linkid=242451)」を参照してください。
    

    > [!IMPORTANT]
    > SharePoint Online で Windows PowerShell の特定のグループを使用できます。詳細については、「<A href="https://technet.microsoft.com/ja-jp/library/fp161362(v=office.15)">SharePoint Online 用の Office 365 PowerShell</A>」を参照してください。



## スクリプトと実行ポリシー

Windows PowerShell では単一の管理タスクを実行できますが、スクリプトを使用して一連のタスクを自動化することもできます。スクリプトは、1 つ以上の Windows PowerShell コマンドが含まれるテキスト ファイルです。Windows PowerShell のスクリプトは, .ps1 というファイル名拡張子を持ちます。

スクリプトを実行するには、SharePoint 2013の実行ポリシーが最低限 RemoteSigned であることが必要です。ただし、Windows PowerShell の既定のポリシーは Restricted です。ポリシーが Restricted のままになっている場合は、SharePoint 2013 管理シェルによって Windows PowerShell のポリシーが RemoteSigned に変更されます。つまり、\[**管理者として実行**\] を選択することにより、管理者権限で SharePoint 2013 管理シェルを起動する必要があります。この変更は、すべての Windows PowerShell セッションに適用されます。詳細については、「[ExecutionPolicy 列挙](http://go.microsoft.com/fwlink/p/?linkid=242452)」を参照してください。

スクリプトと実行ポリシーの詳細については、それぞれ「[about\_scripts](http://go.microsoft.com/fwlink/p/?linkid=144310)」と「[about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)」を参照してください。

## Windows PowerShell について学ぶ

SharePoint IT 担当者向けの Windows PowerShell ラーニング リソースがいくつかあります。

**TechNet スクリプト センター**

TechNet スクリプト センターには、Windows PowerShell の基礎を学ぶための多数のリソースがあります。また、さまざまな Microsoft 製品で一般的に使用するスクリプトのサンプルが含まれているスクリプト リポジトリもあります。次の表に、主なラーニング リソースを示します。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ページ</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187813">TechNet の Windows PowerShell のドキュメント</a></p></td>
<td><p>TechNet ライブラリのこのセクションには、Windows PowerShell の Get-Help の主要なトピックのコピーがあります。また、Windows PowerShell の概要についてのドキュメント、PowerShell.exe のヘルプ、および Windows PowerShell の入門の文書のコピーもあります。</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187815">Windows PowerShell でのスクリプティング</a></p></td>
<td><p>Windows PowerShell スクリプトのラーニング リソースのホーム ページです。</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187817">Windows PowerShell オーナー マニュアル</a></p></td>
<td><p>Windows PowerShell の概要について学ぶための Web ベースのガイドです。</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187819">Windows PowerShell クイック リファレンス</a></p></td>
<td><p>Windows PowerShell と共にインストールされるクイック リファレンス ドキュメントのダウンロード可能なコピーです。</p></td>
</tr>
</tbody>
</table>


これらのリソースを読むときには、SharePoint 2013 向けの Windows PowerShell を使用する前に、以下の概念およびコマンドレットについて学んでおくと役立ちます。

  - [Get-Command](http://go.microsoft.com/fwlink/p/?linkid=171069)

  - [Get-Member](http://go.microsoft.com/fwlink/p/?linkid=171070)

  - [Get-Help](http://go.microsoft.com/fwlink/p/?linkid=171068)

  - [about\_aliases](http://go.microsoft.com/fwlink/p/?linkid=113207)

  - [Windows PowerShell でのパイプ指定とパイプライン](http://go.microsoft.com/fwlink/p/?linkid=187808)

  - [コマンドレット パラメーター セット](http://go.microsoft.com/fwlink/p/?linkid=187810)

  - [Foreach-Object コマンドレットの使用](http://go.microsoft.com/fwlink/p/?linkid=187812)

  - [Where-Object コマンドレットの使用](http://go.microsoft.com/fwlink/p/?linkid=187811)

