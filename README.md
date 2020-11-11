## Getting started

This project was started (and stalled) several years ago. As a result, it's running on .NET Framework 4.5.2. It consists of an API project and a helper class library. See below for step-by-step instructions on getting started.

### Requirements

1. A Slingbox connected to your local network
1. A Slingbox account
1. Your Slingbox admin password (see below)
1. .NET Framework 4.5.2
1. Visual Studio
1. VLC Media Player

#### Slingbox admin password

Internally, the Slingbox itself uses an admin password to authenticate requests. To obtain this password:

1. Navigate to the following URL in a web browser: https://newwatchsecure.slingbox.com/watch/slingAccounts/account_boxes_js
1. Log in when prompted. If you are already logged in, the page should load.
1. You should see something similar to the JS below. The block below is formatted for readability. The admin password is bolded.
1. Copy this value and keep it somewhere safe.
<pre>
var sling_account_boxes = {
	"memberslingbox": {
		"abcdef1234567890": {
			"lookupByFinderId": true,
			"adminPassword": "<b>your-admin-password</b>",
			"userPassword": "your-user-password",
			"finderId": "your-finder-id",
			"isOwner": true,
			"productSignature": 00,
			"passwordAutoMode": true,
			"displayName": "Your Slingbox Name",
			"memberSlingBoxId": 1234567
		}
	},
	"size": 1
}
</pre>

### Setup
1. Open the project in Visual Studio.
1. Edit `app.config` within Slingbox.Capture.
1. Under `appSettings`:
	a. Insert the IP address of your Slingbox in the value for key `Slingbox_IPAddress`.
	a. Insert the admin password acquired above in the value for key `Slingbox_AdminPassword`.
1. Build and begin debugging Slingbox.Capture. A console window should open and will read `Starting web server... FINISHED. Press any key to quit.` when ready.
1. Open VLC.
1. In the Media menu, click "Open Network Stream".
1. Copy the following URL into the box: `http://localhost:9090/api/stream/slingbox`.
1. If everything worked, you should see some activity (see below) in the console window and the output of your cable box should appear in VLC.
<pre>
Starting web server... FINISHED. Press any key to quit.
Issuing forceOkStatus request... COMPLETE
Issuing device request... COMPLETE
Issuing stream request... COMPLETE
Opening video stream... COMPLETE

Beginning stream playback...
</pre>