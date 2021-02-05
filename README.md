# observer
Observer for listening some registered events that trigger React/Vue methods

1. 開一個 observerInterface.js 並且 new 它
```javascript
import Observer from 'observer';

const observerInterface = new Observer();

export default observerInterface;
```

2. 將你要註冊的程式碼餵給 observer
```javascript
observerInterface.subscribe('TOAST_PUSH', (args) => this.push(args));

...

push(options) {
  const message = {
    ...options,
    id: Toasts.idFactory(),
  };
  this.setState((state) => [...state.queue, message]);
}
```

3. 執行剛剛註冊的程式碼，透過 emit 來執行

```javascript
observerInterface.emit('TOAST_PUSH', args);
```

