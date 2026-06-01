# 🛡️ Detecção Inteligente de Spam via Redes LSTM

Trabalho prático desenvolvido para a disciplina de **Inteligência Artificial II** do curso de Engenharia da Computação no Centro Universitário Fundação Hermínio Ometto (FHO).

## 📋 Sobre o Projeto

Este projeto implementa um sistema de identificação de mensagens de SMS indesejadas (spam) utilizando redes neurais **Long Short-Term Memory (LSTM)**. O objetivo é substituir filtros estáticos baseados em regras ou palavras-chave por uma solução de inteligência artificial capaz de compreender o contexto sequencial das mensagens.

O foco central da arquitetura desenvolvida é a **mitigação de falsos positivos** (evitar que mensagens legítimas importantes, como alertas bancários, sejam bloqueadas). O modelo atinge alta acurácia e generalização utilizando o dataset público [UCI SMS Spam Collection](https://archive.ics.uci.edu/ml/datasets/SMS+Spam+Collection).

---

## 🧠 Arquitetura do Sistema e Modelagem

O sistema foi estruturado para processar a linguagem natural de forma sequencial, dividido em duas etapas principais:

### 1. Pipeline de Processamento de Linguagem Natural (NLP)
* **Tokenização:** O vocabulário foi limitado às 5.000 palavras mais frequentes do dataset para atuar como um filtro de ruídos e evitar o sobreajuste (*overfitting*).
* **Padding:** As mensagens foram normalizadas para um tamanho fixo de 80 vetores, garantindo homogeneidade dimensional na entrada da rede.

### 2. Topologia da Rede Neural
* **Embedding:** Mapeamento de palavras para um espaço vetorial denso de 64 dimensões, capturando a similaridade semântica entre os termos.
* **LSTM (Long Short-Term Memory):** Camada recorrente principal com 64 unidades de memória. Responsável por ler a sequência do texto e reter o contexto a longo prazo, essencial para capturar gírias e intenções maliciosas complexas.
* **Dense & Dropout:** Camadas totalmente conectadas ativadas por ReLU, combinadas com *Dropout* agressivo (30% a 50%) para desligar neurônios aleatoriamente e forçar a generalização do aprendizado.
* **Saída (Sigmoid):** Um neurônio final de classificação binária que entrega a probabilidade matemática exata (0 a 1) de a mensagem ser um spam.

### 3. Regra de Negócio e Threshold
Toda a arquitetura e os hiperparâmetros foram otimizados com foco em minimizar os **Falsos Positivos**. O objetivo crítico e funcional do projeto é garantir que mensagens legítimas (como tokens de autenticação) jamais sejam retidas indevidamente pelo filtro de spam, exigindo um alto nível de confiança da IA para realizar o bloqueio.

---

## ⚙️ Funcionalidades e Estrutura

O projeto foi estruturado para fornecer tanto uma avaliação estatística global quanto uma simulação prática em tempo real:

* **Visão Global (Métricas):** Geração de Matriz de Confusão e Histogramas de Distribuição de Probabilidades para avaliar o comportamento do modelo em todo o conjunto de testes.
* **Visão de Produção (Simulador):** Uma interface web interativa que simula a chegada de mensagens aleatórias do banco de testes e a separação feita pela IA em milissegundos.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Deep Learning:** TensorFlow e Keras
* **Análise de Dados e NLP:** Pandas, NumPy e Scikit-Learn
* **Visualização:** Matplotlib e Seaborn
* **Interface Gráfica (Front-end):** Gradio
* **Ambiente de Desenvolvimento:** Google Colab

---

## 🚀 Como Executar (Via Google Colab)

A forma mais rápida e segura de reproduzir os resultados é utilizando o Google Colab com aceleração de hardware:

1. Abra o arquivo `.ipynb` deste repositório no [Google Colab](https://colab.research.google.com/).
2. Vá em **Editar > Configurações do notebook** e certifique-se de que o "Acelerador de hardware" está definido como **GPU** (T4).
3. Execute as células sequencialmente:
   * **Instalação e Pré-processamento:** Instala as dependências (Gradio) e prepara o dataset da UCI.
   * **Treinamento:** Cria e treina a rede neural LSTM.
   * **Métricas:** Gera os gráficos analíticos estáticos para validação do desempenho estatístico.
   * **Simulador:** Inicia a interface do aplicativo Gradio para testes isolados e dinâmicos em tempo real.

---

## 👨‍💻 Autor

**Luiz Augusto Curtolo de Souza** (RA: 113363)  
Curso de Engenharia da Computação  
Centro Universitário Fundação Hermínio Ometto (FHO) - Araras, SP
