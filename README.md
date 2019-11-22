# Web Client SDK 

Zoom offers a web based HTML5 client that is used in environments where the end users cannot download zoom desktop clients due to internal IT restrictions or in very low bandwidth environments. 

The web client lets end users join a meeting, receive screen share from other attendees, join the meeting through the phone and leave the meeting. Zoom has added a Web SDK as part of our developer platform to enable developers to embed this into their web apps. Key functions that are exposed include: init meeting config, join meeting, show/hide invite function, show/hide meeting header, get attendees list, call out, invite by phone, mute, unmute, mute all, unmute all, rename, expel, record, lock meeting, leave meeting, end meeting.

Supported Browsers: Google Chrome, Safari, and Mozilla Firefox with their latest version

### Getting Started with Meetings
[Web-Client-SDK Overview](https://marketplace.zoom.us/docs/sdk/native-sdks/Web-Client-SDK/overview)

### Using the SDK

Refer to the [Web SDK Documentation](https://marketplace.zoom.us/docs/sdk/native-sdks/Web-Client-SDK/api-reference)

### Dependencies

```package.json
"dependencies": {
	"react": "16.8.6",
	"react-dom": "16.8.6",
	"redux": "3.7.2",
	"react-redux": "7.1.0",
	"jquery": "^3.4.1",
	"lodash": "^4.17.14",
	"redux-thunk": "2.2.0"
}
```
### CDN Accelerated

Global CDN ```source.zoom.us```

China CDN ```jssdk.zoomus.cn```

### Include the source

```
<script src="https://source.zoom.us/zoom-meeting-1.6.1.min.js"></script>
```
### or

[![NPM](https://nodei.co/npm/zoomus-jssdk.png)](https://nodei.co/npm/zoomus-jssdk/)

```
npm install zoomus-jssdk
```
   
Please notice, 1.6.1 release with two ways, the normal way and npm way(need babel and webpack).

At first, you invoke those three API to init jssdk.
```
console.log('checkSystemRequirements');
console.log(JSON.stringify(ZoomMtg.checkSystemRequirements()));

// it's option if you want to change the jssdk dependency link resources.
// ZoomMtg.setZoomJSLib('https://source.zoom.us/1.6.1/lib', '/av'); // CDN version default
// ZoomMtg.setZoomJSLib('https://jssdk.zoomus.cn/1.6.1/lib', '/av'); // china cdn option 
// ZoomMtg.setZoomJSLib('http://localhost:9999/node_modules/zoomus-jssdk/dist/lib', '/av'); // Local version default

ZoomMtg.preLoadWasm();
ZoomMtg.prepareJssdk();
```
Go to see sample web app (CDN version) how to update 1.3.5 for 1.6.1


[![sample](https://zoom.github.io/sample-app-web/img/participent-joined-meeting.png)]()

## Screen share
```
ZoomMtg.init({
...
screenShare: true, // default, and it also require account's sharing setting enabled.
...    
})
```

## Chat
```
ZoomMtg.init({
...
isSupportChat: true, // default, and it also require account's sharing setting enabled.
...    
})
```

## Webinar notice
If you want to join webinar you will need to add your email to the userEmail property within the join method and set the role to 0 within the meetingConfig function. 

```
ZoomMtg.join({
...
userEmail: "hello@zoom.us",
...    
})
 ```
 ```
  role: 0
 ```
          

### Video, Computer Audio and Sharing Supported browser
Feature | Chrome | firefox | Safari | Edge | IE >=11 | Opera | Vivaldi
------------ | ------------- | ------------ | ------------- | ------------ |  ------------- | ------------ | ------------
Video | yes| yes | yes | yes | no | yes | yes
Computer Audio | yes | only linux | no | no | no | no | yes 
View Sharing | yes | yes | yes | yes | yes| yes | yes
Screen Sharing | >=72 | >=66 | no | >=17 | no | no | yes
Chat | yes | yes | yes | yes | yes | yes | yes | yes

Notice: If you want use IE10, please use WebSDK version 1.4.2. Due to React 16 adoption version 1.5.0 WebSDK doen't support IE10. 

### Support
For any issues regarding our Web Client SDK, please visit our new Community Support Forum at

[https://devforum.zoom.us/](https://devforum.zoom.us/)

[Register your API Key/Secret](https://marketplace.zoom.us/docs/sdk/native-sdks/Web-Client-SDK/getting-started/prerequisites)

[Transitioning-your-developer-apps-to-zooms-marketplace](https://medium.com/zoom-developer-blog/transitioning-your-developer-apps-to-zooms-marketplace-6a8de3386716)


## Quick start
### More detail 
[https://marketplace.zoom.us/docs/sdk/native-sdks/Web-Client-SDK/getting-started/integrate-the-sdk](https://marketplace.zoom.us/docs/sdk/native-sdks/Web-Client-SDK/getting-started/integrate-the-sdk)

###  sample web app (CDN version) with dependecies.

```javascript
git clone https://github.com/zoom/sample-app-web.git --branch master --depth 1
cd sample-app-web/CDN
npm install
npm run start
```

### sample web app (local version)
```javascript
git clone https://github.com/zoom/sample-app-web.git --branch master --depth 1
cd sample-app-web/Local
npm install
npm run start
```

open browser http://localhost:9999

### run demo with https
we provide a https option, other machines can join the demo and test audio and video feature.

notice: the certification signed by localhost. don't use in your production.

```
npm run https
```
open browser https://localhost:9999

## License

Use of this software is subject to important terms and conditions as set forth in the License file

Please refer to [LICENSE.md](LICENSE.md) file for details
