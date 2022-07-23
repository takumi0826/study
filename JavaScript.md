# 業務で使用する js まとめ

## 配列から重複を削除する。

- new Set()を使用

```ts
const array = [1, 2, 1, 2, 3];
const s = [...new Set(array)];
console.log(s); // [1,2,3]
```

## オブジェクトの詰め替え

- reduce()を使用

```ts
const arr = [
  { id: "001", name: "hoge" },
  { id: "002", name: "fuga" },
];
const newArr = arr.reduce((prev, curr) => {
  prev[curr.id] = curr.name;
  return prev;
}, {});
console.log(newArr); //{001: 'hoge', 002: 'fuga'}
```

## 配列にオブジェクトを追加

- スプレッド演算子を使用

```ts
const items: Item[] = [{ id: "001", name: "hoge" }];
const obj: Item = { id: "002", name: "fuga" };

const addItem = (arr: Item[], obj: Item): Item[] => {
  return [...arr, obj];
};
addItem(items, obj);
// [
//   { id: "001", name: "hoge" },
//   { id: "002", name: "fuga" }
// ]
```

## オブジェクトの key または value を取得

- Object.keys()
- Object.values()

```ts
const obj = { a: 1, b: 2 };
Object.keys(obj); // ['a', 'b']
Object.values(obj); // [1, 2]
```

## 数字を 0 埋めしたいとき

- padStart()

```ts
const num = "1";
num.padStart("0", 3); // '001'
```

## オブジェクト内の変数を取り出して使用

- 何度も参照するときに使用する

```ts
const items = { id: "001", name: "hoge" };
const { id, name } = items;

console.log(id); // '001'
console.log(name); // 'hoge'
```
