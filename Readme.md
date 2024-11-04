## このファイルの使い方
Right Click Checkerは、Script APIを用いてアイテムの右クリックを検出します。
右クリックするアイテムを追加するには、.mcaddon を .zip にかえ、解凍します
その後、ビヘイビアのScirptの、main.jsを開き、中を編集します。


```js
import * as server from '@minecraft/server';

server.world.afterEvents.itemUse.subscribe(ev => {
    if (ev.itemStack.typeId == "elitem:click_checker_rod") {
        ev.source.runCommand(`tellraw @s {"rawtext":[{"text":">>§aクリックされました"}]}`);
    }
    if (ev.itemStack.typeId == "minecraft:stick") {
        ev.source.runCommand(`give @s iron_ingot`);
    }
});
```

このように、
- `ev.itemStack.typeId == `の後にアイテムの名前空間を入力します。カスタムアイテムも対応しています。
- `ev.source.runCommand`の後に実行するコマンドを入力します。
アイテムを追加するときは、`if`を下に追加していけばOKです。

なお、元の二つのファイルは消しても大丈夫です！

使用するときは、アドオンを導入し、実験のベータAPIを必ずONにしてください。

このファイルは、改変・二次配布は問題ありません。サンプルとしてご自由にお使いください！

作：Elsengineer020