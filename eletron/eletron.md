# Electron


## Registrar developer en Mac:

https://medium.com/devschile/publicando-en-la-app-store-y-no-morir-en-el-intento-1f17553dc8b8
https://www.electronjs.org/docs/tutorial/mac-app-store-submission-guide

## Registrar para windows: 

https://www.electronjs.org/docs/tutorial/windows-store-guide


## Build with electron forge:

https://www.electronjs.org/docs/tutorial/quick-start#package-and-distribute-your-application
https://github.com/electron-userland/electron-forge

## Build with electron-builder

https://github.com/electron-userland/electron-builder
https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3


## TIPS:

Usar en package json
"main": "public/electron.js",


scripts: "electron-pack": "electron-builder",
    "preelectron-pack": "yarn build"

"build": {
    "appId": "com.electron.intranet",
    "files": [
      "build/**/*",
      "node_modules/**/*"
    ],
    "directories":{
      "buildResources": "assets"
    }
  },


Y

  "homepage": "./"

Ademas en public agregar archivo electron.js con este contenido:


```js
const electron = require('electron');
const app = electron.app;
const BrowserWindow = electron.BrowserWindow;


const path = require('path');
const url = require('url');
const isDev = require('electron-is-dev');


let mainWindow;


function createWindow() {
  mainWindow = new BrowserWindow({width: 900, height: 680});
  mainWindow.loadURL(isDev ? 'http://localhost:3000' : `file://${path.join(__dirname, '../build/index.html')}`);
  mainWindow.on('closed', () => mainWindow = null);
}


app.on('ready', createWindow);


app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit();
  }
});


app.on('activate', () => {
  if (mainWindow === null) {
    createWindow();
  }
});

```