# XO in WebStorm

This document contains some helpful hints for using [`XO`](https://github.com/sindresorhus/xo) in [WebStorm](https://www.jetbrains.com/webstorm/).

## Import and use the XO WebStorm Code Style

This repository includes a [WebStorm Code Style](https://raw.githubusercontent.com/jamestalmage/xo-with-webstorm/master/.editorconfig) for `XO`. Just [download it](https://raw.githubusercontent.com/jamestalmage/xo-with-webstorm/master/.editorconfig) anywhere on your desktop, and then import it in WebStorm preferences.

![](https://raw.githubusercontent.com/jamestalmage/xo-with-webstorm/master/images/import-code-style.png)

## Add an EditorConfig File

WebStorm includes an EditorConfig [plugin](https://plugins.jetbrains.com/plugin/7294-editorconfig). Just download the `.editorconfig` file from [this repository](https://raw.githubusercontent.com/jamestalmage/xo-with-webstorm/master/.editorconfig) and save it in your projects base directory. EditorConfig is widely supported across a number of editors, so it will have benefits for collaborators that use other editors.

## WebStorm ESLint Plugin

WebStorm provides real time highlighting of errors for a variety of linters. Unfortunately, there is not direct support for XO, but there is support for ESLint. Making things work requires you setup ESLint directly, instead of the more convenient XO wrapper. (You can still use XO from the command line)


##### Install Dependencies

In addition to `XO`, you will need to install a number of dependencies that XO usually includes by default. This includes [`eslint-config-xo`](https://github.com/sindresorhus/eslint-config-xo), and a number of plugins. You can just copy and paste the line below. ([`eslint-config-xo-react`](https://github.com/sindresorhus/eslint-config-xo-react) is optional).

    ```
    npm install --save-dev xo eslint eslint-config-xo eslint-plugin-no-use-extend-native eslint-plugin-ava eslint-plugin-unicorn eslint-plugin-promise eslint-plugin-import eslint-config-xo-react
    ```

##### Add an ESLint config

Add an ESLint config to `package.json`. (Again, `xo-react` is optional here).

    ```json
    {
      "eslintConfig": {
        "parser": "babel-eslint",
        "env": {
          "node": true,
          "es6": true
        },
        "extends": [
            "xo/esnext",
            "xo-react",
            "./node_modules/xo/config/plugins.js"
        ]
      }
    }
    ```

###### Configure WebStorms ESLint support

With the above steps complete, configuring WebStorm to provide linter feedback in the editor is straightforward.

Go to `Preferences > Languages and Frameworks > Code Quality Tools > Eslint` and setup 

![](https://raw.githubusercontent.com/jamestalmage/xo-with-webstorm/master/images/configure-eslint.png)

## Help Wanted

If you have additional suggestions, tips or tricks for using `XO` and `WebStorm` together, please [open an issue](https://github.com/jamestalmage/xo-with-webstorm/issues) or submit a Pull Request.

## License

MIT © [James Talmage](http://github.com/jamestalmage)
