# Angular 記述まとめ

## ng-template

- `#`でテンプレート名を指定、`let-変数名="使用先のオブジェクトのkey名"`

```html
<ng-template #input let-controls="hoge">
  <p>{{controls}}</p>
</ng-template>
```

- 使用するときは`ngTemplateOutlet`にテンプレート名を指定し、`ngTemplateOutletContext`にオブジェクトを渡す。

```html
<ng-template
  [ngTemplateOutlet]="input"
  [ngTemplateOutletContext]="{hoge: 'hello!!'}"
></ng-template>
```

---

## ng-container

- このタグで囲うと無駄なタグがでない。

```html
<ng-container *ngIf="hoge"><ng-container /></ng-container>
```

---

## directive

- イベントの使い回しをしたいときに使用
- `@HostListener`は`addEventListener`みたいなもの
- `@Input`や`@Output`も可能

```ts
/** バブリングを止める */
@Directive({
  selector: "[appStopClickPropagation]",
})
export class ClickStopPropagationDirective {
  @HostListener("click", ["$event"])
  public onClick(event: any): void {
    event.stopPropagation();
  }
}
```

- 定義した`selector`の名前を html につけることでクリックイベントが付与される。

```html
<p appStopClickPropagation></p>
```

---

## Pipe

- html 側で表示などを加工したい時に使用
- デフォルトで用意されているものもある。
  - `number`... 4 桁以上にカンマをつける。
  - [Angular Pipe 一覧](https://www.multispots.net/angular-pipe/)

```ts
/** 文字列の'/'の前後に空白を追加するパイプ */
@Pipe({
  name: "addBlankToSlash",
})
export class AddBlankToSlashPipe implements PipeTransform {
  transform(val: string): string {
    return val.replace(/\//g, " / ");
  }
}
```

- `|`で区切り定義した名前を横につけることで使用可能

```html
<p>{{ text | addBlankToSlash }}</p>
```

## trackBy

- 再描画が多い ngFor を使用している箇所で使用
- trackBy を使用することで変更箇所の DOM のみ再生成するように設定できる。

```html
// 使用例
<app-item *ngFor="let id of itemIds; trackBy: trackById" [id]="id"></app-item>
```

## @ViewChild, @ViewChildren

- 仮想ではない DOM を操作したい場合に使用
- @ViewChild は取得する DOM が単一の場合
- @ViewChildren は取得する DOM が複数の場合
- 基本的に ngAfterViewInit()と一緒に使用することが多い。(ngAfterViewInit は DOM が生成された後にイベントが発火するため)

```ts
export class AppComponent implements AfterViewInit {
  @ViewChild("hogeElement") hogeElement: ElementRef;
  ngAfterViewInit() {
    this.hogeElement.nativeElement.value = "hello!";
  }
}
```
