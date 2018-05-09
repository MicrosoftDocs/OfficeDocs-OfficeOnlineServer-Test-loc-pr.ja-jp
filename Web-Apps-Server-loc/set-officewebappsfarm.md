---
title: Set-OfficeWebAppsFarm
TOCTitle: Set-OfficeWebAppsFarm
ms:assetid: 6b0b434f-5d19-4e63-9296-cf104b2f3da8
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219442(v=office.15)
ms:contentKeyID: 48796430
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsFarm

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

既存の Office Web Apps サーバー ファームの設定を構成します。

## 構文

    Set-OfficeWebAppsFarm [-AllowCEIP <SwitchParameter>] [-AllowHttp <SwitchParameter>] [-AllowHttpSecureStoreConnections <SwitchParameter>] [-CacheLocation <String>] [-CacheSizeInGB <Nullable>] [-CertificateName <String>] [-ClipartEnabled <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DocumentInfoCacheSize <Nullable>] [-EditingEnabled <SwitchParameter>] [-ExcelAllowExternalData <SwitchParameter>] [-ExcelConnectionLifetime <Nullable>] [-ExcelExternalDataCacheLifetime <Nullable>] [-ExcelPrivateBytesMax <Nullable>] [-ExcelRequestDurationMax <Nullable>] [-ExcelSessionTimeout <Nullable>] [-ExcelWarnOnDataRefresh <SwitchParameter>] [-ExcelWorkbookSizeMax <Nullable>] [-ExternalURL <String>] [-FarmOU <String>] [-Force <SwitchParameter>] [-InternalURL <String>] [-LogLocation <String>] [-LogRetentionInDays <Nullable>] [-LogVerbosity <String>] [-MaxMemoryCacheSizeInMB <Nullable>] [-MaxTranslationCharacterCount <Nullable>] [-OpenFromUncEnabled <SwitchParameter>] [-OpenFromUrlEnabled <SwitchParameter>] [-OpenFromUrlThrottlingEnabled <SwitchParameter>] [-PicturePasteDisabled <SwitchParameter>] [-Proxy <String>] [-RecycleActiveProcessCount <Nullable>] [-RemovePersonalInformationFromLogs <SwitchParameter>] [-RenderingLocalCacheLocation <String>] [-SSLOffloaded <SwitchParameter>] [-TranslationEnabled <SwitchParameter>] [-TranslationServiceAddress <String>] [-TranslationServiceAppId <String>] [-WhatIf [<SwitchParameter>]]

## 解説

**Set-OfficeWebAppsFarm** コマンドレットは、既存の Office Web Apps サーバー ファームの設定を構成します。

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
<td><p><strong>AllowCEIP</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Office Web Apps サーバー ファーム内のすべてのサーバーで、カスタマー エクスペリエンス向上プログラム (CEIP) レポートを有効にします。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、Office Web Apps サーバー ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>AllowHttp</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>IIS サイトが HTTP アクセスに対してポート 80 を準備する必要があることを示します。<strong>AllowHTTP</strong> は、すべてのコンピューターが IPSEC (完全な暗号化) を必要とする環境、または機密保持を要するファイルを含まないテスト環境でのみ使用してください。</p>
<p><strong>SSLOffloaded</strong> を有効にすると、自動的に有効にされます。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHttpSecureStoreConnections</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>非 SSL 接続 (HTTP など) を使用して Secure Store 接続を確立できることを示します。既定値は <strong>False</strong> です。</p>
<p><strong>&gt;AllowHTTPSecureStoreConnections</strong> は、すべてのコンピューターが IPSEC (完全な暗号化) を必要とする環境、または機密ファイルが含まれないテスト環境でのみ使用してください。</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheLocation</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>表示された画像ファイルを保存するグローバル ディスク キャッシュの場所を指定します。既定の場所は、<strong>%programdata%\Microsoft\OfficeWebApps\Working\d\</strong> です。</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheSizeInGB</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>グローバル ディスク キャッシュの最大サイズをギガバイト単位で指定します。</p>
<p>型は、<strong>0</strong> または正の整数の、整数値である必要があります。既定サイズは <strong>15</strong> GB です。</p></td>
</tr>
<tr class="even">
<td><p><strong>CertificateName</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>Office Web Apps サーバー が HTTPS バインドを作成する目的で使用する証明書のフレンドリ名を指定します。</p>
<p>指定した証明書が見つからないか期限切れの場合、または、指定した値が複数の証明書に関連付けられている場合は、エラーがログに記録され、ファームは作成されません。</p>
<div class="alert">

