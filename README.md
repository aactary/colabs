```python
import pandas as pd
from numpy import random
import numpy as np
```


```python
df = pd.read_csv("https://github.com/futpythontrader/YouTube/blob/main/Base_de_Dados/futpythontraderpunter.csv?raw=true")
```


```python
#BRAZIL - SERIE A
league = df.loc[(df['League'] == 'BRAZIL - SERIE A') & (df['Season'] == '2023')]
# league = df.loc[(df['League'] == 'BRAZIL - SERIE A')]
#BRAZIL - SERIE B
# league = df.loc[(df['League'] == 'BRAZIL - SERIE B') & (df['Season'] == '2023')]
#ITALY - SERIE A
# league = df.loc[(df['League'] == 'ITALY - SERIE A') & (df['Season'] == '2022/2023')]
#SPAIN - LALIGA
# league = df.loc[(df['League'] == 'SPAIN - LALIGA') & (df['Season'] == '2022/2023')]
#ENGLAND - PREMIER LEAGUE
# league = df.loc[(df['League'] == 'ENGLAND - PREMIER LEAGUE') & (df['Season'] == '2022/2023')]
#FRANCE - LIGUE 1
# league = df.loc[(df['League'] == 'FRANCE - LIGUE 1') & (df['Season'] == '2022/2023')]
#GERMANY - BUNDESLIGA
# league = df.loc[(df['League'] == 'GERMANY - BUNDESLIGA') & (df['Season'] == '2022/2023')]
```


