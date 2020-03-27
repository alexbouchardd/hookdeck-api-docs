# Best Practices

### Handling events

It's common knowledge that you should not take action immediately when receiving webhooks. This is exactly WHY we are building Hookdeck, it's because you CAN take action directly hookdeck webhook event. We allow for up to a 60s timeout for your operations and it's safe to take action. 

### Verification

As of right now, Hookdeck does not do webhook signature verification, you should perform the verification yourself. That's something we plan to change in the future.

### Idempotency

Most webhooks providers operate on a 'at least once' approach when a webhook event can be attempted more then once, even if it was successful. Hookdeck will identify those events as possible 'duplicate' but will still deliver them (we plan on giving you the control around this in the future). Also, because an 'exactly once approach' is almost impossible to guarantee we also operate on a 'at least once' delivery approach. This means that you API should make sure that any action it takes with an event is idempotent.

Read more about [idempotency](https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation) 
