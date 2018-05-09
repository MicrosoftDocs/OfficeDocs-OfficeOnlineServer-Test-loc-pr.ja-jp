---
title: Get-OfficeWebAppsHost
TOCTitle: Get-OfficeWebAppsHost
ms:assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219446(v=office.15)
ms:contentKeyID: 48796438
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsHost

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2013-12-18_

Office Web Apps サーバー ファームの許可リストにあるホスト ドメインのリストを取得します。

## 構文

    Get-OfficeWebAppsHost

## 詳細説明

**Get-OfficeWebAppsHost** コマンドレットは、Office Web Apps サーバー が、ファイル取得、メタデータ取得、ファイル変更のような、ファイル処理要求を許可するホスト ドメインのリストを戻します。許可リストと呼ばれるこのリストは、望ましくないホストが知らない間に Office Web Apps サーバー ファームに接続してファイル操作することを防ぐセキュリティ機能です。

ワイルドカード \* は、許可リスト内のすべてのドメインとみなされ、すべてのサブドメインへの要求も許可されます。たとえば、ドメイン contoso.com が許可リストにある場合、Office Web Apps サーバー はドメイン corp.contoso.com および dev.contoso.com への要求も許可します。(fabrikam.com のような) その他のドメインへの要求は許可されません。


> [!TIP]
> 許可リストにドメインがない場合、Office Web Apps サーバー はすべてのドメイン内のホストにファイル要求を許可します。Office Web Apps サーバー ファームがインターネットからアクセスできる場合は、このリストを空白のままにしないでください。リストを空白にすると、Office Web Apps サーバー ファームを使用して、だれでもコンテンツの表示と編集ができてしまいます。



## パラメーター

## 入力の種類

## 戻り値の種類

## 例

\------------------ 例 1 ---------------------

    Get-OfficeWebAppsHost

この例は、許可リストにあるホスト ドメインを戻します。

## 関連項目


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

