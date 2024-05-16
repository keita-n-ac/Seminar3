```python
import pandas as pd
from IPython.display import display
```


```python
# データを小数点以下4桁で固定
pd.options.display.float_format = '{:.4f}'.format
# データを省略せずに表示
pd.set_option('display.max_columns', None)
```


```python
# 2重リストの場合（復習）
data1 = [
    ['田中優花', '女', 140, 40.5],
    ['佐藤和也', '男', 175, 70.2],
    ['鈴木一郎', '男', 170, 65.0],
    ['高橋美香', '女', 158, 55.6],    
]

print(data1)
```

    [['田中優花', '女', 140, 40.5], ['佐藤和也', '男', 175, 70.2], ['鈴木一郎', '男', 170, 65.0], ['高橋美香', '女', 158, 55.6]]



```python
# 2重リストとカラムを使ってデータフレームを定義
df1 = pd.DataFrame(data1, columns=['氏名', '性別', '身長', '体重'])

print(type(df1))
print()

display(df1)
```

    <class 'pandas.core.frame.DataFrame'>
    



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データフレームの構成物を表示する
print('列インデックス', list(df1.columns))
print()

print('行インデックス', list(df1.index))
print()

# データの値
print('データの中身')
print(df1.values)
```

    列インデックス ['氏名', '性別', '身長', '体重']
    
    行インデックス [0, 1, 2, 3]
    
    データの中身
    [['田中優花' '女' 140 40.5]
     ['佐藤和也' '男' 175 70.2]
     ['鈴木一郎' '男' 170 65.0]
     ['高橋美香' '女' 158 55.6]]


### CSVファイル
- CSVとはコンマ区切りのファイルのこと
    - 1行目はカラムがコンマ区切り
    - 2行目以降は，1行ごとにコンマ区切りにデータが格納されている．
- 例: https://github.com/keita-n-ac/Seminar3/blob/main/df-sample.csv?plain=1
```
氏名,性別,身長,体重
田中優花,女,140,40.5
佐藤和也,男,175,70.2
鈴木一郎,男,170,65.0
高橋美香,女,158,55.6
```
- 1行目がカラム
- 2行目以降がデータ


```python
# このプログラムは，df-sample.csvをgoogle colabにないと利用できない
# csvファイルからデータフレームを作成する
csv_fn = 'df-sample.csv'
df2 = pd.read_csv(csv_fn) # CSVを読み込む
display(df2)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# インターネットにあるcsvファイルからデータフレームを作成する
csv_url = 'https://raw.githubusercontent.com/keita-n-ac/Seminar3/main/df-sample.csv'
df3 = pd.read_csv(csv_url) # CSVを読み込む
display(df3)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# インターネットにあるexcelファイルからデータフレームを作成する
excel_url = 'https://raw.githubusercontent.com/keita-n-ac/Seminar3/main/df-sample.xlsx'
df4 = pd.read_excel(excel_url) # excelファイルを読み込む
display(df4)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データシリーズ形式の場合: リストと名前を指定する
s1 = pd.Series(
    [140, 175, 170, 158],
    name='身長')

print(type(s1))
print(s1)
```

    <class 'pandas.core.series.Series'>
    0    140
    1    175
    2    170
    3    158
    Name: 身長, dtype: int64



```python
# データフレームの特定列からデータシリーズにする
s2 = df4['身長']

print(type(s2))
print(s2)
```

    <class 'pandas.core.series.Series'>
    0    140
    1    175
    2    170
    3    158
    Name: 身長, dtype: int64



```python
# データフレームの特定行からデータシリーズにする
s3 = df4.loc[1]

print(type(s3))
print(s3)
```

    <class 'pandas.core.series.Series'>
    氏名      佐藤和也
    性別         男
    身長       175
    体重   70.2000
    Name: 1, dtype: object



```python
# データフレームの各項目のデータ形式を確認
print(df4.dtypes)

# int64は整数
# float64は小数
# objectは文字列
```

    氏名     object
    性別     object
    身長      int64
    体重    float64
    dtype: object



```python
# 列の絞り込み
# 抽出したいカラムのリストを用意する
cols = ['氏名', '性別']

df5 = df4[cols]
display(df5)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
    </tr>
  </tbody>
</table>
</div>



```python
# 行の絞り込み
# headメソッドを使うことで，先頭から指定した行数を抜き出す
display(df4.head(3))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データフレームの中から，条件を満たす行を抽出する
# 「性別が男」のカラムの作成
index1 = (df4['性別'] == '男')
print(index1) # 該当している行をTrue，該当していない行をFalseを出力
```

    0    False
    1     True
    2     True
    3    False
    Name: 性別, dtype: bool



```python
# Trueの行（index1）で行を抜き出す
index1 = (df4['性別'] == '男')
df6 = df4[index1]
display(df6)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# 1行で抜き出す場合
df7 = df4[df4['性別'] == '男']
display(df7)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データフレームのコピー
# copyメソッドを使用する
df8 = df4.copy()
display(df8)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データフレームの削除
# dropで削除する，axis=0は行，axis=1は列を示す
df8 = df8.drop('氏名', axis=1) # 列の「氏名」を削除する
display(df8)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データフレームに追加
bmi = df4['体重'] / (df4['身長'] / 100) ** 2 # BMIを計算
print(bmi)
```

    0   20.6633
    1   22.9224
    2   22.4913
    3   22.2721
    dtype: float64



```python
# bmi（列）を追加
df9 = df4.copy()
df9['BMI'] = bmi # カラムBMIでbmiを追加する
display(df9)
# この方法だと最後の列で追加される
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
      <th>BMI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
      <td>20.6633</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
      <td>22.9224</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
      <td>22.4913</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
      <td>22.2721</td>
    </tr>
  </tbody>
</table>
</div>



```python
# bmi（列）をinsertで追加
df10 = df4.copy()
df10.insert(2, 'BMI', bmi)  # 2列目をカラムBMIでbmiを追加する
display(df10)
# insertを使うことで指定した列に追加される
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>BMI</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>20.6633</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>22.9224</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>22.4913</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>22.2721</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
  </tbody>
</table>
</div>



```python
# データシリーズをデータフレームに結合
s5 = pd.Series([10, 25, 45, 34], name='年齢')
print(s5)
```

    0    10
    1    25
    2    45
    3    34
    Name: 年齢, dtype: int64



```python
# concatメソッドで結合できる
df11 = pd.concat([df10, s5], axis=1)
display(df11)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>BMI</th>
      <th>身長</th>
      <th>体重</th>
      <th>年齢</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>20.6633</td>
      <td>140</td>
      <td>40.5000</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>22.9224</td>
      <td>175</td>
      <td>70.2000</td>
      <td>25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>22.4913</td>
      <td>170</td>
      <td>65.0000</td>
      <td>45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>22.2721</td>
      <td>158</td>
      <td>55.6000</td>
      <td>34</td>
    </tr>
  </tbody>
</table>
</div>



```python
# 行の追加（新データの追加）df11 = pd.concat([df10, s5], axis=1)
# 辞書データとconcatで新データを追加できる
new_dict = {'氏名': '山田太郎', '性別': '男', '身長': 165, '体重': 64.2}
new_data = pd.DataFrame([new_dict])
df12 = pd.concat([df4, new_data], ignore_index=True)
# ignore_index=True とすることで，追加した際のインデックスを自動的に修正できる
display(df12)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>氏名</th>
      <th>性別</th>
      <th>身長</th>
      <th>体重</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>田中優花</td>
      <td>女</td>
      <td>140</td>
      <td>40.5000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>佐藤和也</td>
      <td>男</td>
      <td>175</td>
      <td>70.2000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>鈴木一郎</td>
      <td>男</td>
      <td>170</td>
      <td>65.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>高橋美香</td>
      <td>女</td>
      <td>158</td>
      <td>55.6000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>山田太郎</td>
      <td>男</td>
      <td>165</td>
      <td>64.2000</td>
    </tr>
  </tbody>
</table>
</div>


### 練習問題
1. ```data1```，```data2```，```columns```が以下のように定義されているとき，```data1```に対するデータフレーム```d1```，```data2```に対するデータフレーム```d2```を定義してください．```d1```と```d2```の中身を表示すること．
    - ```d1```と```d2```のカラムは```columns```を使用すること．
```python
data1 = [
    ['藤井聡太', '八冠', 307, 21],
    ['羽生善治', '九段', 175, 53],
]

data2 = [
    ['伊藤匠', '七段', 324, 21],
    ['藤本渚', '五段', 333, 18],
]

columns = ['名前', '段位', '棋士番号', '年齢']
```

2. ```df1```と```df2```を連結して，新しいデータフレーム```df3```を作成し，中身を表示すること．
