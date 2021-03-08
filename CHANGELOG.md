# [0.2.0](https://github.com/posva/pinia/compare/0.1.0...0.2.0) (2021-03-08)

### Bug Fixes

- only set state provider if a state exists ([#248](https://github.com/posva/pinia/issues/248)) ([3634847](https://github.com/posva/pinia/commit/363484735b5402b45d47ebd7dc2dfde4f00660d6))
- outlive components lifespan ([8516c48](https://github.com/posva/pinia/commit/8516c4828415c658a1b6b7587ce9277f7b6a02a9)), closes [#370](https://github.com/posva/pinia/issues/370)

### Continuous Integration

- add size check ([df59e90](https://github.com/posva/pinia/commit/df59e90422243d36f33cb7cb6c13fb3d30ca0cba))

### Features

- **nuxt:** add buildModule ([b1566f7](https://github.com/posva/pinia/commit/b1566f7586cbd8f444fff48da4b5a8dfb5cb0951))
- **nuxt:** expose nuxt context as $nuxt ([73c48be](https://github.com/posva/pinia/commit/73c48be04d2899ad92d0a2d8a2df210025ebd14a))
- add PiniaPlugin ([b3db04a](https://github.com/posva/pinia/commit/b3db04a807ffdc50e53b4ee7d5a2f2a818da881a))
- deprecate createStore in favor of defineStore ([76c3f95](https://github.com/posva/pinia/commit/76c3f9594615377dca5b5398b613e411360f6af3))

### BREAKING CHANGES

- files in dist folder are renamed to match official libs in the Vue ecosystem. Unless you were importing from `pinia/dist`, this won't affect you.
- It's now necessary to create a pinia instance and
  install it:

  ```js
  import { createPinia, PiniaPlugin } from 'pinia'

  const pinia = createPinia()
  Vue.use(PiniaPlugin)

  new Vue({
    el: '#app',
    pinia,
    // ...
  })
  ```

  The `pinia` instance can be passed to `useStore(pinia)` when called
  outside of a `setup()` function. Check the SSR section of the docs for
  more details.

- `setActiveReq()` and `getActiveReq()` have been
  replaced with `setActivePinia()` and `getActivePinia()` respectively.
  `setActivePinia()` can only be passed a `pinia` instance created with
  `createPinia()`.
- Since req as a parameter was replaced with `pinia`,
  `getRootState` is no longer necessary. Replace it with
  `pinia.state.value` to **read and write** the root state`.
- `PiniaSsr` is no longer necessary and has been removed.

# [0.1.0](https://github.com/posva/pinia/compare/0.0.7...0.1.0) (2020-09-22)

### Features

- access the state and getters through `this` ([#190](https://github.com/posva/pinia/issues/190)) ([7bb7733](https://github.com/posva/pinia/commit/7bb7733ff85c6a908c9090da2762186d7afefac5))

### BREAKING CHANGES

- there is no longer a `state` property on the store, you need to directly access it. `getters` no longer receive parameters, directly call `this.myState` to read state and other getters

## [0.0.7](https://github.com/posva/pinia/compare/0.0.6...0.0.7) (2020-07-13)

### Bug Fixes

- make pinia work with nuxt Composition API plugin ([#180](https://github.com/posva/pinia/issues/180)) ([f4e2583](https://github.com/posva/pinia/commit/f4e25832628b25036657be2719e14917d84e74bd)), closes [#179](https://github.com/posva/pinia/issues/179)

## [0.0.6](https://github.com/posva/pinia/compare/0.0.5...0.0.6) (2020-05-25)

### Bug Fixes

- avoid nuxtContext in spa mode ([#170](https://github.com/posva/pinia/issues/170)) ([a0d10f9](https://github.com/posva/pinia/commit/a0d10f93aa65f63fd2d2befa9291707a01ba7667))

### Features

- support raw Vue SSR ([#90](https://github.com/posva/pinia/issues/90)) ([91d7b38](https://github.com/posva/pinia/commit/91d7b380868f53a8ed2fc14ca7a5dbb4d81493f5))

## [0.0.5](https://github.com/posva/pinia/compare/0.0.4...0.0.5) (2020-01-20)

### Bug Fixes

- bind the actions to the store ([5e262da](https://github.com/posva/pinia/commit/5e262da851716bfcada9b7c5297e54c2dded33cf))

### Features

- add nuxt module ([4c0ef7a](https://github.com/posva/pinia/commit/4c0ef7aab23469644ff1e6f388dfcc579c154ba3))
- allow empty state option to make it easy to group stores ([810e0f0](https://github.com/posva/pinia/commit/810e0f0a1d4439438c68df711960d3b7453c0460))
- allow passing the req to useStore ([f250622](https://github.com/posva/pinia/commit/f25062236fc4105bca3165f8fffc3cf3239cf669))
- allow useStore to be called within a store ([fdf6b45](https://github.com/posva/pinia/commit/fdf6b45bff84e039d716ee5e24fc38cf652ad667))
- allow using getters in other getters ([859eeb3](https://github.com/posva/pinia/commit/859eeb3b348bed07faa8583c46d1747f9362f213))
- export types, support state hydration ([89996ed](https://github.com/posva/pinia/commit/89996ed89bb793475ef17e6eaf427518931a56b5))
- handle SSR state hydration ([2998d53](https://github.com/posva/pinia/commit/2998d53272856d64587d5e880f7dca41775356f0))
- state hydration ([db72247](https://github.com/posva/pinia/commit/db722474fceb5a9090136e2fdf4a706b3dd22d88))

## [0.0.4](https://github.com/posva/pinia/compare/0.0.3...0.0.4) (2020-01-09)

### Bug Fixes

- loose TS type for StateTree ([092f169](https://github.com/posva/pinia/commit/092f169b1d0fe42f75becc0749b54561d5029dd4)), closes [#47](https://github.com/posva/pinia/issues/47)

## [0.0.3](https://github.com/posva/pinia/compare/v0.0.1...0.0.3) (2019-12-31)

### Bug Fixes

- global vueCompositionApi name ([a23acef](https://github.com/posva/pinia/commit/a23acef17e692af4822278dc5811c2f52e174f1b))

## [0.0.1](https://github.com/posva/pinia/compare/06aeef54e2cad66696063c62829dac74e15fd19e...v0.0.1) (2019-11-26)

### Features

- add getters ([ad50755](https://github.com/posva/pinia/commit/ad5075589e9e52a3559f0800421faf0430fed674))
- add initial version ([06aeef5](https://github.com/posva/pinia/commit/06aeef54e2cad66696063c62829dac74e15fd19e))
- make getters optional ([18b5756](https://github.com/posva/pinia/commit/18b5756b97d4551acc18667468be60e524159bbf))
- make getters optional ([341fba8](https://github.com/posva/pinia/commit/341fba875d96b9db4053877fa23a37d59b4b57e6))
- use function to build state ([150e4e1](https://github.com/posva/pinia/commit/150e4e19371782dfda7e92a8bbf000c07341dc11))