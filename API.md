# Blizzard.js API Reference

A promise-based Node.JS library for the Blizzard Battle.net Community Platform API.

### `.initialize()`

Return an initialized Blizzard.js instance with default options.

Your Battle.net API key is required for all API calls so it must be passed to Blizzard.js with `.initialize()` or with each request.

A user access token is only required for account level requests. A default access token can be passed to `.initialize()` (for a browser environment working with a single user account), or to each request (for a server environment working with multiple user accounts).

Other parameters include `origin` and `locale`. When passed to `initialize()` they are no longer required with each request unless you want to override the default (e.g. when setting US as the default region but you want to request from the EU region instead).

Blizzard.js uses [axios](https://github.com/mzabriskie/axios) internally and requests return fetch promises from axios. The `instance` argument is an axios-compatible default configuration object.

**Parameters**

-   `args` Object
    -   `args.apikey` String - Your private Blizzard API key
    -   `args.token` [String] - A default user access token
    -   `args.origin` [String] - The default API region
    -   `args.locale` [String] - The default API locale
-   `instance` [Object] - An axios instance configuration object

**Example**

```js
const blizzard = require('blizzard.js').initialize({ apikey: BATTLENET_API_KEY });
```

## Account

### `.account.user()`

Fetch an authenticated user's account `id` and `battletag`.

**Parameters**

-   `args` Object
    -   `args.token` String - The user access token
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.account.user({ token: USER_ACCESS_TOKEN, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.account.wow()`

Fetch an authenticated user's World of Warcraft character list.

**Parameters**

-   `args` Object
    -   `args.token` String - The user access token
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.account.wow({ token: USER_ACCESS_TOKEN, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.account.sc2()`

Fetch an authenticated user's Starcraft 2 profile.

**Parameters**

-   `args` Object
    -   `args.token` String - The user access token
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.account.sc2({ token: USER_ACCESS_TOKEN, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

## Diablo 3

### `.d3.data()`

Fetch a Diablo 3 data resource.

**Parameters**

-   `key` String - The data resource key: `follower`, `artisan`, `item`
-   `args` Object
    -   `args.id` String - The data resource ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.d3.data('follower', { id: 'templar', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.data('artisan', { id: 'mystic', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.d3.era()`

Fetch a Diablo 3 era.

**Parameters**

-   `args` Object
    -   `args.id` [Number] - The era ID
    -   `args.token` [String] - A user access token
    -   `args.leaderboard` [String] - The era leaderboard key
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.d3.era({ origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.era({ id: 5, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.era({ id: 5, leaderboard: 'rift-barbarian', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.d3.profile()`

Fetch a Diablo 3 profile.

**Parameters**

-   `args` Object
    -   `args.tag` String - The user battletag
    -   `args.hero` [Number] - The hero ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.d3.profile({ tag: 'skt#1884', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.profile({ tag: 'skt#1884', hero: 287801, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.d3.season()`

Fetch a Diablo 3 season.

**Parameters**

-   `args` Object
    -   `args.id` [String] - The season ID
    -   `args.leaderboard` [String] - The season leaderboard key
    -   `args.token` [String] - A user access token
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.d3.season({ origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.season({ id: 5, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.d3.season({ id: 5, leaderboard: 'rift-barbarian', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

## Starcraft 2

### `.sc2.data()`

Fetch a Starcraft 2 data resource.

**Parameters**

-   `key` String - The data resource key: `achievements`, `rewards`
-   `args` Object
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.sc2.data('achievements', { origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.sc2.data('rewards', { origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.sc2.ladder()`

Fetch a Starcraft 2 ladder.

**Parameters**

-   `args` Object
    -   `args.id` Number - The ladder ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.sc2.ladder({ id: 194163, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.sc2.profile()`

Fetch a Starcraft 2 player profile.

**Parameters**

-   `key` String - The profile resource key: `profile`, `ladders`, `matches`
-   `args` Object
    -   `args.id` Number - The profile ID
    -   `args.name` String - The profile name
    -   `args.region` [String] - The profile region (optional, default `1`)
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.sc2.profile('profile', { id: 2137104, name: 'skt', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.sc2.profile('ladders', { id: 2137104, name: 'skt', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.sc2.profile('matches', { id: 2137104, name: 'skt', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

## World of Warcraft

### `.wow.achievement()`

Fetch an achievement.

**Parameters**

-   `args` Object
    -   `args.id` Number - The achievement ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.wow.achievement({ id: 2144, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.wow.auction()`

Fetch auction data.

**Parameters**

-   `args` Object
    -   `args.realm` String - The slugified realm name
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.wow.auction({ realm: 'proudmoore', origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.wow.boss()`

Fetch boss data.

**Parameters**

-   `args` Object
    -   `args.id` [Number] - The boss ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

**Example**

```javascript
blizzard.wow.boss({ origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

```javascript
blizzard.wow.boss({ id: 24664, origin: 'us' })
  .then(response => {
    console.log(response.data);
  });
```

### `.wow.challenge()`

Fetch challenge data.

**Parameters**

-   `args` Object
    -   `args.realm` [String] - The slugified realm name
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.character()`

Fetch character data.

**Parameters**

-   `keys` String|Array - One or more character resource keys
-   `args` Object
    -   `args.name` String - The character name
    -   `args.realm` String - The slugified realm name
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.data()`

Fetch a WoW data resource.

**Parameters**

-   `key` String - The data resource key
-   `args` Object
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.guild()`

Fetch guild data.

**Parameters**

-   `keys` String|Array - One or more guild resource keys
-   `args` Object
    -   `args.name` String - The guild name
    -   `args.realm` String - The slugified realm name
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.item()`

Fetch item data.

**Parameters**

-   `args` Object
    -   `args.id` Number - The item or set ID
    -   `args.set` [Boolean] - Whether this is an item set request or not
    -   `args.bonuses` [Array] - A list of bonuses to apply to the item
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.mount()`

Fetch mount data.

**Parameters**

-   `args` Object
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.pet()`

Fetch pet data.

**Parameters**

-   `key` String - The pet resource key
-   `args` Object
    -   `args.id` [String] - The pet resource ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.pvp()`

Fetch pvp data.

**Parameters**

-   `args` Object
    -   `args.bracket` String - The pvp bracket ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.quest()`

Fetch quest data.

**Parameters**

-   `args` Object
    -   `args.id` Number - The quest ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.realms()`

Fetch realm data.

**Parameters**

-   `args` Object
    -   `args.realms` [Array] - A list of slugified realm names
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.recipe()`

Fetch recipe data.

**Parameters**

-   `args` Object
    -   `args.id` Number - The recipe ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.spell()`

Fetch spell data.

**Parameters**

-   `args` Object
    -   `args.id` Number - The spell ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object

### `.wow.zone()`

Fetch zone data.

**Parameters**

-   `args` Object
    -   `args.id` Number - The zone ID
    -   `args.origin` [String] - The region key
    -   `args.locale` [String] - A locale code for this region
-   `instance` [Object] - An axios instance configuration object