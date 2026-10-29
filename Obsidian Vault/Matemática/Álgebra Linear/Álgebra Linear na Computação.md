# Álgebra Linear na Computação

Onde cada conceito aparece de verdade. Boa nota para reler quando bater o "pra que serve isso?".

## Computação gráfica
- Cada transformação 2D/3D (escala, rotação, reflexão) é uma matriz — ver [[Transformações Lineares]]. Compor transformações é multiplicar matrizes.
- **Coordenadas homogêneas**: translação não é linear, mas vira linear se acrescentarmos uma coordenada extra. Em 2D, o ponto $(x,y)$ vira $(x,y,1)$ e
$$\begin{pmatrix}1&0&t_x\\0&1&t_y\\0&0&1\end{pmatrix}\begin{pmatrix}x\\y\\1\end{pmatrix}=\begin{pmatrix}x+t_x\\y+t_y\\1\end{pmatrix}$$
Assim girar, escalar **e** transladar viram um único produto de matrizes.
- O *pipeline* de uma GPU (modelo → mundo → câmera → tela) é uma cadeia de multiplicações de matrizes $4\times4$.

## Machine learning
- Dados são **matrizes**: cada linha uma amostra, cada coluna uma característica.
- Uma camada densa de rede neural é $\vec y=W\vec x+\vec b$ — uma transformação linear mais um deslocamento.
- **Regressão linear** = [[Produto Interno e Ortogonalidade#Mínimos quadrados|mínimos quadrados]].
- **PCA**: autovetores da matriz de covariância dão as direções de maior variância ([[Autovalores e Autovetores]]).
- **Embeddings** são vetores; a similaridade entre dois textos/itens costuma ser o **cosseno do ângulo** entre eles ([[Vetores no Espaço Euclidiano]]).

## Busca e redes
- **PageRank**: a importância de cada página é o autovetor dominante da matriz de links.
- **Grafos**: a matriz de adjacência $A$ conta caminhos — o elemento $(A^k)_{ij}$ é o número de caminhos de comprimento $k$ de $i$ a $j$.

Exemplo: grafo com arestas $1-2$ e $2-3$:
$$A=\begin{pmatrix}0&1&0\\1&0&1\\0&1&0\end{pmatrix},\quad A^2=\begin{pmatrix}1&0&1\\0&2&0\\1&0&1\end{pmatrix}$$
$(A^2)_{22}=2$: dois caminhos de tamanho 2 de $2$ para $2$ ($2\to1\to2$ e $2\to3\to2$); $(A^2)_{13}=1$: o caminho $1\to2\to3$.

## Compressão
A **SVD** (decomposição em valores singulares), parente próxima da diagonalização, permite aproximar uma imagem por poucos componentes: guardar só os maiores valores singulares dá uma imagem parecida com muito menos dados.

## Criptografia
A cifra de Hill criptografa blocos de texto multiplicando por uma matriz módulo 26 — e só funciona se a matriz for invertível módulo 26 ([[Matriz Inversa]]).

## Desempenho
Bibliotecas como BLAS/LAPACK (por baixo de NumPy, MATLAB, PyTorch) são otimizadas ao extremo e usam instruções vetoriais (SIMD) e GPUs. Prefira operações matriciais prontas a laços escritos à mão. Conexão com baixo nível: [[04_Avancado/SIMD|SIMD no vault de Assembly]].

## Receitas em NumPy
```python
import numpy as np

A = np.array([[4, 1],
              [2, 3]])
b = np.array([5, 6])

A @ A                      # produto matricial (A * A seria elemento a elemento)
A.T                        # transposta
np.linalg.det(A)           # determinante
np.linalg.inv(A)           # inversa
np.linalg.solve(A, b)      # resolve A x = b (prefira a inv(A) @ b)
np.linalg.matrix_rank(A)   # posto

vals, vecs = np.linalg.eig(A)   # autovalores e autovetores (colunas de vecs)

# mínimos quadrados: ajustar y = c + d t
t = np.array([0, 1, 2]); y = np.array([1, 2, 2])
X = np.column_stack([np.ones_like(t), t])
coef, *_ = np.linalg.lstsq(X, y, rcond=None)   # [7/6, 1/2]
```
Tente reproduzir à mão os exemplos das outras notas e conferir com o código — é um ótimo exercício.

## Conexões
[[Matrizes]] · [[Autovalores e Autovetores]] · [[Diagonalização]] · [[Transformações Lineares]] · [[Álgebra Linear - Índice]]
