リスト
========================================

リストとは
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- 0 個以上の要素をまとめて管理することができる型

- 真偽値、None、数値、文字列、配列、辞書、集合などオブジェクトであれば、どのようで値でも要素に追加できる。
  

リストの作り方
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- [] で囲む

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    >>> l2 = ["hoge", "foo", "baa"]
    ["hoge", "foo", "baa"]


各要素へのアクセス
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    >>> l1[0]
    1
    >>> l1[1]
    2
    >>> l2 = ["hoge", "foo", "baa"]
    ["hoge", "foo", "baa"]
    >>> l2[0]
    "hoge"
    >>> l2[1]
    "foo"
    

リストのスライス
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- 配列から、部分的に配列を取り出すことができる。

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    >>> l1[:4] # 終端指定の -1 要素目まで取得する
    [1, 2, 3, 4]
    >>> l1[5:] # 始端指定から最後の要素まで取得する
    [6, 7, 8, 9, 0]
    >>> l1[1:4] # 始端指定要素から終端指定の -1 要素目まで取得する
    [2, 3, 4]
    

メソッド
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- 要素の追加

.. code-block:: python

    >>> l = [1, 2, 3]
    >>> l.append(4)
    >>> print(l)
    [1, 2, 3, 4]

    >>> l = ["hoge"]
    >>> l.append("foo")
    >>> l.append("baa")
    >>> print(l)
    ['hoge', 'foo', 'baa']

    >>> l = [1, 2, 3]
    >>> l.append([4, 5, 6])
    >>> print(l)
    [1, 2, 3, [4, 5, 6]]

    >>> l = [1, 2, 3]
    >>> l.append(["hoge": 100, "foo": 200, "baa": 300])
    >>> print(l)
    [1, 2, 3, {'baa': 300, 'foo': 200, 'hoge': 100}]


- 要素をクリアする

.. code-block:: python

    >>> l = [1, 2, 3]
    >>> l.clear()
    >>> print(l)
    []


- 浅いコピーを作る

  - コピー元に要素に含む配列/辞書については、参照状態を保持する
  
.. code-block:: python

    >>> l1 = [1, 2, 3, [4, 5, 6]]
    >>> l2 = l1.copy()
    >>> print(l1)
    [1, 2, 3, [4, 5, 6]]
    >>> print(l2)
    [1, 2, 3, [4, 5, 6]]
    >>> l1[3].append(7)
    >>> print(l1)
    [1, 2, 3, [4, 5, 6, 7]]
    >>> print(l2)
    [1, 2, 3, [4, 5, 6, 7]]


- 深いコピーを作る

  - コピー元に要素に含む配列/辞書について、参照状態を保持しない
  
.. code-block:: python

    >>> import copy
    >>> l1 = [1, 2, 3, [4, 5, 6]]
    >>> l2 = copy.deepcopy(l1)
    >>> print(l1)
    [1, 2, 3, [4, 5, 6]]
    >>> print(l2)
    [1, 2, 3, [4, 5, 6]]
    >>> l1[3].append(7)
    >>> print(l1)
    [1, 2, 3, [4, 5, 6, 7]]
    >>> print(l2)
    [1, 2, 3, [4, 5, 6]]


- 指定した値が、配列の中にいくつ含んでいるか

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1]
    >>> l1.count()
    2


- 配列を結合する

.. code-block:: python
		
    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.extend([100, 200, 300, 400, 500])
    >>> print(l1)
    [1, 2, 3, 4, 5, 100, 200, 300, 400, 500]

    >>> [1, 2, 3, 4, 5] + [100, 200, 300, 400, 500]
    [1, 2, 3, 4, 5, 100, 200, 300, 400, 500]


- 配列の中身を検索する該当する値のインデックスを返す

.. code-block:: python
		
    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.index(3)
    2

    
- 指定したインデックス部分にデータを挿入する

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.insert(0, [100, 200, 300])
    >>> print(l1)
    [[100, 200, 300], 1, 2, 3, 4, 5]

    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.insert(100, [100, 200, 300])
    [1, 2, 3, 4, 5, [100, 200, 300]]
    

- 配列から値を取り出す

.. code-block:: python
		
    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.pop()
    >>> print(l1)
    [1, 2, 3, 4] # 終端から値を取り出す

    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.pop(0)
    >>> print(l1)
    [2, 3, 4] # 始端から値を取り出す
    

- 配列から値を削除する

 - メソッドに指定した値があれば、はじめに見つかった値を削除する
  
.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5, 1]
    >>> l1.remove(1)
    >>> print(l1)
    [2, 3, 4, 5, 1]
    >>> l1.remove(1)
    >>> print(l1)
    [2, 3, 4, 5]


- 要素の並びを反転させる

.. code-block:: python
		
    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1.reverse()
    >>> print(l1)
    [5, 4, 3, 2, 1]


- 要素をソートする

.. code-block:: python
		
    >>> l1 = [1, 3, 2, 5, 8, 4]
    >>> l1.sort()
    >>> print(l1)
    [1, 2, 3, 4, 5, 8]

    >>> l1 = [1, 3, 2, 5, 8, 4]
    >>> l1.sort(reverse=True)
    [8, 5, 4, 3, 2, 1]


例外
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

配列操作に失敗すると、例外を送出します。

- 存在しないインデックスを指定したとき

.. code-block:: python

    >>> l1 = [1, 2, 3, 4, 5]
    >>> l1[100]
    ---------------------------------------------------------------------------
    IndexError                                Traceback (most recent call last)
    <ipython-input-482-fab35c02c4db> in <module>()
    ----> 1 l1[100]

    IndexError: list index out of range

    >>> l1[100] = 100
    ---------------------------------------------------------------------------
    IndexError                                Traceback (most recent call last)
    <ipython-input-483-0bacec6b6ded> in <module>()
     ----> 1 l1[100] = 100

    IndexError: list assignment index out of range

