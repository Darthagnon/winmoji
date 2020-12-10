## winMoji

<div align="center">
  <h1>
    <img src="https://github.com/ryanSN/winmoji/blob/master/winMoji.gif" alt="winMoji" title="winMoji" />
  </h1>
</div>

![CI](https://github.com/ryanSN/winmoji/workflows/CI/badge.svg)
[![jest](https://facebook.github.io/jest/img/jest-badge.svg)](https://github.com/facebook/jest)
[![Coverage Status](https://coveralls.io/repos/github/ryanSN/winmoji/badge.svg)](https://coveralls.io/github/ryanSN/winmoji)
[![Known Vulnerabilities](https://snyk.io/test/github/ryanSN/winmoji/badge.svg)](https://snyk.io/test/github/ryanSN/winmoji)

Look up emoji's on windows! It's an alternative solution to using the windows onscreen keyboard or on windows 7 where this keyboard does not exist.

🤓😎😆😐

## Features

Clicking on the emoji saves the emoji to your clipboard to be pasted anywhere you need it.
Using shortcut `CTRL+SHIFT+E` will toggle winMoji for quick adding of emojis.

## Download/Install

You can manually download the latest release [here](https://github.com/ryanSN/winmoji/releases)

## How do I contribute to `winMoji` ?

Contributions are welcome! Checkout our [issues](https://github.com/ryansn/winMoji/issues) list or contribute to one of the [PRs](https://github.com/ryansn/winMoji/pulls).
Make your own if you want something and don't see it listed.

## Development

Feel free to contribute to this app. To develop run the following commands

```
$ yarn
$ yarn dev
```

## Distribute

```
$ yarn release
```

**OR**

To package for debug purpose

```
$ yarn pack
```

## :shield: Privacy

This app ~~has~~ had analytics (added in v2.3.0) that will track number of users only ([analytics.js](https://github.com/ryansn/winmoji/blob/master/app/helpers/analytics.js)). **Removed in this fork**

## Changes made in this fork
- removed telemetry (privacy risk)
- removed updater (I dislike autoupdaters)
- changed some build details in package.json
- build installer only, because "portable" Electron means "Electron app that will extract to ```%LocalAppData%\Temp``` then delete itself when you're done. This is bad practice, as Electron programs are massive, and will remove 200mb from your SSD's lifespan each time it's run
- build 32bit only, because:
	- 32bit software takes less RAM; this is RAM-hogging Electron software, so you want to limit RAM usage as much as possible
	- 32bit software is compatible with both 64bit and 32bit systems
	- 64bit provides no useful advantage here.

### RAM usage test
Both 64bit and 32bit versions spawn 4 processes. Here is their total RAM usage according to Process Hacker:

| arch  |Private WS| Private bytes|
|-------|----------|--------------|
| 32bit | 79.93 MB | 140.16 |
| 64bit | 109.22 MB | 148.6 |

Screenshots are included.

### Build method
1. Install [Node.js](https://nodejs.org/en/)
2. Install [Yarn](https://classic.yarnpkg.com/en/docs/install/#windows-stable)
3. Open the WinMoji folder and run ```npm install``` to download all dependencies
4. Then run ```npm run-script build:win```
5. Binaries are found in ```\dist\```
6. NPM binaries didn't work. So I edited line 19 ```release``` command in package.json to remove Linux ```rm``` command and ran ```yarn release```. Despite massive errors appearing, it built successfully.
7. 32bit builds by default. Edit package.json  after ```target: "nsis", "arch": [ "ia32"``` to ```x64``` for 64bit builds. Don't put both, or you'll get a huge installer containing both.

## License

MIT © [Ryan Chatterton](./LICENSE)
