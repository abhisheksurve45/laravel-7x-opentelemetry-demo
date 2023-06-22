# Laravel 7.2X PHP 8.0 Auto Opentelemetry setup


0. Setup

```bash
composer create-project laravel/laravel=^7.24 laravel-7x-opentelemetry-demo --prefer-dist
```

1. Install `opentelemetry-beta`

```bash
pecl install opentelemetry-beta
```

Post this confirm that package is installed by

```bash
php -m | grep opentelemetry
opentelemetry
```

2. Set `discovery` to true

```bash
composer config allow-plugins.php-http/discovery true
```

composer.json

```json
{
    "config": {
        "preferred-install": "dist",
        "platform-check": false,
        "allow-plugins": {
            "php-http/discovery": true
        }
    }
}
```

5. Install opentelemetry packages

```bash
composer require open-telemetry/sdk open-telemetry/opentelemetry-auto-laravel
```

6. Add environment

`.env` file

```env
OTEL_SERVIE_NAME=test
OTEL_PHP_AUTOLOAD_ENABLED=true
OTEL_TRACES_EXPORTER=otlp
OTEL_EXPORTER_OTLP_ENDPOINT=http://xxx.xx.xx.xx:4317
OTEL_PHP_DETECTORS=all
OTEL_EXPORTER_OTLP_PROTOCOL=grpc
```