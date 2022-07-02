## Observable

- Observable オブジェクトは、subscribe という名前のメソッドを持つ
- .pipe()を使用することで Operator を繋いで操作することができる。(ここで様々な加工ができる)
- .subscribe() することで実行される。

## Subject

- 任意のタイミングでデータを流したいときに使用する。
- .next()で値を流すことができる。

## BehaviorSubject

- 最後に流れてきた値を保持する
- 初期値を設定でき.getValue() 現在の値を取得することができる。
- .next()で値を流すことができる。
- 変数を直接触れないように asObservable() して取得するのが良い

## of

- 値を Observable で返却する

## from

- 配列を Observable で返却する

## first

- Observable で流れてくる最初のみ取得し返却
- 条件分岐も可能

## filter

- 条件に一致するものを返却
- javaScript の filter とほぼ同じ

## catchError

- エラーをキャッチする。
- エラーハンドリングで使用

## take

- 何回まで実行するかを指定できる。
- 引数に number

## takeUntil

- 任意の Observable が流れたら unsubscribe する。
- 主にメモリリークを防ぐために使用する。
- ngOnDestroy の際に Subject を next し unsubscribe することが多い。

## map

- Observable で流れてくる値を加工できる。
- 例) `map(v => v * 100)`
- tap
- 主にデバッグなどで使用される
- 返却は必要なし

## mergeMap

- Observable を新規に作成し、次の処理に流す。
- 同時にデータを取得したい場合や、実行速度を早めたい場合に使用。

## concatMap

- Observable を新規に作成し、次の処理に流す。
- 非同期処理を順番通りに実行したい場合に使用。

## switchMap

- Observable を新規に作成し、次の処理に流す。
- 途中で新規の Observable が流れてきた場合 実行中の Observable をキャンセルして新しい方を実行する。

## withLatestFrom

- メインの Observable がながれたときに、引数に指定した Observable の最新の値を取得する。

## combineLatest

- 引数に指定した Observable が全て流れると処理が動く。
- 複数の Observable を検知できる。
- 1 つ流れると他の Observable の最新の値を取得する。