> [!IMPORTANT]
> この値は、Office Web Apps サーバー ファームに参加するすべてのサーバーで使用されます。つまり、ファーム内のすべてのサーバーがこのフレンドリ名の証明書を持つ必要があります。


</div>
<p><strong>AllowHttp</strong> または <strong>SSLOffloaded</strong> パラメーターを使用している場合は、<strong>CertificateName</strong> パラメーターを指定する必要はありません。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>ClipartEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Office ドキュメントに Office.com からのクリップ アートを挿入できるようにします。この機能には、サーバーから Web への通信が必要です。この通信は、<strong>Proxy</strong> パラメーターで指定するプロキシにより、または、直接、構成されます。</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>DocumentInfoCacheSize</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>メモリ キャッシュに保存されるドキュメント変換レコードの最大数を指定します。</p>
<p>既定値は <strong>5000</strong> レコードです。</p></td>
</tr>
<tr class="even">
<td><p><strong>EditingEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>ブラウザーでの編集のサポートを有効にします。既定値は <strong>False</strong> です。編集機能を使用できる適切なライセンス契約を持っている場合にのみ、<strong>True</strong> に設定します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelAllowExternalData</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>サポートされている外部データを、外部データへの接続が含まれる Excel Web App ワークブックで更新できるようにします。既定値は <strong>True</strong> です。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelConnectionLifetime</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>Excel Web Appの外部データ接続の長さを秒単位で指定します。既定値は <strong>1800</strong> です。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelExternalDataCacheLifetime</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>Excel Web Appの外部データ キャッシュ有効期間の長さを秒単位で指定します。既定値は <strong>300</strong> です。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelPrivateBytesMax</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>Excel Web Appで使用される最大プライベート バイトをメガバイト単位で指定します。<strong>-1</strong> を設定した場合、プライベート バイトの最大サイズは、既定でコンピューター上の物理メモリの 50% に設定されます。</p>
<p>この型は、<strong>-1</strong> または任意の正の整数である必要があります。既定値は <strong>-1</strong> です。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelRequestDurationMax</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>セッションの 1 つの要求の最大持続時間を秒単位で指定します。この時間が経過すると、要求はタイムアウトします。</p>
<p>この型は、<strong>-1</strong> (無期限)、または <strong>1</strong> ～ <strong>2,073,600</strong> の範囲の整数である必要があります。既定値は <strong>300</strong> です。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelSessionTimeout</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>Excel Web Appでユーザー操作のないセッションをアクティブに保つ時間を秒単位で指定します。有効な値は次のとおりです。</p>
<p><strong>-1</strong>   セッションは無期限です。</p>
<p><strong>0</strong>   1 つの要求が終わったときにセッションの有効期限が終了します。</p>
<p><strong>1</strong> ～ <strong>2,073,600</strong>   1 秒～ 24 日の間、アクティブです。既定値は <strong>450</strong> です。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelWarnOnDataRefresh</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Excel Web App でデータが更新されるとき、警告ダイアログ ボックスの表示のオンとオフを切り替えます。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelWorkbookSizeMax</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>読み込み可能なブックの最大サイズ (MB 単位) を指定します。</p>
<p>この型は、<strong>1</strong> ～ <strong>1000</strong> の範囲の整数である必要があります。既定値は <strong>5</strong> です。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalURL</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>クライアントがインターネットから Office Web Apps サーバー ファームにアクセスする目的で使用する URL ルートを指定します。負荷分散されたマルチサーバーの Office Web Apps サーバー ファームの場合、外部 URL は、外向きのロード バランサーの IP アドレスにバインドされます。</p>
<p>Office Web Apps サーバー ファームは、<strong>ExternalURL</strong> または <strong>InternalURL</strong> で設定した、少なくとも 1 つの URL を必要とします。内部および外部 URL の両方を設定することもできます。</p></td>
</tr>
<tr class="even">
<td><p><strong>FarmOU</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>サーバーが Office Web Apps サーバー ファームに参加する目的でメンバーである必要がある Active Directory 組織単位 (OU) の名前を指定します。許可されていないサーバー (つまり、OU 内にないサーバー) を、Office Web Apps サーバー ファームに参加させないようにする目的で、このパラメーターを使用します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>ユーザー プロンプトを表示せずに、すべての確認に対して [はい] と回答します。</p></td>
</tr>
<tr class="even">
<td><p><strong>InternalURL</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>クライアントがイントラネットから Office Web Apps サーバー ファームにアクセスする目的で使用する URL ルートを指定します。</p>
<p>Office Web Apps サーバー ファームは、<strong>ExternalURL</strong> または <strong>InternalURL</strong> で設定した、少なくとも 1 つの URL を必要とします。内部および外部 URL の両方を設定することもできます。</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLocation</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>アクティビティ ログが保存される、ローカル コンピューターでの場所を指定します。</p>
<p>この場所は、ファーム内のすべてのサーバーに適用され、サーバーごとにカスタマイズはできません。既定の場所は、<strong>%programdata%\Microsoft\OfficeWebApps\Data\Logs\ULS\</strong> です。</p>
<p>ログが保存されるドライブに、十分な空きディスク領域があることを確認してください。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>LogRetentionInDays</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>ログ エントリを保持する日数を指定します。構成された日付より古いログ エントリはトリムされます。</p>
<p>この型は、<strong>0</strong> ～ <strong>365</strong> の範囲の整数である必要があります。既定値は <strong>7</strong> です。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>LogVerbosity</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>トレース ログ ファイルに保存される情報の量を指定します。値は、次のとおりです。</p>
<p><strong>VerboseEX</strong> は、トレース ログ ファイルに (最も情報量が多い) 低レベルの詳細を書き込みます。大規模になるトレースで役立ちます。</p>
<p><strong>Verbose</strong> は、トレース ログ ファイルに低レベルの詳細を書き込みます。</p>
<p><strong>Medium</strong> は、トレース ログ ファイルに中レベルの詳細を書き込みます。</p>
<p><strong>High</strong> は、トレース ログ ファイルに (情報量が少ない) 高レベルの詳細を書き込みます。</p>
<p><strong>Monitorable</strong> は、監視する必要がある特殊なコード パスおよびアクションを示すトレースを作成します。</p>
<p><strong>Unexpected</strong> は、監視する必要がある予測外のコード パスおよびアクションを示すトレースを作成します。</p>
<p><strong>None</strong> は、トレース ログ ファイルにトレース情報を書き込みません。</p>
<div class="alert">

