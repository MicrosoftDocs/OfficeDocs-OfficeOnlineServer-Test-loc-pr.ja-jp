---
title: Remove-OfficeWebAppsHost
TOCTitle: Remove-OfficeWebAppsHost
ms:assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219453(v=office.15)
ms:contentKeyID: 48796449
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsHost

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

Office Web Apps サーバー ファームの許可リストからホスト ドメインを削除します。

## 構文

    Remove-OfficeWebAppsHost -Domain <String>

## 解説

**Remove-OfficeWebAppsHost** コマンドレットは、許可リストから指定したホスト ドメインを削除します。許可リストには、Office Web Apps サーバー がファイル処理要求を許可するホスト ドメインが含まれます。


> [!TIP]
> 許可リストにドメインがない場合、Office Web Apps サーバー はすべてのドメイン内のホストにファイル要求を許可します。Office Web Apps サーバー ファームがインターネットからアクセスできる場合は、このリストを空白のままにしないでください。リストを空白にすると、Office Web Apps サーバー ファームを使用して、だれでもコンテンツの表示と編集ができてしまいます。



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
<th>種類</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Domain</strong></p></td>
<td><p>必須</p></td>
<td><p>System.String</p></td>
<td><p>許可リストから削除するホスト ドメインを指定します。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\------------------ 例 1 ---------------------

    Remove-OfficeWebAppsHost -domain "contoso.com"

この例は、許可リストからドメイン contoso.com を削除します。

## 関連項目


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Get-OfficeWebAppsHost](get-officewebappshost.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

