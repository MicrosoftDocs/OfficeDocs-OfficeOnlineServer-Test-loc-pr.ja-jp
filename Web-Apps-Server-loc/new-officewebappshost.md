---
title: New-OfficeWebAppsHost
TOCTitle: New-OfficeWebAppsHost
ms:assetid: f1d523ab-45c6-4e3c-b274-22c0d229a6a0
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219459(v=office.15)
ms:contentKeyID: 48796459
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsHost

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

Office Web Apps サーバー ファームの許可リストにホスト ドメインを追加します。

## 構文

    New-OfficeWebAppsHost -Domain <String>

## 解説

**New-OfficeWebAppsHost** コマンドレットは、Office Web Apps サーバー が、ファイル取得、メタデータ取得、ファイル変更のような、ファイル処理要求を許可するホスト ドメインのリストにホスト ドメインを追加します。許可リストと呼ばれるこのリストは、望ましくないホストが知らない間に Office Web Apps サーバー ファームに接続してファイル操作することを防ぐセキュリティ機能です。


> [!TIP]
> パブリック、プール、ファーム、および Active Directory ドメイン名などのドメインの種類を追加できます。アクセスを許可するドメインがセキュリティの必要条件を満たしていることを確認してください。



ワイルドカード \* は、許可リスト内に追加される任意のドメインとみなされ、すべてのサブドメインへの要求も許可されます。たとえば、ドメイン contoso.com を許可リストに追加する場合、Office Web Apps サーバー はドメイン corp.contoso.com および dev.contoso.com への要求も許可します。(fabrikam.com のような) その他のドメインへの要求は許可されません。


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
<td><p>許可リストに追加するドメインを指定します。アスタリスクを指定しないでください。また、ピリオドから始まる名前を指定しないでください。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\------------------ 例 2 ---------------------

    New-OfficeWebAppsHost -domain "contoso.com"

この例は、許可リストにドメイン contoso.com を追加します。


> [!NOTE]
> 複数のホスト ドメインがある場合、一度にすべてのドメインを許可リストに追加することはできません。許可リストに追加するホスト ドメインごとに New-OfficeWebAppsHost コマンドレットを実行する必要があります。



## 関連項目


[Get-OfficeWebAppsHost](get-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

