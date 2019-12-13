# 植物の生長
苗に水をかけると生長する仕掛けは、汎用(はんよう)的に利用できる仕組みを作った。以下に従うことで、水がかかった時のアニメの開始、アニメが終了した時点の把握ができるようになる。

# スクリプト
`Assets/Scripts/Grow.cs`を、苗のオブジェクトのルートにアタッチする。このスクリプトは、以下のことを制御する。

- 現在の状態を、苗(Nae)、生長中(Growing)、生長完了(Growed)で表す
- 現在の状態は、publicのstate変数で、他のスクリプトからも参照できる
- Naeの時に、水と接触したら(OnTriggetEnter)、Animatorの`Grow`トリガーを有効にする
- 生長アニメーションが完了した時に呼び出すGrowDoneメソッドを持つ。これが呼ばれたら生長が完了した状態に設定する

# アニメーション
原則として、ルートのオブジェクトにAnimatorをアタッチすることを想定している。`Grow`パラメーターをTrigger型で定義。これをトリガーにして、生長アニメーションを開始する。アニメが完了したら、`GrowDone`を呼び出すイベントを設定する。

# まとめ
- GrowスクリプトとAnimatorをルートのオブジェクトにアタッチ
- AnimatorにGrowトリガーを定義して、それで生長が開始するようにする
- 生長が完了したら、イベントで`GrowDone`を呼び出す

以上をやることで、苗が発芽する仕組みを動かすことができる。生長が完了しているかどうかは、`GetComponent<Grow>()`で`Grow`スクリプトのインスタンスを取得して、`state`が`StateType.Growed`かどうかで判定することができる。