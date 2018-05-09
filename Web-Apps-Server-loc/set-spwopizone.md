---
title: Set-SPWOPIZone
TOCTitle: Set-SPWOPIZone
ms:assetid: bc751cc4-8ac8-45f7-b6ea-da6fcb5473ac
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219451(v=office.15)
ms:contentKeyID: 48796445
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIZone

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

現在の SharePoint ファームがブラウザーを WOPI アプリケーションに移動するときに使用するゾーンを構成します。

## 構文

    Set-SPWOPIZone [[-Zone] <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 解説

**Set-SPWOPIZone** コマンドレットでは、現在の SharePoint ファームがブラウザーを WOPI アプリケーション (Office Web Apps サーバー が実行されているサーバーなど) に移動するときに使用するゾーンを構成します。WOPI アプリケーションには、ページを含むフレームが、ブラウザーの SharePoint Server ページによって作成されます。WOPI アプリケーション ページの URL のゾーンは、この設定によって決まります。

ゾーンを設定しない場合は、既定の "internal-HTTPS" が使用されます。WOPI アプリケーションでサポートされていないゾーンを選択すると、Office Web Appsは動作しません。HTTP を使用するのは、IPSEC (完全な暗号化) が使用されているセキュリティが万全なネットワーク、または機密データが含まれないテスト環境で作業しているときだけにしてください。

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
<td><p><strong>Zone</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>ゾーンを指定します。WOPI アプリケーションがサポートするゾーンの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p>
<p>内部と外部に SharePoint ファームがある場合は、External を指定します。内部にしか SharePoint ファームがない場合は、Internal を指定します。HTTP を使用するのは、IPSEC (完全な暗号化) が使用されているセキュリティが万全なネットワーク、または機密データが含まれないテスト環境で作業しているときだけにしてください。オプションは次のとおりです。</p>
<p>- Internal-HTTP</p>
<p>- Internal-HTTPS</p>
<p>- External-HTTP</p>
<p>- External-HTTPS</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>適切な破棄を行うためにオブジェクトを管理します。<strong>SPWeb</strong> や <strong>SPSite</strong> などのオブジェクトの使用によって大量のメモリが使用される場合があるので、Windows PowerShell スクリプトでこれらのオブジェクトを使用するには適切なメモリ管理が必要です。メモリの解放が必要になった場合は、<strong>SPAssignment</strong> オブジェクトを使用して、変数へのオブジェクトの割り当てとオブジェクトの破棄を行うことができます。割り当てコレクションまたは <strong>Global</strong> パラメーターが使用されない場合、<strong>SPWeb</strong>、<strong>SPSite</strong>、または <strong>SPSiteAdministration</strong> オブジェクトが使用されると、オブジェクトは自動的に破棄されます。</p>
<div class="alert">

> [!NOTE]
> <STRONG>Global</STRONG> パラメーターが使用されている場合は、オブジェクトはすべてグローバル ストアに格納されます。<STRONG>Stop-SPAssignment</STRONG> コマンドを使用してオブジェクトの使用または破棄を直接行わないと、メモリ不足のシナリオになる場合があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する代わりに、コマンドの実行結果を説明するメッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 -----------------

    Set-SPWOPIZone -Zone "external-https"

この例では、HTTPS 経由で WOPI アプリケーション (Office Web Apps サーバー が実行されているサーバーなど) に外部接続するように現在の SharePoint ファームを構成します。

## 関連項目


[Get-SPWOPIZone](get-spwopizone.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

