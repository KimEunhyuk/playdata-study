# 0407 Review ๐

<br>

## 1. enumerate  
```
for ~~~ in **enumerate**():
```
- data์ ์คํ์์๋ฅผ indexํ ํด์ค๋ค
- for ๋ฌธ์ ๋๋ฆด๋ ์ด๋๊น์ง ๋์๋์ง ํ์ธ๊ฐ๋ฅ
- ๋ฐ์ดํฐ์ ์งํ์์๋ฅผ ์๋ ค์ค


## 2. unpacking
```
In :
for x in ~~~:
 a, b = x.text.split(":")
        player_dict[a] = b.strip()
a, b

out :
{'์ ์๋ช': '๊ฐ์ ํ'}
```

## 3. sorted(~~.items())
sorted(tmp)๋ฅผ ํ๋๋ value๊ฐ์ ๋์ค์ง ์๊ณ  key๊ฐ๋ง ๋์๋๋ฐ 
tmp.items()๋ฅผ ํ๋๋ value๊ฐ๊น์ง ์ ์ถ๋ ฅ๋์๋ค.
```
In:
sorted(tmp.items(), key=lambda x : x[1], reverse=True)

out:
[('ํ๊ธฐ์', 39.24646781789639)]
```
