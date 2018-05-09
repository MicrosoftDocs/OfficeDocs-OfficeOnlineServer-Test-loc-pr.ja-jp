---
title: Update-SPWOPIProofKey
TOCTitle: Update-SPWOPIProofKey
ms:assetid: fe7f3a87-082e-4a43-a5f3-7be41d8e91a3
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219460(v=office.15)
ms:contentKeyID: 48796460
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Update-SPWOPIProofKey

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで、WOPI アプリケーションへの接続に使用する公開キーを更新します。

## 構文

    Update-SPWOPIProofKey [-AssignmentCollection <SPAssignmentCollection>] [-ServerName <String>]

## 解説

**Update-SPWOPIProofKey** コマンドでは、このコマンドレットが実行されている現在の SharePoint ファームで、WOPI アプリケーション (Office Web Apps サーバー が実行されているサーバーなど) への接続に使用する公開キーを更新します。このコマンドレットは、SharePoint ファームと WOPI アプリケーションの間でキーが同期していない場合に使用します。キーが同期していないと、ドキュメントがブラウザーで開かない可能性があります。また、統合ログ システム (ULS) ログには、"ファイルを証明する署名が無効..."、"フォルダーを証明する署名が無効..." といった内容のメッセージが表示されます。

SharePoint 管理シェル

## パラメーター


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>パラメーター</th>
<th>必須</th>
<th>型</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>適切な破棄を行うためにオブジェクトを管理します。<strong>SPWeb</strong> や <strong>SPSite</strong> などのオブジェクトの使用によって大量のメモリが使用される場合があるので、Windows PowerShell スクリプトでこれらのオブジェクトを使用するには適切なメモリ管理が必要です。メモリの解放が必要になった場合は、<strong>SPAssignment</strong> オブジェクトを使用して、変数へのオブジェクトの割り当てとオブジェクトの破棄を行うことができます。割り当てコレクションまたは <strong>Global</strong> パラメーターが使用されない場合、<strong>SPWeb</strong>、<strong>SPSite</strong>、または <strong>SPSiteAdministration</strong> オブジェクトが使用されると、オブジェクトは自動的に破棄されます。</p>
<div class="alert">

> [!NOTE]
> <STRONG>Global</STRONG> パラメーターが使用されている場合は、オブジェクトはすべてグローバル ストアに格納されます。<STRONG>Stop-SPAssignment</STRONG> コマンドを使用してオブジェクトの使用または破棄を直接行わないと、メモリ不足のシナリオになる場合があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>ServerName</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>キーの取得元となる WOPI アプリケーションを指定します。これは、Office Web Apps サーバー が実行されているサーバーの場合があります。このパラメーターを指定しない場合、現在の SharePoint ファームに接続されているすべての WOPI アプリケーションの公開キーが更新されます。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 -----------------

    Update-SPWOPIProofKey -ServerName "Server.corp.Contoso.com"

この例では、WOPI アプリケーション (Office Web Apps サーバー が実行されているサーバーなど) から現在の公開キーを取得し、SharePoint ファームに格納されているキーを更新します。

## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

