#共通
##各戦略

taker：

matcher：

giver：

random：


##共通で追加したい機能
・移動先を選ぶときに、多くのエージェントがいる方向への移動が選択されやすいようにしているが、どの程度偏らせるかは、エージェントごとに固有のパラメータを持たせている

・各エージェントはたまに戦略を移動する。戦略を移行するときは、相対的にうまくいっている戦略に高確率で移行する。

・現在の適応度が低いほどほかの戦略に移行しやすく、現在の適応度が高いほどほかの戦略に移行しずらいようにする。戦略移行確立を「コミュニティ内の相対的な適応度の高さの関数」にする場合と、「全コミュニティで共通のかつ不変な適応度の変数、の関数」にする場合、両方できれば。

・各エージェントが戦略を変更するときの遷移確率を、同じコミュニティ内における適応度の高い戦略ほど高くなるようにする



#パラメータ調整
各種パラメータを変化させ、条件と適応的な戦略の対応関係を見ていくことができるように、改善する。以下のような条件でシミュレーションできるようにしたい。

・閉じた系の唯一のコミュニティ

・複数のコミュニティを行き来できるパターン

・うまくいっている時ほどその場にとどまりやすくする＆その逆　の行動パターン
