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
