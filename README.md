# SentinelTeamsNotifyEnrichment
> このレポジトリは Microsoft Sentinel の Teams インシデント通知のサンプルテンプレートです。<p>

![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/70bcbc7f-6b33-4425-a0c8-7c563c7e72dd)
![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/0178e15f-9ec8-496b-9772-6832b42f2d4c)

# 事前準備
本テンプレートは Microsoft Graph の RESTAPI を用いて Azure AD ユーザー情報取得を行います。
Microsoft Graph を利用するために Azure AD のアプリケーション登録を行い、サービスプリンシパルを取得して下さい。

  - テナント ID、クライアント ID の取得
![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/9083e294-dd7d-4dfc-93d2-758e51f635ee)

  - シークレット情報
![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/43f5c3be-0c7c-4144-8200-26c58b7021bf)

  - 「API のアクセス許可」の設定に対して、Microsoft Graph の ``User.Read``, ``User.Read.All`` を与えて下さい。
<img width="1105" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/a0e5afb6-0763-4706-9cb1-bbcc66293470">


# Deploy to Azure
> Azure 環境への適用については、以下ボタンを押して下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelTeamsNotifyEnrichment%2Fmain%2FtemplateTeamsv2.json)

# Requirement
> 以下必要要件になります。<p>

- Teams チャネル投稿が可能な Azure AD アカウント（ユーザー認証）

# Configuration
> デプロイ後、以下設定を行ってください。<p>

- 「API 接続」より、``MicrosoftTeams-(プレイブック名)`` を選択して、``承認する``より Teams が投稿するユーザー認証を行ってください。
<img width="956" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/c7651c51-b799-4167-b783-98f67dcc3613"><BR>
- ロジック アプリ デザイナー画面より、Teams コネクタで接続する Teams/Channel ID を設定して下さい。
<img width="649" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/83a113d6-00d1-495a-b32b-fa1c75482b26">