```python
league.tail(15)
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
      <th>Unnamed: 0</th>
      <th>Date</th>
      <th>Time</th>
      <th>League</th>
      <th>Season</th>
      <th>Round</th>
      <th>Home</th>
      <th>Away</th>
      <th>HT_Goals_H</th>
      <th>HT_Goals_A</th>
      <th>...</th>
      <th>CS_2x1</th>
      <th>CS_2x2</th>
      <th>CS_2x3</th>
      <th>CS_3x0</th>
      <th>CS_3x1</th>
      <th>CS_3x2</th>
      <th>CS_3x3</th>
      <th>CS_4x4</th>
      <th>Goals_Minutes_Home</th>
      <th>Goals_Minutes_Away</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>121004</th>
      <td>121005</td>
      <td>2023-11-01</td>
      <td>20:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Flamengo RJ</td>
      <td>Santos</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>...</td>
      <td>8.5</td>
      <td>21.0</td>
      <td>51.0</td>
      <td>9.5</td>
      <td>13.0</td>
      <td>29.0</td>
      <td>67.0</td>
      <td>501.0</td>
      <td>[21]</td>
      <td>[33, 90]</td>
    </tr>
    <tr>
      <th>121011</th>
      <td>121012</td>
      <td>2023-11-01</td>
      <td>21:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Atletico-MG</td>
      <td>Fortaleza</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>...</td>
      <td>9.0</td>
      <td>19.0</td>
      <td>51.0</td>
      <td>13.0</td>
      <td>15.0</td>
      <td>34.0</td>
      <td>67.0</td>
      <td>501.0</td>
      <td>[16, 56, 61]</td>
      <td>[44]</td>
    </tr>
    <tr>
      <th>121012</th>
      <td>121013</td>
      <td>2023-11-01</td>
      <td>21:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Botafogo RJ</td>
      <td>Palmeiras</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>11.0</td>
      <td>17.0</td>
      <td>34.0</td>
      <td>29.0</td>
      <td>26.0</td>
      <td>41.0</td>
      <td>51.0</td>
      <td>351.0</td>
      <td>[21, 31, 36]</td>
      <td>[50, 84, 90, 90]</td>
    </tr>
    <tr>
      <th>121060</th>
      <td>121061</td>
      <td>2023-11-02</td>
      <td>17:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Cuiaba</td>
      <td>Vasco</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>11.0</td>
      <td>17.0</td>
      <td>41.0</td>
      <td>26.0</td>
      <td>26.0</td>
      <td>41.0</td>
      <td>67.0</td>
      <td>501.0</td>
      <td>[]</td>
      <td>[58, 90]</td>
    </tr>
    <tr>
      <th>121063</th>
      <td>121064</td>
      <td>2023-11-02</td>
      <td>18:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Goias</td>
      <td>Bragantino</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>...</td>
      <td>12.0</td>
      <td>15.0</td>
      <td>29.0</td>
      <td>34.0</td>
      <td>26.0</td>
      <td>34.0</td>
      <td>51.0</td>
      <td>251.0</td>
      <td>[]</td>
      <td>[45, 90]</td>
    </tr>
    <tr>
      <th>121065</th>
      <td>121066</td>
      <td>2023-11-02</td>
      <td>20:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 31</td>
      <td>Sao Paulo</td>
      <td>Cruzeiro</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>9.5</td>
      <td>21.0</td>
      <td>51.0</td>
      <td>15.0</td>
      <td>19.0</td>
      <td>41.0</td>
      <td>81.0</td>
      <td>501.0</td>
      <td>[84]</td>
      <td>[]</td>
    </tr>
    <tr>
      <th>121568</th>
      <td>121569</td>
      <td>2023-11-04</td>
      <td>19:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>America MG</td>
      <td>Atletico-MG</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>15.0</td>
      <td>15.0</td>
      <td>26.0</td>
      <td>41.0</td>
      <td>34.0</td>
      <td>41.0</td>
      <td>51.0</td>
      <td>251.0</td>
      <td>[66]</td>
      <td>[80]</td>
    </tr>
    <tr>
      <th>121569</th>
      <td>121570</td>
      <td>2023-11-04</td>
      <td>19:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Gremio</td>
      <td>Bahia</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>8.5</td>
      <td>15.0</td>
      <td>41.0</td>
      <td>13.0</td>
      <td>13.0</td>
      <td>26.0</td>
      <td>51.0</td>
      <td>251.0</td>
      <td>[70]</td>
      <td>[]</td>
    </tr>
    <tr>
      <th>121583</th>
      <td>121584</td>
      <td>2023-11-04</td>
      <td>21:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Palmeiras</td>
      <td>Athletico-PR</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>8.5</td>
      <td>21.0</td>
      <td>41.0</td>
      <td>13.0</td>
      <td>15.0</td>
      <td>29.0</td>
      <td>67.0</td>
      <td>451.0</td>
      <td>[7]</td>
      <td>[]</td>
    </tr>
    <tr>
      <th>121996</th>
      <td>121997</td>
      <td>2023-11-05</td>
      <td>16:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Bragantino</td>
      <td>Corinthians</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>8.5</td>
      <td>19.0</td>
      <td>41.0</td>
      <td>11.0</td>
      <td>13.0</td>
      <td>26.0</td>
      <td>67.0</td>
      <td>351.0</td>
      <td>[29]</td>
      <td>[]</td>
    </tr>
    <tr>
      <th>121997</th>
      <td>121998</td>
      <td>2023-11-05</td>
      <td>16:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Cruzeiro</td>
      <td>Internacional</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>...</td>
      <td>9.5</td>
      <td>19.0</td>
      <td>41.0</td>
      <td>19.0</td>
      <td>21.0</td>
      <td>41.0</td>
      <td>67.0</td>
      <td>501.0</td>
      <td>[90]</td>
      <td>[15, 53]</td>
    </tr>
    <tr>
      <th>121998</th>
      <td>121999</td>
      <td>2023-11-05</td>
      <td>16:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Fortaleza</td>
      <td>Flamengo RJ</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>...</td>
      <td>10.0</td>
      <td>15.0</td>
      <td>41.0</td>
      <td>23.0</td>
      <td>21.0</td>
      <td>34.0</td>
      <td>51.0</td>
      <td>351.0</td>
      <td>[]</td>
      <td>[45, 87]</td>
    </tr>
    <tr>
      <th>122027</th>
      <td>122028</td>
      <td>2023-11-05</td>
      <td>18:30</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Coritiba</td>
      <td>Goias</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>10.0</td>
      <td>15.0</td>
      <td>34.0</td>
      <td>26.0</td>
      <td>23.0</td>
      <td>34.0</td>
      <td>51.0</td>
      <td>301.0</td>
      <td>[]</td>
      <td>[70]</td>
    </tr>
    <tr>
      <th>122116</th>
      <td>122117</td>
      <td>2023-11-06</td>
      <td>19:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Vasco</td>
      <td>Botafogo RJ</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>9.5</td>
      <td>15.0</td>
      <td>41.0</td>
      <td>21.0</td>
      <td>21.0</td>
      <td>34.0</td>
      <td>51.0</td>
      <td>351.0</td>
      <td>[29]</td>
      <td>[]</td>
    </tr>
    <tr>
      <th>122124</th>
      <td>122125</td>
      <td>2023-11-06</td>
      <td>21:00</td>
      <td>BRAZIL - SERIE A</td>
      <td>2023</td>
      <td>ROUND 32</td>
      <td>Santos</td>
      <td>Cuiaba</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>...</td>
      <td>9.0</td>
      <td>21.0</td>
      <td>51.0</td>
      <td>13.0</td>
      <td>17.0</td>
      <td>34.0</td>
      <td>81.0</td>
      <td>501.0</td>
      <td>[]</td>
      <td>[]</td>
    </tr>
  </tbody>
</table>
<p>15 rows × 52 columns</p>
</div>




```python
import json

