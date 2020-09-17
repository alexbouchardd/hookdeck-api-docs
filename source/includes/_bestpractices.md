# Best Practices

### Handling events

It's common knowledge that you should not take action immediately when receiving webhooks and differ processing asyncronisly via a queue. However, that's precisely why we are building Hookdeck. With Hookdeck you **can** perform operations directly upon receiving an event. We allow for up to a 60s timeout for your operations and it's safe to take action. Implementing a queue on top of the events received from hookdeck would be redudant. You will find Hookdeck most useful when performing processing syncronously and returning representative response and HTTP status code of what occured on your server.

### Verification

As of right now, Hookdeck does not do webhook signature verification, you should perform the verification yourself. That's something we plan to change in the future.

### Idempotency

Most webhooks providers operate on a 'at least once' approach when a webhook event can be attempted more then once, even if it was successful. Hookdeck will identify those events as possible 'duplicate' but will still deliver them (we plan on giving you the control around this in the future). Also, because an 'exactly once approach' is almost impossible to guarantee we also operate on a 'at least once' delivery approach. This means that your API should make sure that any action it takes with an event is idempotent.

Read more about [idempotency](https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation) 
