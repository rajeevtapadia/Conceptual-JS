## `setTimeout()`
- `setTimeout` allows us to run a function once after the interval of time.
```javascript
let timerId = setTimeout(func|code, [delay], [arg1], [arg2], ...)
```

## `setInterval()`
- `setInterval` allows us to run a function repeatedly, starting after the interval of time, then repeating continuously at that interval.
```javascript
let timerId = setInterval(func|code, [delay], [arg1], [arg2], ...)
```
## Canceling with `clearTimeout` or `clearInterval`

A call to `setTimeout` or `setInterval` returns a “timer identifier” `timerId` that we can use to cancel the execution.
```javascript
let timerId = setTimeout(...);
let intervalId = setInterval(...);

clearTimeout(timerId);
clearInterval(intervalId)
```

## Nested `setTimeout`
Instead of `setInterval` we can use nested `setTimeout`
```javascript
let timerId = setTimeout(function tick() {
  alert('tick');
  timerId = setTimeout(tick, 2000); // (*)
}, 2000);
```

## Zero delay `setTimeout()`
- `setTimeout` if called as `setTimeout(func, 0)` schedules `func` for immediate execution, but as scheduler is only invoked after the current script is complete, `func` will get executed as soon as the current script is completed.