> [!IMPORTANT]
> <STRONG>LogVerbosity</STRONG> を長時間、低レベルのままにするとパフォーマンスを低下させます。


</div>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>MaxMemoryCacheSizeInMB</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>レンダリング キャッシュが使用できるメモリの最大量をメガバイト単位で指定します。</p>
<p>型は、<strong>0</strong> または正の整数の、整数値である必要があります。既定サイズは <strong>1024</strong> MB です。</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxTranslationCharacterCount</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>ドキュメントが翻訳できるようにする目的で、含める文字の最大数を指定します。</p>
<p>型は整数値である必要があります。設定できる値は、2000 から <strong>2,000,000</strong> で、制限をしない場合は <strong>0</strong> を指定できます。既定値は <strong>125,000</strong> です。</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUncEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>オンライン ビューアーを使用して UNC パスから Office ファイルを表示するかのオンとオフを切り替えます。</p>
<p>最初に OpenFromUrlEnabled を True に設定し、オンライン ビューアーで UNC パスのファイルを表示できるようにします。</p></td>
</tr>
<tr class="odd">
<td><p><strong>OpenFromUrlEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>オンライン ビューアーを使用して、URL または UNC パスから Office ファイルを表示する機能の有効と無効を切り替えます。</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUrlThrottlingEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>一定時間内での、特定のサーバーからの &quot;URL から開く&quot; 要求の数を調整します。既定の調整値は、構成できません。この値により、Office Web Apps サーバー ファームで、オンライン ビューアーで表示されるコンテンツの要求が単一サーバーを占有しないようにします。</p></td>
</tr>
<tr class="odd">
<td><p><strong>PicturePasteDisabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Ｗeb ページから Office Web Apps に画像を貼り付ける機能を無効にします。既定値は <strong>False</strong> です。<strong>OpenFromURLEnabled</strong> を <strong>True</strong> に設定して、<strong>PicturePasteDisabled</strong> を設定しないか、<strong>False</strong> に設定すると、ユーザーは画像を Office Web Apps に貼り付けることができます。</p></td>
</tr>
<tr class="even">
<td><p><strong>Proxy</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>外部サイトへの HTTP 要求を可能にする目的で構成されたプロキシ サーバーの URL を指定します。一般的には、<strong>ClipartEnabled</strong> および <strong>TranslationEnabled</strong> パラメーターとともに構成されます。</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecycleActiveProcessCount</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Nullable</p></td>
<td><p>プロセスがリサイクルされる前に、単一の Word または PowerPoint プロセスが表示できるファイルの数を指定します。</p>
<p>The type must be an integer value in the range of <strong>1</strong> to <strong>1000</strong>. The default value is <strong>5</strong>.</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>RemovePersonalInformationFromLogs</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Provides a best effort scrub of personal information from Office Web Apps サーバー logs and replaces values with a SHA256 hash. Potentially scrubbed information can be:</p>
<ul>
<li><p>ドキュメント名および URL</p></li>
<li><p>IP アドレス</p></li>
<li><p>電子メール アドレス</p></li>
<li><p>ユーザー名</p></li>
</ul>
<p>既定値は <strong>False</strong> です。このパラメーターを有効にすると、個人情報が Office Web Apps サーバー ログに記録される可能性があります。</p></td>
</tr>
<tr class="odd">
<td><p><strong>RenderingLocalCacheLocation</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>Word および PowerPoint Viewing Service が使用する一時的なキャッシュの場所を指定します。</p>
<p>既定の場所は、<strong>%programdata%\Microsoft\OfficeWebApps\Working\waccache\</strong> です。</p></td>
</tr>
<tr class="even">
<td><p><strong>SSLOffloaded</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Office Web Apps サーバー ファーム内のサーバーに、SSL がロード バランサーにオフロードされることを示します。<strong>SSLOffloaded</strong> が有効にされると、Web アプリケーションは、ローカル サーバーのポート 80 (HTTP) にバインドされます。しかし、CSS または画像のようなその他のリソースを参照する HTML は、参照に HTTPS URL を使用します。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationEnabled</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><div class="alert">

