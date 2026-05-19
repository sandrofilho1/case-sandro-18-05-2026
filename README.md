Problemas encontrados e como tratar
Problema (célula 9) — a coluna gt tem um valor "null" como se fosse uma atividade:
Não são nulos de verdade (por isso a célula 7 não detectou)
É a string "null" escrita como texto — ou seja, registros onde a atividade não foi identificada
No Phone Accelerometer são 1.783.200 registros
No Watch Accelerometer são 520.357 registros
Como tratar: substituir a string "null" por nulo real com o código abaixo
—---------------------------------------------------------------------------------------

from pyspark.sql.functions import when, col

df_phone_acc_limpo = df_phone_acc.withColumn(
    "gt",
    when(col("gt") == "null", None).otherwise(col("gt"))
)

—---------------------------------------------------------------------------------------
O que estava OK:
O schema está consistente, todas as colunas com os tipos certos. (Célula 6)
Não foram encontrados valores nulos (Célula 7)
Não foram encontrados duplicatas (Célula 8)
