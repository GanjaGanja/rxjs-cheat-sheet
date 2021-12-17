# RxJS 7 operators Cheat Sheet

List of the most used RxJS operators (at least from my experience) and description.

<br />

## Join Operators

### combineLatestWith
Create an observable that combines the latest values from all passed observables and the source into arrays and emits them.

### concatWith
![Image of 'concatWith' operator](/rxjs-cheat-sheet/assets/img/concat.png "Image of 'concatWith' operator")

Emits all of the values from the source observable, then, once it completes, subscribes to each observable source provided, one at a time, emitting all of their values, and not subscribing to the next one until it completes.

This operator will sequentially emit the Observable given as input and proceed to the next one.

### mergeWith
Merge the values from all observables to an single observable result.

<br />

## Transformation Operators

### map
Applies a given project function to each value emitted by the source Observable, and emits the resulting values as an Observable.

### mergeMap
Projects each source value to an Observable which is merged in the output Observable.

### switchMap
Projects each source value to an Observable which is merged in the output Observable, emitting values only from the most recently projected Observable.

<br />

## Filtering Operators

### debounce
Emits a notification from the source Observable only after a particular time span determined by another Observable has passed without another source emission.

### filter
Filter items emitted by the source Observable by only emitting those that satisfy a specified predicate.

### take
Emits only the first ```count``` values emitted by the source Observable.

<br />

## Conditional Operators

### find
Emits only the first value emitted by the source Observable that meets some condition.

<br />

## Utility Operators

### tap
Used to perform side-effects for notifications from the source observable. Mostly used for debugging.

<br />

## Error Handling Operators

### catchError
Catches errors on the observable to be handled by returning a new observable or throwing an error.

### retry
This operator will take care of retrying back on the source Observable if there is error and the retry will be done based on the input count given.
