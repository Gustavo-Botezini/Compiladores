# Analisador Léxico - Compiladores

Este projeto implementa um **Analisador Léxico** (Lexical Analyzer) utilizando um **Autômato de Pilha (PDA - Pushdown Automaton)** para reconhecer e processar tokens de uma linguagem específica.

## 📋 Descrição

O analisador léxico é responsável por:
- Reconhecer padrões de tokens em uma entrada de texto
- Processar palavras linha por linha (separadas por '#')
- Gerar uma tabela de símbolos com informações sobre cada token
- Rastrear o caminho de estados percorrido durante o processamento

## 🏗️ Estrutura do Projeto

```
Compiladores/
├── main.py          # Arquivo principal com exemplos de teste
├── pda.py           # Implementação do Autômato de Pilha
├── delta.py         # Função de transição (Delta)
├── constants.py     # Constantes do projeto (EPSILON)
└── README.md        # Este arquivo
```

## 🔧 Componentes Principais

### 1. Autômato de Pilha (AP)
- **Estados (Q)**: 36 estados definidos no formato 'letra,letra,Z'
- **Alfabeto de Entrada (Σ)**: Caracteres ['K', 'O', 'E', 'L', 'H', 'N', 'J', 'U', 'F', 'S', 'I', 'M', 'D', 'R', 'T', 'A', '#', ε]
- **Alfabeto da Pilha (Γ)**: Mesmos caracteres do alfabeto de entrada
- **Estado Inicial**: 'S'
- **Estados Finais (F)**: 13 estados de aceitação

### 2. Função de Transição (Delta)
A função δ está definida no arquivo `delta.py` e contém todas as transições possíveis no formato:
```python
(estado_atual, símbolo_entrada, topo_pilha) -> (novo_estado, símbolo_empilhado)
```

## 🚀 Como Executar

1. **Pré-requisitos**:
   - Python 3.x instalado

2. **Executar o programa**:
   ```bash
   cd Compiladores
   python main.py
   ```

## 📝 Formato de Entrada

O analisador processa strings com o seguinte formato:
- Palavras separadas por espaços
- Linhas separadas por '#'
- Exemplo: `"KO KEL # LOS"`

### Exemplos de Teste

O arquivo `main.py` contém exemplos de teste:
```python
nova_sequencia_testes = [
    "KO KEL # LOS",
    "# FAH # HIM # JUN #",
    " FOD # FUS # HON # NUST AAN ANRK",
    "FUS ROH DAH"
]
```

## 📊 Saída do Programa

O analisador produz:

1. **FITA**: Lista com os caminhos completos percorridos
2. **Tabela de Símbolos (TS)**: Tuplas no formato `(linha, estado_final, palavra)`
3. **Estatísticas**: Número total de linhas e palavras processadas

### Exemplo de Saída:
```
==================================================
FITA (Caminhos Completos): ['S -> B1,B2,Z -> B1,Z', 'S -> B1,B2,Z -> C2,Z -> C8,Z', ...]

Tabela de Simbolos (TS):
  1. Linha 1: 'KO' -> B1,Z
  2. Linha 1: 'KEL' -> C8,Z
  ...

Total de linhas processadas: 2
Total de palavras processadas: 3
```

## ⚙️ Funcionamento

1. **Inicialização**: O autômato começa no estado 'S' para cada palavra
2. **Processamento**: Cada caractere da palavra é processado sequencialmente
3. **Verificação**: Se o estado final não estiver em F, a palavra é rejeitada (estado 'X')
4. **Registro**: Cada palavra gera uma entrada na FITA e na Tabela de Símbolos

## 🎯 Estados Finais

O autômato aceita palavras que terminam nos seguintes estados:
- E11,Z, D10,Z, E12,Z, D3,Z
- D5,Z, D9,Z, D4,Z, D6,Z
- D7,Z, D8,Z, D2,Z, B1,Z

## 📚 Conceitos Utilizados

- **Autômato de Pilha (PDA)**: Máquina de estados finitos com memória auxiliar (pilha)
- **Análise Léxica**: Primeira fase da compilação, responsável pelo reconhecimento de tokens
- **Tabela de Símbolos**: Estrutura de dados para armazenar informações sobre identificadores
- **Estados de Aceitação**: Estados que indicam reconhecimento bem-sucedido de um padrão

## 👨‍💻 Autor

Desenvolvido como projeto acadêmico para a disciplina de Compiladores.

## 📄 Licença

Este projeto é para fins educacionais.