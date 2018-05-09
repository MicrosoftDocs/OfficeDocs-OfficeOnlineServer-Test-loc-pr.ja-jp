---
title: Get-SPWOPISuppressionSetting
TOCTitle: Get-SPWOPISuppressionSetting
ms:assetid: a7924964-e16f-4eca-be91-7aff8d45e0c6
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219445(v=office.15)
ms:contentKeyID: 48796437
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPISuppressionSetting

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで抑制設定を返します。

## 構文

    Get-SPWOPISuppressionSetting [-AssignmentCollection <SPAssignmentCollection>]

## 解説

**Get-SPWOPISuppressionSetting** コマンドレットでは、このコマンドレットが実行されている現在の SharePoint ファームで抑制設定を取得します。

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
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 -----------------

    Get-SPWOPISuppressionSetting

この例では、このコマンドレットが実行されている現在の SharePoint ファームで抑制設定を取得します。取得する抑制設定には、**DocType**、**WOPIAction** などがあります。

## 関連項目


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

