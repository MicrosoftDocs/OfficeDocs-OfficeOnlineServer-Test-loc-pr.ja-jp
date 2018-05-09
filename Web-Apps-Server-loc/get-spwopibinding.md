---
title: Get-SPWOPIBinding
TOCTitle: Get-SPWOPIBinding
ms:assetid: b757301b-f6c5-43a5-a8ca-2ef33ede0ae8
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219450(v=office.15)
ms:contentKeyID: 48796444
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIBinding

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで、**New-SPWOPIBinding** を使用して作成されたバインドの一覧を返します。

## 構文

    Get-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WOPIZone <String>]

## 解説

**Get-SPWOPIBinding** コマンドレットでは、このコマンドレットが実行されている現在の SharePoint ファームで、**New-SPWOPIBinding** を使用して作成されたバインドの一覧を取得します。結果には、WOPI アプリケーション (Office Web Apps サーバーが実行されているサーバーなど) に対して構成されているアクション、アプリケーション、ファイルの種類、ゾーンなどが含まれます。

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
<td><p><strong>Action</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得するアクションを指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得するアプリケーションを指定します。</p></td>
</tr>
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
<td><p><strong>Extension</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得するファイル名拡張子を指定します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得するアプリケーションのプログラム識別子 (ProgID) を指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Server</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得する WOPI アプリケーション (Office Web Apps サーバーが実行されているサーバーなど) の名前を指定します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドを取得するゾーンを指定します。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 1 -----------------

    Get-SPWOPIBinding -Server "Server.corp.Contoso.com"

この例では、WOPI アプリケーション "Server.corp.Contoso.com" について、このコマンドレットが実行されている現在の SharePoint ファームで作成されたバインドの一覧を取得します。WOPI アプリケーションは、Office Web Apps サーバー が実行されているサーバーの場合があります。

\-------------- 例 2 -----------------

    Get-SPWOPIZone | Get-SPWOPIBinding

この例では、WOPI アプリケーションに対して構成されたゾーンについて、このコマンドレットが実行されている現在の SharePoint ファームで作成されたバインドの一覧を取得します。

## 関連項目


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

