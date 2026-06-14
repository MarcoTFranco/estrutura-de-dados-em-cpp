# Estruturas de Dados em C++

Implementações educacionais das principais estruturas de dados em C++, com foco em clareza e funcionamento prático. Cada estrutura possui uma interface interativa via terminal para testes.

## Estruturas Implementadas

| Estrutura | Diretório | Resolução de Colisão / Armazenamento |
|---|---|---|
| Árvore Binária de Busca | `Arvore/` | — |
| Fila Encadeada | `Fila Encadeada/` | Lista ligada dinâmica |
| Fila Estática | `Fila Estatica/` | Vetor circular (tamanho fixo) |
| Tabela Hash com Encadeamento | `Tabela Hash/` | Encadeamento com listas ligadas |
| Tabela Hash com Endereçamento Aberto | `Tabela Hash Colisao/` | Sondagem linear com marcação tombstone |

---

## Detalhes das Implementações

### Árvore Binária de Busca (ABB)
**Arquivo:** `Arvore/arvore.cpp`

Implementação clássica de ABB com nós contendo um valor inteiro.

**Operações disponíveis:**
- `insere(int)` — insere um valor mantendo a propriedade da ABB
- `remover(int)` — remove um nó (trata os 3 casos: folha, 1 filho, 2 filhos)
- `busca(int)` — retorna ponteiro para o nó com o valor buscado
- `minimo()` / `maximo()` — encontra o menor/maior valor
- `percorreEmOrdem()` — percurso esquerda-raiz-direita (produz sequência ordenada)
- `percorrePreOrdem()` — percurso raiz-esquerda-direita

**Interface interativa:**
```
i → inserir | r → remover | o → em-ordem | p → pré-ordem | f → encerrar
```

---

### Fila Encadeada
**Arquivo:** `Fila Encadeada/fila.cpp`

Fila implementada com lista ligada, sem limite de capacidade.

**Operações disponíveis:**
- `enfileira(int)` — adiciona ao final
- `desenfileira()` — remove do início
- `topo()` — consulta o elemento da frente sem remover
- `tamanho()` — retorna o número de elementos
- `vazia()` — verifica se a fila está vazia
- `limpaFila()` — remove todos os elementos

---

### Fila Estática
**Arquivo:** `Fila Estatica/fila.cpp`

Fila implementada com vetor circular de capacidade fixa (`CAPACIDADE_FILA = 6`).

**Operações disponíveis:**
- `enfileirar(int)` — adiciona ao final
- `desenfileirar()` — remove do início
- `vazia()` / `cheia()` — verifica o estado da fila
- `informacoes()` — exibe o elemento da frente
- `limparTudo()` — reinicia a fila

> Utiliza aritmética modular para o controle circular do vetor, sendo mais eficiente em memória que a versão encadeada.

---

### Tabela Hash com Encadeamento
**Arquivo:** `Tabela Hash/hash.cpp`

Tabela hash que armazena pares `(chave: string, tipo: char, valor: int)`. Colisões são resolvidas por **encadeamento separado** com listas ligadas em cada posição.

**Função hash:** `pos = (7 * pos + char) % capacidade`

**Operações disponíveis:**
- `insere(string, char, int)` — insere um registro (previne chaves duplicadas)
- `remove(string)` — remove um registro pela chave
- `valor(string, ...)` — consulta o valor associado a uma chave
- `imprime()` — exibe a estrutura completa da tabela

**Capacidade padrão:** 100 posições

---

### Tabela Hash com Endereçamento Aberto
**Arquivo:** `Tabela Hash Colisao/hash.cpp`

Tabela hash que armazena registros de processos `(assunto, nomeInteressado, tipo, numeroProcesso)`. Colisões são resolvidas por **sondagem linear**.

**Função hash:** `pos = (13 * pos + char) % capacidade`

**Operações disponíveis:**
- `inserir(string, string, char, int)` — insere um registro
- `remover(string)` — remove com marcação `REMOVIDO` (tombstone)
- `consultar(string)` — busca um registro pela chave
- `imprimir()` — exibe todas as posições da tabela

**Capacidade padrão:** 50 posições | **Sentinelas:** `INVALIDO` (vazio) e `REMOVIDO` (excluído)

---

## Como Compilar e Executar

Cada estrutura é um arquivo `.cpp` independente. Para compilar e executar, utilize `g++`:

```bash
# Exemplo: compilar e executar a Árvore Binária de Busca
g++ "Arvore/arvore.cpp" -o arvore
./arvore

# Exemplo: compilar e executar a Fila Encadeada
g++ "Fila Encadeada/fila.cpp" -o fila_encadeada
./fila_encadeada
```

**Requisitos:** compilador C++ com suporte a C++11 ou superior (g++, clang++).

---

## Estrutura do Repositório

```
estrutura-de-dados-em-cpp/
├── Arvore/
│   └── arvore.cpp
├── Fila Encadeada/
│   └── fila.cpp
├── Fila Estatica/
│   └── fila.cpp
├── Tabela Hash/
│   └── hash.cpp
└── Tabela Hash Colisao/
    └── hash.cpp
```

---

## Autor

**Marco Túlio** — Implementações desenvolvidas em 2023 como estudo de estruturas de dados fundamentais em C++.
