# Spectacle Demo App

## Description

### Features

#### Event listing

- [ ] Add gif showing the functionality

#### Event creation:

- [ ] Add gif showing the functionality

## TODO
#### Must be done
- [ ] Add unit testing setups
- [x] Single Event Card
- [x] List events
  - [x] Error handling message
- [ ] Create Event
  - [x] Fix navigation between pages
  - [ ] Frontend Unit tests
  - [x] Set the event's time too

#### Someday
- [ ] Environment configurations
- [ ] Add logging setup
- [ ] Add analytics
- [ ] Automate with CI/CD
- [x] Cleanup transpiling options
- [ ] Improve chunks for dist in view
- [ ] Skeleton - loading state
- [ ] Paginate and filter event list query
- [ ] Authentication
- [ ] Security rules in Firebase based on Auth
- [ ] Eslint
- [ ] Codecov setup
- [ ] Improve tests setup
  - [ ] Cypress e2e tests with Playwright (responsiveness)
  - [ ] Automated API calls (system tests)
  - [ ] Cron jobs to cleanup the dev database
  - [ ] Add architecture testing for dependency safety TSArch
  - [ ] Setup Jest centrally with projects - advanced reporting
- [ ] Feature flags (in Firebase it's called Remote Configurations)
- [ ] Add translations and localization (for datetime picker and location selector)

### File structure
This is a monorepo, here's the general folder structure:

```json
{ "show folder structure": "TODO" }
```

## How Tos

### Initial setup

_commands are all run from the repository root_

```shell
npm install -g firebase-tools
firebase login
```

### Run in dev

```shell
npm install
npm run dev
```

### Run script only in specific package
```shell
npm run dev -w @spectacle/view
```

### Deploy
```shell
npm run deploy
```

## Technologies used and explained:

1. ReactJS with Vite
2. React Query with the developer tools
3. Firebase : Includes Firestore, Functions, Hosting and Storage.
   - Chose this BaaS (Backend as a Service) for a quick and free MVP setup. Also very interesting in short-medium term as we can use all these interesting features (as suspected for an event planning app) : Authentication, Feature Toggles, Notifications service, Analytics, Emails Plugin, and more. Its economical considering we don't have as much infra to implement.
4. ExpressJS
   - It's not necessarily the solution I would have chosen as we can use RPC calls directly with a [Cloud Functions Client SDK](https://firebase.google.com/docs/functions/callable), however this removes the static typechecking.
   - We could also have used Firestore's REST api directly.
5. Prettier
6. Typescript
   - This adds a lot of overhead but I think it helps when the types are defined in `domain/`. Also useful to generate mock data for tests. This avoids repetitive work and ensures the data integrity.
7. Workspaces & lerna
   - using lerna for its very useful --parallel option. We might be okay without it though. It's a popular lib in monorepos.
   - I would maybe opt for another dependency resolution strategy. hoisting seems risky with the traditionnal npm workspaces. See https://blog.logrocket.com/exploring-workspaces-other-advanced-package-manager-features/.
8. Prettier & ESLint (TODO)
   - Eslint because it handles both js and ts files.