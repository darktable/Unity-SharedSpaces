# Configuration

To build and run your copy of SharedSpaces, you will need to create an application for it on the [Oculus developer dashboard](https://developers.meta.com/horizon/).

## 1. <a id="C1">Application Identifier</a>

Your Oculus application identifier must be placed in [Assets/Resources/OculusPlatformSettings.asset](Assets/Resources/OculusPlatformSettings.asset).

The identifier (**App ID**) can be found in the _API_ section.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/dashboard/dashboard_api.png"  width="800">
</div>

## 2. <a id="C2">Destinations</a>

To recreate the SharedSpaces destinations in your application, locate them under __Engagement__

![Dashboard Platform Services](./Media/dashboard/dashboard_platform_services.png "Dashboard Platform Services")

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/dashboard/dashboard_destinations.png"  width="800">
</div>

SharedSpaces includes five destinations: a Lobby, three private rooms (red, green, and blue), and one public room (purple). Below are their settings:

| API Name | Deeplink Message | Display Name | Description |
| :--- | :--- | :--- | :--- |
| [Lobby](./Media/dashboard/dashboard_destination_lobby.png) | {"is_lobby":"true","map":"Lobby"} | Lobby | The Lobby |
| [RedRoom](./Media/dashboard/dashboard_destination_redroom.png) | {"map":"RedRoom"} | Red Room | The Red Room |
| [GreenRoom](./Media/dashboard/dashboard_destination_greenroom.png) | {"map":"GreenRoom"} | Green Room | The Green Room |
| [BlueRoom](./Media/dashboard/dashboard_destination_blueroom.png) | {"map":"BlueRoom"} | Blue Room | The Blue Room |
| [PurpleRoom](./Media/dashboard/dashboard_destination_purpleroom.png) | {"map":"PurpleRoom","public_room_name":"ThePurpleRoom"} | Purple Room | The Purple Room |

Set __Deeplink Type__ to __Enabled__ and add an image for each destination. For SharedSpaces, set the destination __Audience__ to __Everyone__. Ensure you configure the max group launch capacity for each destination to enable the group launch feature.

## 3. <a id="C3">Data Use Checkup</a>

Request access to the platform data required by SharedSpaces. Under __Data Use Checkup__, add these items and submit for certification:

- User ID
- User Profile
- Deep Linking
- Friends
- Invites

## 4. <a id="C4">Upload to Release Channel</a>

To use platform features, upload an initial build to a release channel.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/DeveloperHub.png"  width="800">
</div>

Package your project, open the Meta Developer Hub app, go to App Distribution, and find your app. Choose a Release Channel and press Upload.

After uploading, view your build on the Oculus Developer Dashboard under Distribution -> Release Channels. Once tests pass, go to Distribution -> Release Channels, click the release channel, go to Users, and click Email Invite Users. Invite users with emails associated with Quest devices to download the app and pass the entitlement check. Without an invitation, the Oculus platform won't function correctly.

If done correctly, the app will appear in your app library on your Quest device, ready for download and installation. Afterward, you can upload a development or shipping build directly to your device, ensuring the entitlement check always passes.

Each time you upload a new build, delete the app data on your Quest device before launching. Go to Settings -> Storage, find your app, and delete the app data.

To test with other users, add them to the channel. More information is available in the [Add Users to Release Channel](https://developers.meta.com/horizon/resources/publish-release-channels-add-users/) topic.

Once the initial build is uploaded, you can use any development build with the same application ID without uploading every build to test local changes.

## 5. <a id="C5">Setup User Reporting</a>

We implemented the required User reporting for all multiplayer applications using the default system. The implementation is in [SharedSpacesApplication.cs](./Assets/SharedSpaces/Scripts/SharedSpacesApplication.cs#L248-L255).

Set it up in the dashboard: [Setup User reporting Settings](https://developers.meta.com/horizon/resources/reporting-plugin/)
