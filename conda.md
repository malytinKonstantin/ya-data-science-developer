conda env create -f /Users/konstantinmalutin/Downloads/projects/education/ya-data-science-developer/da_practicum_env_m1.yml

conda activate practicum 

jupyter notebook 


# Установка toc2 в Jupyter Notebook
pip install jupyter notebook==6.4.0 --user 
conda install -c conda-forge jupyter_contrib_nbextensions 
jupyter contrib nbextension install --user 


jupyter notebook 


jupyter lab 


Как сохранить датасет из проекта и тренажера
Скачать по ссылке
Любой упомянутый на курсе датасет можно скачать, даже если на него не дана ссылка. Для этого подставьте его название в ссылку https://code.s3.yandex.net/datasets/ и перейдите по ней.

Примеры:
https://code.s3.yandex.net/datasets/data.csv
https://code.s3.yandex.net/datasets/yandex_music_project.csv

import pandas as pd
data = pd.read_csv('/datasets/название_датасета.расширение')
data.to_csv('название_датасета.расширение', index=False) 



 Скопированная ссылка будет иметь примерно вот такой вид: https://docs.google.com/spreadsheets/d/1K83j_yl9b52m4qg5VidHLxLUNTNUoEH39BqyGdMBSek/edit?usp=sharing
    Часть ссылки 1K83j_yl9b52m4qg5VidHLxLUNTNUoEH39BqyGdMBSek  – это идентификатор таблицы. Скопируйте его и используйте в следующих пунктах.
В Jupyter notebook вставьте код:
from io import BytesIO
import requests
spreadsheet_id = '<ИДЕНТИФИКАТОР_GOOGLE_SPREADSHEET>'
file_name = 'https://docs.google.com/spreadsheets/d/{}/export?format=csv'.format(spreadsheet_id)
r = requests.get(file_name)
df = pd.read_csv(BytesIO(r.content))
df 