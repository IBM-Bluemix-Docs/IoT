---

copyright:
  years: 2016, 2018
lastupdated: "2017-11-03"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.iot_short_notm}} のトラブルシューティング
{: #ts}

{{site.data.keyword.Bluemix_notm}} 上での {{site.data.keyword.iot_full}} の使用についての一般的なトラブルシューティングの質問に対する答えを提供します。
{:shortdesc}

## {{site.data.keyword.iot_short_notm}} 組織へのアクセスの問題
{: #access-expiry-problem}

自分の {{site.data.keyword.iot_short_notm}} 組織にログインできません。
{:shortdesc}

組織の URL または `https://internetofthings.ibmcloud.com` を使用して自分の {{site.data.keyword.iot_short_notm}} 組織に直接アクセスできません。
{: tsSymptoms}

自分の {{site.data.keyword.iot_short_notm}} 組織へのアクセスが期限切れになっている可能性があります。 {{site.data.keyword.Bluemix}} を使用して作成された {{site.data.keyword.iot_short_notm}} 組織では、デフォルトで一時ユーザー・プロファイルが使用されます。
{: tsCauses}

この問題は、{{site.data.keyword.iot_short_notm}} 組織にアクセスするか、{{site.data.keyword.Bluemix_notm}} を使用して、ユーザー・プロファイルの有効期限の設定を変更することで解決できます。 ユーザーの有効期限の設定を変更するには、以下のようにします。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、{{site.data.keyword.iot_short_notm}} サービスを開きます。
2. ナビゲーション・バーから**「メンバー」**をクリックします。
3. **「編集」**アイコンをクリックします。
4. **「アクセスの有効期限が切れました」**のボックスをクリアして、**「保存」**をクリックします。
{: tsResolve}

## {{site.data.keyword.iot_short_notm}} への接続の問題
{: #connection_problem}

{{site.data.keyword.iot_short_notm}} への接続が予期せずドロップまたは切断されます。
{:shortdesc}

{{site.data.keyword.iot_short_notm}} に接続しようとすると、デバイスまたはアプリケーションがエラーを受け取ります。
{: tsSymptoms}

同じ clientID と資格情報を使って 2 つのデバイスが接続を試行している可能性があります。clientID ごとに 1 つの固有の接続のみが許可されています。 同じ ID を使用して 2 つの同時接続を行うことはできません。 アプリケーションは同じ API キーを共有できますが、MQTT ではクライアント ID が常に固有であることが必要です。
{: tsCauses}

この問題は、同じ資格情報を使用して接続を試行する 2 つのデバイスをなくすことで解決できます。
{: tsResolve}

## デバイスが {{site.data.keyword.iot_short_notm}} から断続的に切断されます。
{: #disconnection_problem}

{{site.data.keyword.iot_short_notm}} へのデバイスの接続が予期せず断続的にドロップします。
{:shortdesc}

{{site.data.keyword.iot_short_notm}} サービスに接続しているデバイスが断続的に切断されます。 デバイスは再接続しますが、しばらくすると再び予期せずに切断されます。
{: tsSymptoms}

接続時に使用する MQTT の ping オプションの値が小さすぎるため、接続タイムアウトになったと認識されている可能性があります。 例えば、クライアント MQTT が正しく設定されていない場合、ping はタイミング良く受信されず、接続が閉じてしまいます。
{: tsCauses}

この問題は、接続の ping パラメーターと KeepAlive パラメーターを正しく設定することで修正できます。   
{: tsResolve}

