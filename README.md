# Extra features for rabbitmq/amqp091-go package

[Documentation](https://pkg.go.dev/github.com/lafriks/amqpextra#section-documentation)

## Dialer

Provides:

* Auto reconnect.
* Context aware.
* Configured by WithXXX options.
* Dial multiple servers.
* Notifies ready\unready\closed states.

Examples:

* [Dialer.ConnectionCh](https://pkg.go.dev/github.com/lafriks/amqpextra#example-Dialer.ConnectionCh)
* [Dialer.Consumer](https://pkg.go.dev/github.com/lafriks/amqpextra#example-Dialer.Consumer)
* [Dialer.Publisher](https://pkg.go.dev/github.com/lafriks/amqpextra#example-Dialer.Publisher)

## Consumer

Provides:

* Auto reconnect.
* Context aware.
* Configured by WithXXX options.
* Consumer can process messages in parallel.
* Consumers in-process auto-scaling and backpressure.
* Adds message context.
* Detects queue deletion and reconnect.
* Notifies ready\unready\closed states.

Examples:

* [NewConsumer](https://pkg.go.dev/github.com/lafriks/amqpextra#example-NewConsumer)
* [Wrap](https://pkg.go.dev/github.com/lafriks/amqpextra@v0.16.1/consumer#example-Wrap)

## Publisher

Provides:

* Auto reconnect.
* Context aware.
* Configured by WithXXX options.
* Notifies ready\unready\closed states.
* Publish could wait till connection ready.
* Adds message context.
* Publish a message struct (define only what you need). 
* Supports [flow control](https://www.rabbitmq.com/flow-control.html). 

Examples:

* [NewPublisher](https://pkg.go.dev/github.com/lafriks/amqpextra#example-NewPublisher)

### Consumer middlewares

The consumer could chain middlewares for a preprocessing received message.

Here's some built-in middlewares:

* [HasCorrelationID](consumer/middleware/has_correlation_id.go) - Nack message if has no correlation id
* [HasReplyTo](consumer/middleware/has_reply_to.go) - Nack message if has no reply to.
* [Logger](consumer/middleware/logger.go) - Context with logger.
* [Recover](consumer/middleware/recover.go) - Recover worker from panic, nack message.
* [Expire](consumer/middleware/expire.go) - Convert Message expiration to context with timeout.
* [AckNack](consumer/middleware/ack_nack.go) - Return middleware.Ack to ack message.
