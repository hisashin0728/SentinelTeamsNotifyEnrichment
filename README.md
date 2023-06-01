# SentinelTeamsNotifyEnrichment
> このレポジトリは Microsoft Sentinel の Teams インシデント通知のサンプルテンプレートです。<p>

![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/70bcbc7f-6b33-4425-a0c8-7c563c7e72dd)

# Deploy to Azure
> Azure 環境への適用については、以下ボタンを押して下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelTeamsNotifyEnrichment%2Fmain%2FtemplateTeams.json)

# Requirement
> 以下必要要件になります。<p>

- Teams チャネル投稿が可能な Azure AD アカウント（ユーザー認証）

# Configuration
> デプロイ後、以下設定を行ってください。<p>

- 「API 接続」より、``MicrosoftTeams-(プレイブック名)`` を選択して、``承認する``より Teams が投稿するユーザー認証を行ってください。
<img width="956" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/c7651c51-b799-4167-b783-98f67dcc3613">
- ロジック アプリ デザイナー画面より、Teams コネクタで接続する Teams/Channel ID を設定して下さい。
<img width="649" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/83a113d6-00d1-495a-b32b-fa1c75482b26">
