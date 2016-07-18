# PHP client for Vk.com API


## Installation

You can get library and all of it dependencies through [composer](https://getcomposer.org/)

`composer require atehnix/vk-client:dev-master`

## Usage

### Simple example

```php
    $api = new Client;

    $response = $api->request('wall.get', ['owner_id' => 1]);
```

### Use Request class

```php
    $api = new Client;

    $request = new Request('wall.get', ['owner_id' => 1]);
    $response = $api->send($request);
```

### Use ExecuteRequest class

Send multiple requests at once

```php
    $api = new Client;

    $execute = ExecuteRequest::make([
        new Request('wall.get', ['owner_id' => 1]),
        new Request('wall.get', ['owner_id' => 2]),
        // ... few requests
        new Request('wall.get', ['owner_id' => 25]),
    ]);

    $response = $api->send($execute);
```

### Use with access token

Set default token in client.

```php
    $api = new Client;

    $api->setDefaultToken("some_token");

    // ...
```

Or set token for specific request.

```php
    $api = new Client;

    // Token in the request is a higher priority than the default token.
    $request = new Request('wall.get', ['owner_id' => 1], "some_token");

    // ...
```

### Authorization

```php
    $auth = new Auth('client_id', 'client_secret', 'redirect_uri');

    echo "<a href='{$auth->getUrl()}'>ClickMe<a>";

    // ...

    $token = $auth->getToken($_GET['code']);
```

### License
[MIT](https://raw.github.com/atehnix/vk-client/master/LICENSE)
