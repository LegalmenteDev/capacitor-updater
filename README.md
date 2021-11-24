# capacitor-updater

Download app update from url and install it.

And reload the view.

You can list the version and manage it with the command below.
## Install

```bash
npm install capacitor-updater
npx cap sync
```

```
  import { CapacitorUpdater } from 'capacitor-updater'
  import { SplashScreen } from '@capacitor/splash-screen'
  import { App } from '@capacitor/app'

  // Do the update when user leave app
  App.addListener('appStateChange', async(state) => {
      if (!state.isActive) {
        const version = await CapacitorUpdater.download({
        url: 'https://github.com/Forgr-ee/Mimesis/releases/download/0.0.1/dist.zip',
        })
        await CapacitorUpdater.set(version)
      }
  })

  // or do it when click on button
  const updateNow = async () => {
    const version = await CapacitorUpdater.download({
      url: 'https://github.com/Forgr-ee/Mimesis/releases/download/0.0.1/dist.zip',
    })
    // show the splashscreen to let the update happen
    SplashScreen.show()
    await CapacitorUpdater.set(version)
  }
```

## API

<docgen-index>

* [`download(...)`](#download)
* [`set(...)`](#set)
* [`delete(...)`](#delete)
* [`list()`](#list)

</docgen-index>

<docgen-api>
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->

### download(...)

```typescript
download(options: { url: string; }) => Promise<{ version: string; }>
```

download new version from url

| Param         | Type                          |
| ------------- | ----------------------------- |
| **`options`** | <code>{ url: string; }</code> |

**Returns:** <code>Promise&lt;{ version: string; }&gt;</code>

--------------------


### set(...)

```typescript
set(options: { version: string; }) => Promise<void>
```

set version as current version

| Param         | Type                              |
| ------------- | --------------------------------- |
| **`options`** | <code>{ version: string; }</code> |

--------------------


### delete(...)

```typescript
delete(options: { version: string; }) => Promise<void>
```

delete version in storage

| Param         | Type                              |
| ------------- | --------------------------------- |
| **`options`** | <code>{ version: string; }</code> |

--------------------


### list()

```typescript
list() => Promise<{ versions: string[]; }>
```

get all avaible verisions

**Returns:** <code>Promise&lt;{ versions: string[]; }&gt;</code>

--------------------

</docgen-api>


### Inspiraton

- [cordova-plugin-ionic](https://github.com/ionic-team/cordova-plugin-ionic)
- [capacitor-codepush](https://github.dev/mapiacompany/capacitor-codepush)


### Contributer

[jamesyoung1337](https://github.com/jamesyoung1337) Thanks a lot for your guidance and support, it was impossible to make this plugin work without you.
