# RxJS 7 Cheat Sheet

List of the most used RxJS operators and Observable creators (at least from my experience) and description. Images were taken from [rxjs-visualize](https://rxjs-visualize.explosionpills.com/).

<br />

## Observable Creators

### forkJoin
![Image of 'forkJoin' operator](/rxjs-cheat-sheet/assets/img/forkJoin.png "Image of 'forkJoin' operator")

Accepts an Array of ObservableInput or a dictionary Object of ObservableInput and returns an Observable that emits either an array of values in the exact same order as the passed array, or a dictionary of values in the same shape as the passed dictionary.

```forkJoin``` does not emit until all source Observables complete. Once that happens, it emits once: an array of the last values that were emitted by the source Observables.

### combineLatestWith (formerly combineLatest)
![Image of 'combineLatestWith' operator](/rxjs-cheat-sheet/assets/img/combineLatest.png "Image of 'combineLatestWith' operator")

Create an observable that combines the latest values from all passed observables and the source into arrays and emits them.

This operator is best used when you have multiple, long-lived observables that rely on each other for some calculation or determination.

```combineLatestWith``` will not emit an initial value until each observable emits at least one value.

### concatWith (formerly concat)
![Image of 'concatWith' operator](/rxjs-cheat-sheet/assets/img/concat.png "Image of 'concatWith' operator")

Emits all of the values from the source observable, then, once it completes, subscribes to each observable source provided, one at a time, emitting all of their values, and not subscribing to the next one until it completes.

This operator will sequentially emit the Observable given as input and proceed to the next one.

### mergeWith (formerly merge)
![Image of 'mergeWith' operator](/rxjs-cheat-sheet/assets/img/merge.png "Image of 'mergeWith' operator")

Merge the values from all observables to an single observable result.

### zipWith (formerly zip)
![Image of 'zipWith' operator](/rxjs-cheat-sheet/assets/img/zip.png "Image of 'zipWith' operator")

Subscribes to the source, and the observable inputs provided as arguments, and combines their values, by index, into arrays.

```zip``` will only emit when all of its sources have emitted since the last time zip emitted.

<br />

## Transformation Operators

### map
![Image of 'map' operator](/rxjs-cheat-sheet/assets/img/map.png "Image of 'map' operator")

Applies a given project function to each value emitted by the source Observable, and emits the resulting values as an Observable.

### mergeMap (formerly flatMap)
![Image of 'mergeMap' operator](/rxjs-cheat-sheet/assets/img/mergeMap.png "Image of 'mergeMap' operator")

Projects each source value to an Observable which is merged in the output Observable.

### switchMap
![Image of 'switchMap' operator](/rxjs-cheat-sheet/assets/img/switchMap.png "Image of 'switchMap' operator")

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
