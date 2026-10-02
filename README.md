# Prevenção a fraudes: case FREEDOM

Avaliação do modelo de fraude que está em produção (champion) e treino de um novo modelo (LightGBM) para substituí-lo, com o ponto de corte escolhido pelo lucro.

## Onde está cada coisa

- `meli_assessment.ipynb`: o notebook do case, executado do início ao fim e com todas as saídas. É o arquivo a ser avaliado.
- `notebooks/rascunhos/`: os notebooks de trabalho (EDA, avaliação do modelo atual e novo modelo) que deram origem ao principal. Podem ter textos e números de versões anteriores.
- `pyproject.toml` e `uv.lock`: as dependências do projeto.

## Como reproduzir

É preciso ter Python 3.13 e o [uv](https://docs.astral.sh/uv/) instalados.

```bash
uv sync
```

Depois, abra `meli_assessment.ipynb` com o kernel do ambiente do projeto (`.venv`) e execute todas as células. Os dados são lidos da URL fornecida no case, então é preciso ter acesso à internet.

## Resultado principal

No período de teste (13/04 a 21/04), o LightGBM gerou 81,2 mil de lucro, contra 69,0 mil do modelo atual, e recusou menos transações (16,7% contra 18,8%). O ponto de corte que maximiza o lucro é recusar a transação quando a probabilidade de fraude for maior ou igual a 0,075.
