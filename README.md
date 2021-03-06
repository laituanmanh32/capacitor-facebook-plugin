## Installation

```bash
$ npm i --save git+https://github.com/laituanmanh32/capacitor-facebook-plugin.git
$ npx cap sync
```

## Android configuration

In file `android/app/src/main/java/**/**/MainActivity.java`, add the plugin to the initialization list:

```diff
  this.init(savedInstanceState, new ArrayList<Class<? extends Plugin>>() {{
    [...]
+   add(vn.etop.facebookplugin.FacebookPlugin.class);
    [...]
  }});
```

## API

### Init SDK
```ts
import {Plugins} from "@capacitor/core";
const {FacebookPlugin} = Plugins;
let res = await FacebookPlugin.init({appId: "<AppID>"})
console.log(res); // {message: "OK"}
```

### Login

```ts
import {Plugins} from "@capacitor/core";
import {FacebookLoginResult} from "capacitor-facebook-plugin"
const {FacebookPlugin} = Plugins;

const FACEBOOK_PERMISSIONS = 'email,user_birthday,user_photos,user_gender';
const result = await <FacebookLoginResult>FacebookLogin.login({ permissions: FACEBOOK_PERMISSIONS });

if (result.accessToken) {
  // Login successful.
  console.log(`Facebook access token is ${result.accessToken.token}`);
} else {
  // Cancelled by user.
}
```

### Logout

```ts
import { Plugins } from '@capacitor/core';
const { FacebookLogin } = Plugins;

await FacebookLogin.logout();
```
