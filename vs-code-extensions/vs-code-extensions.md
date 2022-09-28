# Extensiones De Visual Studio Code

code --install-extension 2gua.rainbow-brackets
code --install-extension adpyke.codesnap
code --install-extension alefragnani.Bookmarks
code --install-extension bierner.markdown-preview-github-styles
code --install-extension bradlc.vscode-tailwindcss
code --install-extension cesium.gltf-vscode
code --install-extension chris-noring.node-snippets
code --install-extension christian-kohler.npm-intellisense
code --install-extension christian-kohler.path-intellisense
code --install-extension CodeStream.codestream
code --install-extension dbaeumer.vscode-eslint
code --install-extension donjayamanne.githistory
code --install-extension dsznajder.es7-react-js-snippets
code --install-extension eamodio.gitlens
code --install-extension ecmel.vscode-html-css
code --install-extension EditorConfig.EditorConfig
code --install-extension eg2.vscode-npm-script
code --install-extension En10ve.threejs
code --install-extension EQuimper.react-native-react-redux
code --install-extension esbenp.prettier-vscode
code --install-extension formulahendry.auto-close-tag
code --install-extension formulahendry.auto-rename-tag
code --install-extension hasanakg.firebase-snippets
code --install-extension helgardrichard.helium-icon-theme
code --install-extension jakob101.RelativePath
code --install-extension jasonnutter.search-node-modules
code --install-extension jeremyrajan.webpack
code --install-extension jzmstrjp.color-the-tag-name
code --install-extension Kelvin.vscode-sshfs
code --install-extension KevinParraLpez.kaian
code --install-extension MaxvanderSchee.web-accessibility
code --install-extension mgmcdermott.vscode-language-babel
code --install-extension mhutchie.git-graph
code --install-extension ms-azuretools.vscode-docker
code --install-extension MS-CEINTL.vscode-language-pack-es
code --install-extension ms-vscode-remote.remote-containers
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension ms-vscode.powershell
code --install-extension ms-vscode.vscode-typescript-tslint-plugin
code --install-extension msjsdiag.vscode-react-native
code --install-extension naumovs.color-highlight
code --install-extension Orta.vscode-jest
code --install-extension PKief.material-icon-theme
code --install-extension pnp.polacode
code --install-extension PWABuilder.pwa-studio
code --install-extension riazxrazor.html-to-jsx
code --install-extension ritwickdey.LiveServer
code --install-extension RobbOwen.synthwave-vscode
code --install-extension ruiquelhas.vscode-lowercase
code --install-extension ruiquelhas.vscode-uppercase
code --install-extension Shan.code-settings-sync
code --install-extension shardulm94.trailing-spaces
code --install-extension shd101wyy.markdown-preview-enhanced
code --install-extension skyran.js-jsx-snippets
code --install-extension sldobri.bunker
code --install-extension slevesque.vscode-3dviewer
code --install-extension spywhere.guides
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension streetsidesoftware.code-spell-checker-spanish
code --install-extension syler.sass-indented
code --install-extension usernamehw.errorlens
code --install-extension waderyan.nodejs-extension-pack
code --install-extension WakaTime.vscode-wakatime
code --install-extension webhint.vscode-webhint
code --install-extension wix.vscode-import-cost
code --install-extension wmaurer.change-case
code --install-extension xabikos.JavaScriptSnippets
code --install-extension ysemeniuk.emmet-live
code --install-extension Zignd.html-css-class-completion

## Para agregar code a la terminal hay que:

Open the Command Palette (Cmd+Shift+P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.

Para copiar las extensiones que tenemos hay que poner en terminal:

#### MAC:

code --list-extensions | xargs -L 1 echo code --install-extension  

#### WINDOWS:

code --list-extensions | % { "code --install-extension $_" }

Y luego copiar el output que nos genera y podemos instalar uno por uno.
Por ejemplo:

code --install-extension aaron-bond.better-comments

## Para sincronizar con Github instalar esta extensión:

https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync
