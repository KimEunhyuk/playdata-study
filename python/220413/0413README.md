# 0413 Review ๐

### .iter()
iterrable? ๋ฐ๋ณต๊ฐ๋ฅํ๋ค  
for๋ฌธ์ฒ๋ผ ์๋ํ๋ฉฐ ๋ฐ๋ณต๋๋ ๋ฐ์ดํฐ๋ฅผ ์ฒ๋ฆฌํ๋ ๊ธฐ๋ฅ์ ํ๋ ํจ์

- ์ฌ์ฉ๋ฒ
```
import xml.etree.ElementTree as ET

root = ET.fromstring(r.text)
items = root.iter(tag='item')
```
๋์  items[0] ์ฒ๋ผ ์ธ๋ฑ์ฑ์ผ๋ก ํธ์ถ์ด ๋ถ๊ฐ๋ฅํ๋ค -> for๋ฌธ์ผ๋ก๋ง ๊ฐ๋ฅ

### .set ์งํฉ
```
set([1,2,3,3,3,3])
{1, 2, 3}
```
์ด๋ ๊ฒ ์ค๋ณต๊ฐ ์ ๊ฑฐ ๊ฐ๋ฅ

- ์ฐจ์งํฉ
์ฐจ์ด๋ฅผ ์๊ณ ์ถ์ผ๋ ์ฐจ์งํฉ
set(set_b) - set(set_a)

.astype(int) 
ํ๋ณํ ํด์ฃผ๋ ํจ์

.diff(-1)
ํ์ฌ์์น์์ ์ด๋์์น(-1)๋ฅผ ๋บ๊ฑด์ง
-1์ด๋๊น ํ์ฌ์ ๋ฐ๋ก ๋ค์ ๊ฑธ ๋นผ๋ ๊ฒ

.shift(1)
row๋ฅผ ํ ์ด ๋ฐ์ผ๋ก ๋ด๋ฆฌ๋ ํจ์


### Python array[::] ์ฉ๋ฒ
arr[a:b:c]์ ํํ๋ก ๋์ด์๋๋ฐ, index a ๋ถํฐ b๊น์ง c์ ๊ฐ๊ฒฉ์ผ๋ก ๋ฐฐ์ด์ด ๋ง๋ค์ด ์ง๋ ๊ฒ
c๊ฐ none์ด๋ฉด ํ์นธ ๊ฐ๊ฒฉ์ผ๋ก 

```
tmp[::-1]
```
์ ์ฒด ๋ฐฐ์ด์ -1์ ๊ฐ๊ฒฉ(์ญ์)์ผ๋ก ๋ฐฐ์ด์ ๋ง๋  ๊ฒ

### .concat
index๋ฅผ ๊ธฐ์ค์ผ๋ก column์ด ์์ผ๋ก ๋ถ๊ฒ๋๋ค (column๋ง ์ด๋ํ๊ฒ ๋จ)


### ORM
- ์์
```
import sqlalchemy
pip install mysqlclient
engine = sqlalchemy.create_engine("mysql+mysqldb://root:" + "1234" + "@127.0.0.1/stock", encoding='utf-8')
conn = engine.connect()
covid2.to_sql(name='covid2', con = engine, if_exists = 'replace', index=False)
```

- if_exists
'replace' ๋ ๊ฐ์ ์ด๋ฆ์ ํ์ด๋ธ์ด ์์ผ๋ฉด ์ด ๊ฒฐ๊ณผ๋ก ๋์ฒด๋จ
โappendโ๋ ๊ฐ์ ์ด๋ฆ์ ํ์ด๋ธ์ด ์์ผ๋ฉด ๋ฐ์ ์ถ๊ฐ๋จ
โfailโ๋ error์ฒ๋ฆฌํจ

pd.read_sql_query("select * from covid", conn)
์ฟผ๋ฆฌ๋ฌธ์ผ๋ก ํ์ด๋ธ์ ๋ด๊ธด ๋ชจ๋  ๋ฐ์ดํฐ ์ถ๋ ฅ

```
tmp3.to_sql(name='tmp', con = engine, if_exists = 'append', index=False, 
           dtype = {
               'createDt' : sqlalchemy.types.VARCHAR(100),
               'deathCnt' : sqlalchemy.types.INTEGER(),
               'decideCnt' : sqlalchemy.types.INTEGER()
           })
```

### ์ค๋ณต๊ฐ
.duplicates -> dropํ  ๋
.duplicated -> ์ค๋ณต๊ฐ์ ํ์ธํ  ๋

### column 
- column ์ด๋ฆ ๋ฐ๊พธ๋ ๋ฒ
tmp.columns = ['์ฃผ์', '์ด์์๊ฐ', '๋งค์ฅ์ด๋ฆ']   
column์ ์ํ๋ ์ด๋ฆ์ ๋ฆฌ์คํธ๋ฅผ ๋์ํด์ ์์ฑํ๋ฉด ๋๋ค
๋จ, column์ ๊ฐ์์ list์ ๋ด์ ์์์ ๊ฐ์๊ฐ ๊ฐ์์ผํจ

- column ์์ ๋ณ๊ฒฝ
ediya_df = ediya_df[['๋งค์ฅ์ด๋ฆ', '์ฃผ์', '์ด์์๊ฐ']]
data frame์์ []์ ํ์์ผ๋ก ์ํ๋ ์์๋๋ก ๋ฆฌ์คํธ๋ฅผ ์์ฑํ๋ฉด ๋๋ค

### ์ํ๋ column์ ๊ธฐ์ค์ผ๋ก ์ ๋ ฌํ๊ธฐ
ediya_df.sort_values(by=['๋ง๊ฐ'])


