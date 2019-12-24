# Changelog

## 1.0.0

### Major Changes

- f96a517: Drop `immediate` option from the `useMachine` hook. It wasn't safe for async React. If you need to send events to your created machine before it has a chance to start in React's commit phase for your component then you have to implement queuing of events appropriate for your use case.

### Patch Changes

- Updated dependencies [6b3d767]
  - xstate@4.7.5

All notable changes to this project will be documented in this file.

## [0.8.1]

- Services are now kept up to date

## [0.8.0]

- The `useActor()` hook is now available.
- Support for persisted states

## [0.7.1]

- Actions passed into `useMachine(..., { actions: { ... } })` will now be kept up-to-date and no longer reference stale data.

## [0.7.0]

### Added

- Machine configuration can now be merged into the options argument of `useMachine(machine, options)`. The following Machine Config options are available: `guards`, `actions`, `activities`, `services`, `delays` and `updates` (NOTE: `context` option is not implemented yet, use `withContext` or `withConfig` instead for the meantime)

```js
const [current, send] = useMachine(someMachine, {
  actions: {
    doThing: doTheThing
  },
  services: {
    /* ... */
  },
  guards: {
    /* ... */
  }
  // ... etc.
});
```
