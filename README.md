# stlite-desktop-example


Current version of the stlite desktop app development

[Updated: use @stlite/desktop-cli instead of @stlite/desktop]

Repo: https://github.com/whitphx/stlite-desktop-example
Sample apps: https://github.com/whitphx/stlite-desktop-example/releases/tag/v0.2.0

    Create a new NPM project with the following package.json. Edit the name field.

{
  "name": "xxx",
  "version": "0.1.0",
  "main": "./build/electron/main.js",
  "scripts": {
    "dump": "dump-stlite-desktop-artifacts",
    "serve": "NODE_ENV=\"production\" electron .",
    "pack": "electron-builder --dir",
    "dist": "electron-builder",
    "postinstall": "electron-builder install-app-deps"
  },
  "build": {
    "files": [
      "build/**/*"
    ],
    "directories": {
      "buildResources": "assets"
    }
  },
  "devDependencies": {
    "@stlite/desktop-cli": "^0.12.0",
    "electron": "20.2.0",
    "electron-builder": "^23.3.3"
  }
}

    Run npm install or yarn install.
    Create streamlit_app directory.
        Any directory name can be used here.
    Create streamlit_app/streamlit_app.py.
        Change the directory name if you used a different name in the previous step.
    Write your Streamlit app code in streamlit_app/streamlit_app.py.
    Optionally, you can add more contents in the directory, including pages/*.py for MPA, any data files, and so on.
    Run yarn dump streamlit_app. If some packages are needed, use -r option like yarn dump streamlit_app -r <PackageName1> ... <PackageNameN>.
        This command creates ./build directory. It includes
            The stlite bare app files.
            streamlit_app directory copied from the one you created in the previous steps.
            site-packages-snapshot.tar.gz that includes the installed package files.
    Run yarn serve for preview. Run yarn dist for packaging.
        electron-builder is used (see the "scripts" field in the package.json) and it simply bundles the ./build directory created in the step above. If you want to customize the built app, e.g., setting the icon, follow its instruction.
