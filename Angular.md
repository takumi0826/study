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
