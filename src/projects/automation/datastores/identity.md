# Identity

An Identity represents a link to third party account such as a Microsoft or Google account. This allows you to use actions such as :docs-link[Outlook Send]{key="OutlookSendEmail" type="Action"} or :docs-link[GMail List Emails]{id="GmailListEmails" type="Action"} on behalf of a user. This can be used in any action that takes an Identity as a form of authentication or input.

You can link an identity by selecting one of the :docs-link[Identity Providers]{id="admin/identity_providers"} that have been set up on your system.
You can then select the scopes that you need for this identity, where scopes refer to the permissions you need to execute the necessary actions such as reading an inbox or permission to upload a file.

> For best security practices, you should only ever select the scopes you need for the automation you are intending on using the identity for.

An identity will be stored with an access token and also a refresh token, so you don't have to worry about your identity unexpectedly expiring.
