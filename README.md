# Desafio Técnico: Tratamento de Dados Financeiros e Assistente de IA 

Este repositório contém a resolução de um desafio técnico focado no tratamento, padronização e análise de dados financeiros, além da implementação de um protótipo de assistente de inteligência artificial.

## Introdução
O projeto apresenta uma solução completa para o processamento de grandes volumes de transações financeiras e utiliza o modelo Gemini 1.5 Flash para gerar insights estratégicos a partir dos dados tratados.

## Tratamento de Dados
Para a padronização e enriquecimento da base de dados, utilizei a biblioteca Pandas em ambiente Python (Google Colab). As principais ações realizadas foram:

* Limpeza de Identificadores (CPF): Utilização de Expressões Regulares (Regex) para remover caracteres não numéricos e aplicação de máscara padrão (`XXX.XXX.XXX-XX`). Registros ausentes foram preenchidos como "Não informado".
* Padronização de Valores: Conversão da coluna `Valor_Transacao` para formato numérico (float), tratando símbolos de moeda e separadores decimais.
* Tratamento de Câmbio: Conversão de transações em USD e EUR para BRL, utilizando taxas de câmbio fixadas para manter a consistência da análise.
* Higienização de Categorias: Padronização de strings para evitar duplicidade por erro de digitação (ex: "pix", "Pix" e "PIX" consolidados em um único grupo).
* Cálculo de Novas Métricas: Criação da coluna `Valor_Final` somando o valor da transação à taxa de serviço.

## Assistente de IA
Foi desenvolvido um script Python utilizando a biblioteca oficial `google-genai` para conectar a base de dados tratada ao modelo Gemini 1.5 Flash.

* Lógica de Contexto: O código não envia a base bruta (1.000 linhas), mas sim um Resumo Analítico calculado via Pandas (total movimentado, taxas de recusa por banco, ticket médio, etc.). Isso otimiza o uso de tokens e aumenta a precisão da IA.
* Interface: Implementação de um loop `input()` que permite interações em linguagem natural diretamente no terminal do Colab.

## Arquivos no Repositório
* `Desafio_Citi.ipynb`: Notebook com todo o código Python desenvolvido.
* `Base_Tratada_Final.csv`: Base de dados final após todo o processo de limpeza.
* `Base_Financeira_PTC_26.csv`: Base de dados original (bruta).
