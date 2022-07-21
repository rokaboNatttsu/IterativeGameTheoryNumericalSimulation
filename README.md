# Simulator()の初期化パラメータ

ROUND：行動の繰り返し数。

SQR：2次元正方形領域の辺の長さ。正の整数限定。デフォルト=20

AGENT_NUM：エージェント数。正の整数限定。デフォルト=1000

ASSEMBLY_PARAM：エージェントが、人口密度の大きい方向に移動する傾向を決める。大きい値ほど、人口密度の高いほうに向かいやすい。正の実数限定。デフォルト=1

PRESSHURE_2_CENTER：2次元平面上の中央に向かって移動する傾向。0のとき、中央に向かう傾向がなくなる。二次元平面領域には端っこがり、この値を0より大きくしておかないと、エージェントが端に偏る傾向がある。正の実数限定。デフォルト=0.01

AMP_OF_ADVANTAGES_OF_GROUPING：人口密度の高いところに移動したときに得られる得の程度を指定する。大きい値を指定するほど、人口密度の高い場所にいることのメリットが大きくなる。実数限定。デフォルト＝１

TMGR_WAIGHT：T＝Taker、M＝Matcher、G＝Giver、R＝Random、の順で初期の戦略の確立を指定する。0を指定すると、その戦略は存在しないものとして扱う。デフォルト=[1/4,1/4,1/4,1/4]

STRATEGY_SHIFT_MAX_RATE：「１エージェントが１時間区間で戦略を変える確率」の上限を指定。0のとき、各エージェントの戦略は固定される。変更後の戦略には、現状適応的な戦略が選ばれやすい。0~1の実数限定。デフォルト=0

PENALTY_LINE：(r, a) でタプル形式で指定する。r = 「コミュニティ内で略奪行動をとったエージェント数」÷(「コミュニティ内で略奪行動をとったエージェント数」ー「コミュニティ内で協力行動をとったエージェント数」)　でrを定義したとき、r < PENALTY_LINE の集団では、略奪行動をとったエージェントがペナルティを受ける。ペナルティの大きさは、a*max(0, 「コミュニティ内で略奪行動をとったエージェント数」-「コミュニティ内で協力行動をとったエージェントの平均損得値」) となる。rの値の範囲は,\、0 <= r < 1　であり、aの値の範囲は0 < a (1 < a を推奨)である。デフォルト=(r=0,a=1)では、ペナルティは存在しない。

INITIALIZE_RUN：シミュレーションを始める前に、コミュニティを形成するために、シミュレーションと同じ条件でエージェントを動かす回数。デフォルト＝1000

#   メソッド

simulator.run(r) : r回の行動とその結果の記録をする。 rを省略すると1回行動する

simulator.plot_current_point_histgrams(savefig_name) : 戦略ごとの、前回の行動時の損得値のヒストグラムを出力する。savefig_nameに画像ファイル名を指定すると、画像で保存される。指定しない場合、画像ファイルは出力されない

simulator.plot_point_sum_histgrams(savefig_name) : 前回の行動時の戦略ごとの、これまでのすべての損得値の合計のヒストグラムを出力する。savefig_nameに画像ファイル名を指定すると、画像で保存される。指定しない場合、画像ファイルは出力されない

simulator.plot_transition_number_of_strategy(savefig_name) : 戦略ごとに、その戦略をとるエージェントの数の変化を出力する。savefig_nameに画像ファイル名を指定すると、画像で保存される。指定しない場合、画像ファイルは出力されない

simulator.traceplot_average_point_for_all_strategy(savefig_name) : 戦略ごとに、その戦略をとるエージェントの平均損得値の変化を出力する。savefig_nameに画像ファイル名を指定すると、画像で保存される。指定しない場合、画像ファイルは出力されない

simulator.plot_2d_hist_for_strategy(savefig_name) : 戦略ごとに、その戦略をとるエージェントの平面空間上の分布(ヒートマップ)を出力する。savefig_nameに画像ファイル名を指定すると、画像で保存される。指定しない場合、画像ファイルは出力されない

simulator.run_and_plot_template(ROUND) ： ROUND回行動し、その結果をテンプレ形式で出力する。

# 各戦略

taker：常に略奪する。あだ名は「略奪者」

matcher：ほかのエージェントの行動の多数派に追従する戦略。すなわち、前回協力したエージェントが多ければ今回協力し、前回略奪したエージェントが多ければ今回略奪する。あだ名は「キョロ充」

giver：常に協力する。あだ名は「間抜け」

random：協力することもあれば略奪することもある。周りのエージェントの行動と関係なくランダムに自身の行動を選択する。あだ名は「気分屋」。

# 他

・Cooporationが多い集団ほど成長し、成長した集団内ではCompetitonが盛んになり、Competitionが盛んだと集団が衰退し、衰退する集団からは多くのエージェントが流出し、流出したエージェントは新たな集団の構成員になる」という一連の流れが再現されることになると思われる。コミュニティが唯一無二になるような条件では停滞が見られ、新しいコミュニティができては消えていく条件では停滞する集団と躍進する集団がある、という状態。

・各種パラメータを変化させ、条件と適応的な戦略の対応関係を見ていくことができるように、改善する。以下のような条件でシミュレーションできるようにしたい。

