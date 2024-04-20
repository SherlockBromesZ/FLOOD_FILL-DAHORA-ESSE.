# Tutorial de Flood Fill em C++

## Introdução
O algoritmo de Flood Fill é uma técnica de preenchimento de áreas conectadas em uma matriz bidimensional. É comumente usado em programas de edição de imagens para preencher uma área com uma cor específica, mas também tem outras aplicações, como em jogos para determinar áreas acessíveis.

## Como Funciona
O Flood Fill começa em um ponto específico e se espalha para as células adjacentes que têm o mesmo valor da célula inicial. O algoritmo continua se espalhando até que não haja mais células adjacentes válidas para preencher.

## Implementação em C++
A seguir, está a implementação do algoritmo de Flood Fill em C++. Este código preenche todas as células conectadas que não são obstáculos (representados por '#') a partir de uma posição inicial com um caractere de preenchimento (neste caso, 'D').

```cpp
#include<bits/stdc++.h>
using namespace std;

void floodFill(vector<vector<char>> &grid, int x, int y, char preenchimento){
    if(x < 0 || x >= grid.size() || y < 0 || y >= grid[0].size() || grid[x][y] != '.'){
        return;
    }
    
    grid[x][y] = preenchimento;
    
    floodFill(grid, x + 1, y, preenchimento);
    floodFill(grid, x - 1, y, preenchimento);
    floodFill(grid, x, y + 1, preenchimento);
    floodFill(grid, x, y - 1, preenchimento);
}

int main()
{
    int linhas, colunas;
    cin >> linhas >> colunas;
    
    vector<vector<char>> grid(linhas, vector<char>(colunas));
    
    for(int i = 0; i < linhas; i++){
        for(int j = 0; j < colunas; j++){
            cin >> grid[i][j];
        }
    }
    
    floodFill(grid, 0, 0, 'D');
    
    for(int i = 0; i < linhas; i++){
        for(int j = 0; j < colunas; j++){
            cout << grid[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

## Exemplo de Entrada e Saída
**Entrada:**
```
5 6
. . # . . .
. # . . # .
. # # . . .
. . # # # .
. . . . . #
```

**Saída:**
```
D D # . . . 
D # . . # . 
D # # . . . 
D D # # # . 
D D D D D #
```