home = "Corinthians"
away = "Atletico-MG"
odd_over05 = 1.71

# Defina uma função para contar os valores menores que 45
def contar_menores_que_45(lista):
    lista = json.loads(lista)
    counter = 0
    if not lista:  # Verifica se a lista está vazia
        return counter  # Se estiver vazia, retorna 0
    for numero in lista:
        if int(numero) <= 45:
            counter = 1
#             counter += 1
    return counter
```


```python
home_ht_gols = league.loc[(league['Home'] == home)]
```


```python
home_ht_gols = home_ht_gols[['League','Season','Round','Home','Away','HT_Goals_H','HT_Goals_A','Goals_Minutes_Home','Goals_Minutes_Away']]
```


```python
home_ht_gols['Menores_Que_45'] = home_ht_gols['Goals_Minutes_Home'].apply(contar_menores_que_45)
```


```python
score_home = home_ht_gols['Menores_Que_45'].sum()
```


```python
away_ht_gols = league.loc[(league['Away'] == away)]
```


```python
away_ht_gols = away_ht_gols[['League','Season','Round','Home','Away','HT_Goals_H','HT_Goals_A','Goals_Minutes_Home','Goals_Minutes_Away']]
```


```python
away_ht_gols['Menores_Que_45'] = away_ht_gols['Goals_Minutes_Away'].apply(contar_menores_que_45)
```


```python
score_away = away_ht_gols['Menores_Que_45'].sum()
```


```python
total_jogos_home = len(home_ht_gols)
total_jogos_away = len(away_ht_gols)
prob_home = (1 - (score_home / total_jogos_home)) 
prob_away = (1 - (score_away / total_jogos_away)) 
prob_0x0 = prob_home * prob_away
prob_gols = round(((1 - prob_0x0) * 100),2)
odd_betfair = round((1/odd_over05),2)
```


```python
print(prob_home)
print(prob_away)
print(prob_0x0)
print(prob_gols)
```

    0.8125
    0.5
    0.40625
    59.38
    


```python
print(home + " x " + away)

print("Em "+ str(total_jogos_home) +" Jogos, " + home + " marcou gols em " + str(score_home) + " jogos no 1º tempo")
print("Em "+ str(total_jogos_away) +" Jogos, " + away + " marcou gols em " + str(score_away) + " jogos no 1º tempo")
print("A probabilidade de sair pelo menos 1 gol no 1º tempo: " + str(prob_gols) + " %")
print("A probabilidade de sair gol no mercado OVER05 na betfair é: " + str(odd_betfair) + " % ")

# if(score_home >= (total_jogos_home * 0.75)) and (score_away >= (total_jogos_away * 0.5)):

if(prob_gols >= 70):
    print("Vale a pena apostar neste jogo")
else:
    print("Não aposte em " + home + " x "+ away + " no mercado OVER05_HT")
```

    Corinthians x Atletico-MG
    Em 16 Jogos, Corinthians marcou gols em 3 jogos no 1º tempo
    Em 16 Jogos, Atletico-MG marcou gols em 8 jogos no 1º tempo
    A probabilidade de sair pelo menos 1 gol no 1º tempo: 59.38 %
    A probabilidade de sair gol no mercado OVER05 na betfair é: 0.58 % 
    Não aposte em Corinthians x Atletico-MG no mercado OVER05_HT
    


```python

```
