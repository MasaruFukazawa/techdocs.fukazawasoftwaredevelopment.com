エラー
===================================

エラー戦略
-----------------------------------

関数がエラーを返した場合、そのエラーを検査して適切に対応するのは呼び出しもとの責任とする

- エラーを伝播する。
	- 呼び出し関数のエラーは、呼び出しもとのエラーとなる

- リトライする
	- 再び試みる間に遅延を行う
	- 試みる回数と制限する
	- 費やす時間を制限する

- プログラムを停止する
	- 処理を進めるのが不可能な場合は、呼び出しもとがエラーを表示してプログラムを停止する
	- main関数に限り、OK
	- ライブラリでは、エラーを伝播させるべき

- 処理を制限させる
	- エラーを記録して、エラーが影響しない範囲で、制限付きの機能で処理を続ける

- エラーを無視する
	- エラーを無視して、処理の続きを行う。まれなパターン


パニック
-----------------------------------

- 実行時にエラーを検出すると発生
	- 境界外への配列アクセス
	- nilポインタによる参照
- 実行を停止し、ゴルーチン内でのすべての遅延関数の呼び出しが行われる
- エラーメッセージ
	- パニック値 (panic value)
	- パニック時に動作していた関数呼び出しのスタックを示すスタックトレース
- panic関数で発生させることも可能
	- プログララム内で、論理的に「起きるはずがない」ところに到達したときに置くと良い
	- 引数には、任意の値も与えることができる


.. code-block:: go

	panic("文字列")


リカバー
-----------------------------------

