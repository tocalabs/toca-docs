# App Gateways

An App Gateway represents a server for you to deploy your Apps to, where they will be served and hosted from. A Toca platform will always come with a Default App Gateway, this is built into the platform so your Apps will be deployed and hosted from the same server as the rest of the platform but this allows you to define other deploy targets.

An App Gateway is useful when you want to serve and host your App(s) from somewhere other than the default location. One App Gateway can have many apps deployed to it and you can put your App Gateway wherever you want provided it can communicate to the core server via HTTPS.

![App Gateway Diagram](/src/assets/app_gateway.png)

This is useful for a number of reasons:
1. You can host your App on a custom URL (e.g. <https://myapp.mycompany.com>), you just need to make sure the DNS A record for this URL is configured to point to the IP address of the App Gateway server. When you deploy an App on the Default App Gateway it will always be hosted on <https://apps.{platform URL}/app-slug>
2. You can move your App network traffic to a separate server, therefore reducing the load on the main platform
3. You can independently scale your App Gateway server to adapt to increases and decreases in traffic
4. You can have the main platform located behind a firewall but can make an App Gateway public facing so your Apps can be accessed publicly without compromising the security of your main platform
5. You can deploy different versions of the App to the Gateway and Default gateway so you can deploy the draft version on the default gateway for testing and you can deploy your published version of the App to your App Gateway for your app users.
6. You can set up two App Gateways and deploy your App(s) to both of them and use a load balancer to set up a "Blue-green deployment" - you can find out more about this ![here](https://en.wikipedia.org/wiki/Blue%E2%80%93green_deployment).

> SSL provisioning and renewal will be handled internally by an App Gateway so you do not need to worry about configuring SSL certificates. However, if you wish to use a private SSL certificate provider please raise a ticket via <support@toca.io>.
