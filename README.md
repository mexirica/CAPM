# CAPM
Código para descobrir custo de capital

#Beta

import numpy as np
import pandas as pd
from pandas_datareader import data as wb

acoes = ['JHSF3.SA', '^BVSP']
data = pd.DataFrame()
for t in acoes:
data[t] = wb.DataReader(t, 'yahoo', '2015-1-1')['Adj Close']

retorno = np.log( data / data.shift(1) )
cov = retorno.cov() * 250
cov_mercado = cov.iloc[0,1]
var_mercado = retorno['^BVSP'].var() * 250

beta = cov_mercado / var_mercado
beta

#CAPM

capm=0.025*beta**0.05
print(str(round(capm,3)*100)+ ' %')

Image

Properties
Assignees

mexirica
mexirica
Status

Done
Convert to issue
Archive
Delete from project
PYTHON
View 1

New view
Fronteira Eficiente
Long Short
CAPM
Monte Carlo
Portfolio
