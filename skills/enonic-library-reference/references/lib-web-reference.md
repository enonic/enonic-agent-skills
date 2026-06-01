# lib-i18n and lib-websocket API Reference

> Sources:
> - https://developer.enonic.com/docs/xp/7.x/api/lib-i18n
> - https://developer.enonic.com/docs/xp/7.x/api/lib-websocket

---

## lib-i18n

**Import:** `import i18nLib from '/lib/xp/i18n';`
**Gradle:** `include "com.enonic.xp:lib-i18n:${xpVersion}"`

> Localizes phrases from `.properties` resource bundles under `src/main/resources/`.

### localize

Localizes a phrase by searching the provided locales for a translation, falling back to the default if missing.

**Parameters (object):**

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| key | string | yes | — | The phrase key identifier |
| locale | string \| string[] | no | Site language | Locale or array of locales in preferred order |
| values | string[] | no | — | Placeholder values for `{0}`, `{1}`, … substitution |
| bundles | string[] | no | — | Bundle names to search |
| application | string | no | Current app | Application key for resource bundles |

**Returns:** `string` — Localized string with placeholders substituted.

### getPhrases

Returns key/value pairs for all phrases matching the given locales in the specified bundles.

**Parameters (object):**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| locale | string \| string[] | yes | Locale or array in preferred order; empty array uses the default |
| bundles | string[] | yes | Bundle names as paths relative to `src/main/resources/` |

**Returns:** `object` — Phrase keys mapped to localized values.

### getSupportedLocales

Returns the supported locale codes for the specified bundles.

**Parameters (object):**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| bundles | string[] | yes | Bundle names as paths relative to `src/main/resources/` |

**Returns:** `string[]` — Supported locale codes.

---

## lib-websocket

**Import:** `import webSocketLib from '/lib/xp/websocket';`
**Gradle:** `include "com.enonic.xp:lib-websocket:${xpVersion}"`

> Send messages over WebSocket connections opened against an HTTP service that declares `webSocket` support. Socket ids and events arrive via the service's `webSocketEvent` callback.

### send

Transmits a message directly to a specific socket.

| Name | Type | Description |
|------|------|-------------|
| id | string | Socket id |
| message | string | Text message |

**Returns:** `void`

### sendToGroup

Broadcasts a message to all sockets in a group.

| Name | Type | Description |
|------|------|-------------|
| group | string | Group name |
| message | string | Text message |

**Returns:** `void`

### addToGroup

Adds a socket id to a named group.

| Name | Type | Description |
|------|------|-------------|
| group | string | Group name |
| id | string | Socket id |

**Returns:** `void`

### removeFromGroup

Removes a socket id from a named group.

| Name | Type | Description |
|------|------|-------------|
| group | string | Group name |
| id | string | Socket id |

**Returns:** `void`

### getGroupSize

Returns the number of sockets in a group. *(XP 7.6.0+)*

| Name | Type | Description |
|------|------|-------------|
| group | string | Group name |

**Returns:** `number`