> [!IMPORTANT]
> 各言語間でテキストを翻訳するオンライン サービスである Microsoft Translator を使用する、自動的なドキュメント翻訳のサポートを有効にします。翻訳されたファイルは Word Web Appで表示されます。Microsoft Translator はオンライン サービスであることから、直接の、または <STRONG>Proxy</STRONG> パラメーターで指定するプロキシを使用する、サーバーから Web への通信を有効にする必要があります。<BR>Microsoft Translator は、翻訳の品質を向上する目的でデータを収集することがあります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>TranslationServiceAddress</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>翻訳要求の送信先翻訳サーバーの URL を指定します。既定値は Microsoft Translator オンライン サービスです。通常、このパラメーターは使用しません。ただし、翻訳サービスを変更する必要がある場合は除きます。</p>
<div class="alert">

> [!IMPORTANT]
> この変更を有効にするには、Office Web Apps サーバー ファーム内のすべてのサーバーを再起動する必要があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationServiceAppId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>翻訳サービスのアプリケーション ID を指定します。既定値は Office Web Appsの公開アプリケーション ID です。通常、このパラメーターは使用しません。ただし、追加サービスについて Microsoft Translator とネゴシエートし、非公開アプリケーション ID が提供された場合は除きます。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する代わりに、コマンドの実行結果を説明するメッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\------------------ 例 1 ---------------------

    Set-OfficeWebAppsFarm -ClipartEnabled:$true

この例では、Office.com からのクリップ アートの挿入を有効にします。

\------------------ 例 2 ---------------------

    Set-OfficeWebAppsFarm -EditingEnabled:$true

この例は、Office Web Apps の編集機能を有効にします。

\------------------ 例 3 ---------------------

    Set-OfficeWebAppsFarm -OpenFromUncEnabled:$false

この例は、UNC パスから Office ファイルを表示する機能をオフにします。

## 関連項目


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

