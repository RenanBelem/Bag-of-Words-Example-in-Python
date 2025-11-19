## Matriz Termo-Documento usando Bag of Words (Python)

Este projeto em Python implementa a técnica **Bag of Words (BoW)** para gerar uma matriz termo-documento a partir de textos extraídos da internet sobre Processamento de Linguagem Natural (NLP).

### Objetivo

O principal objetivo é demonstrar a construção de uma **matriz termo-documento** onde:

1.  O **corpus** (vocabulário) é gerado a partir da união de palavras de todos os documentos.
2.  A matriz registra a **frequência** de cada palavra do vocabulário em cada documento de origem.

### Tecnologias e Bibliotecas Utilizadas

O script utiliza as seguintes bibliotecas Python:

  * **`requests`**: Para realizar as requisições HTTP e obter o HTML dos sites.
  * **`BeautifulSoup` (bs4)**: Para analisar o HTML e extrair o texto dos documentos.
  * **`spaCy`**: Uma biblioteca de NLP para tokenização e remoção de pontuação. O modelo **`en_core_web_sm`** (inglês) é carregado para processar o texto.

### Fluxo de Processamento de Dados

O script executa as seguintes etapas para construir a matriz termo-documento:

#### 1\. Extração de Documentos e Pré-Processamento

  * O script faz requisições para cinco URLs sobre NLP.
  * Para cada URL, ele usa `BeautifulSoup` para extrair o texto do **terceiro parágrafo** (`.find_all("p")[2]`). *Nota: Isso garante que cada documento de entrada seja um único segmento de texto extraído consistentemente.*
  * A função **`verifica(s)`** é aplicada a cada texto. Ela usa `spaCy` para tokenizar o texto e retorna uma lista de *lexemas* (palavras) após remover a pontuação (`if not x.is_punct`).

#### 2\. Construção do Corpus (Vocabulário)

  * Os *tokens* de todos os cinco documentos (`envio1` a `envio5`) são concatenados para formar uma lista única chamada **`dicionario`** (que representa o vocabulário ou o corpus).

#### 3\. Cálculo das Frequências (Técnica BoW)

  * A função **`frequencia(envio, tudo)`** é a implementação da técnica Bag of Words (BoW).
  * Para cada documento (`envio1` a `envio5`), esta função itera sobre o **corpus completo** (`tudo`/`dicionario`) e conta quantas vezes cada palavra do corpus aparece nesse documento específico.

#### 4\. Geração e Impressão da Matriz

  * O resultado final é armazenado na lista **`vetorD`**.
  * A primeira linha impressa mostra o **Vocabulário** (o `dicionario`) que serve como os cabeçalhos das colunas (os termos).
  * As linhas subsequentes (`Documento 1` a `Documento 5`) mostram os **vetores de frequência** calculados, representando a matriz termo-documento.

### Documentos de Origem

Os cinco documentos (D1 a D5) são formados a partir do terceiro parágrafo das seguintes URLs:

1.  `https://www.linguamatics.com/what-text-mining-text-analytics-and-natural-language-processing`
2.  `https://www.techtarget.com/searchenterpriseai/definition/natural-language-processing-NLP`
3.  `https://en.wikipedia.org/wiki/Natural_language_processing`
4.  `https://monkeylearn.com/blog/natural-language-processing-techniques/`
5.  `https://towardsdatascience.com/introduction-to-natural-language-processing-for-text-df845750fb63`

### Matriz de Saída (Formato)

A saída no console terá a seguinte estrutura:

```
Matriz Termo Documento:

           [Palavra1, Palavra2, Palavra3, Palavra4, ...]  <-- Vocabulário
Documento 1[Frequência de P1 em D1, Frequência de P2 em D1, ...]
Documento 2[Frequência de P1 em D2, Frequência de P2 em D2, ...]
...
```
