
```bash
# antd
yarn add antd
yarn add @craco/craco
yarn add craco-less

# alias (skip for now)
# https://www.npmjs.com/package/craco-alias

# sass 原生支持

# prettier, eslint
# Parsing error: No Babel config file detected for /Users/slackbuffer/Projects/defi/chosenweb/src/containers/App.jsx. Either disable config file checking with requireConfigFile: false, or configure Babel so that it can find the config files.       https://tjaddison.com/blog/2021/03/updating-babel-eslint-to-babeleslint-parser-for-react-apps/

# https://levelup.gitconnected.com/how-to-add-a-custom-eslint-configuration-to-a-create-react-app-project-aea3f7c1d7af
# https://www.npmjs.com/package/eslint-plugin-prettier
# https://www.npmjs.com/package/eslint-config-react-app

# https://github.com/prettier/eslint-config-prettier
# https://reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html#eslint



```

- [ ] storage 相关
- [ ] 仅签名需要 gas 吗；access token 的更新逻辑，过期时间多久，refresh_token 保存

- [ ] 重看 react hooks https://github.com/SlackBuffer/under-react；重看 function components

- [ ] npm 引用 github 项目web3-react 内部包，https://github.com/NoahZinsmeister/web3-react
    - uniswap interface 这样做


- [ ] wallet
    - 网络错误提示
    - [x] 刷新 fake disconnect
    - [x] `await` 错误的情况（如网络超时，用户 reject）；Promise race 加上超时
    - metamask 何时需要重新连接
    - [x] 多账号
        - // We currently only ever provide a single account
        - https://docs.metamask.io/guide/getting-started.html#basic-considerations
        - [x] 监听账号变化事件
        - 监听 disconnect，要做，多账号还要能切换到下一个账号
        - 监听网络切换
        - 刷新保持
            - pancakeswap: localstorage `connectorIdv2: injected`
    - 发交易（查询交易要不要签名）
        - https://docs.ethers.io/v5/api/contract/example/#example-erc-20-contract--connecting-to-a-contract--erc20contract
        - https://docs.ethers.io/v5/getting-started/#getting-started--contracts
    - 签名信息表示身份（公钥加时间戳，返回时吧公钥也返回来做校验，时间戳防止重放，会有弹窗，jwt）
        - ca 的作用是将公钥和真实的用户绑定起来（真实的用户信息可以比较方便地甄别，public knowledge）

- router
    - `<Link>` 触发的跳转不会重新加载所有资源；浏览器地址栏直接输入 url 会重新加载所有资源，此时前进后退也会重新加载
    - https://reactrouter.com/docs/en/v6/getting-started/overview

- [ ] context, later
    - auth: https://reactrouter.com/docs/en/v6/examples/auth
    - [x] https://github.com/dai-shi/react-hooks-global-state

- [x] es6 async await

- [ ] data hooks
    - swr，mock api 分页
    - auth 后加载授权内容

- previous hook: https://blog.logrocket.com/accessing-previous-props-state-react-hooks/

- [ ] i18n，later

## [ESLint](https://eslint.org/docs/user-guide/getting-started)

There are 2 primary ways to configure ESLint:
- Configuration **Comments** - use JavaScript comments to embed configuration information directly into a file.
- Configuration **Files** - use a JavaScript, JSON, or YAML file to specify configuration information for an entire directory and all of its subdirectories. This can be in the form of an `.eslintrc.*` file or an `eslintConfig` field in a `package.json` file, both of which ESLint will look for and read automatically, or you can specify a configuration file on the command line.

ESLint comes with a large number of built-in [rules](https://eslint.org/docs/user-guide/configuring/rules) and you can **add more rules through *plugins***. You can modify which rules your project uses either using configuration comments or configuration files. To change a rule setting, you must set the rule ID equal to one of these values:
- `"off"` or `0` - turn the rule off
- `"warn"` or `1` - turn the rule on as a warning (doesn't affect exit code)
- `"error"` or `2` - turn the rule on as an error (exit code will be 1)

To configure a rule which is defined within a plugin you have to prefix the rule ID with the plugin name and a `/`.


ESLint supports the use of third-party plugins. ***Before using the plugin, you have to install it using npm***. To configure plugins inside of a configuration file, use the `plugins` key, which contains a list of plugin names. The `eslint-plugin-` prefix can be omitted from the plugin name.

A [plugin](https://eslint.org/docs/user-guide/configuring/configuration-files#using-a-configuration-from-a-plugin) is an npm package that can add various extensions to ESLint. A plugin can perform numerous functions, including but not limited to adding new rules and exporting shareable configurations. Make sure the package has been installed in a directory where ESLint can require it.

***When using rules, environments or configs defined by plugins, they must be referenced following the convention***:
- `eslint-plugin-foo` → `foo/a-rule`
- `@foo/eslint-plugin` → `@foo/a-config`
- `@foo/eslint-plugin-bar` → `@foo/bar/a-environment`


A configuration file, once extended, can inherit all the traits of ***another configuration file*** (including rules, plugins, and language options) and modify all the options. As a result, there are three configurations, as defined below:
- Base config: the configuration that is extended.
- Derived config: the configuration that extends the base configuration.
- Resulting actual config: the result of merging the derived configuration into the base configuration.
