# Implementação de uma nova função no Processador ICMC
Implementação de uma nova função no Processador ICMC para a disciplina de Organização de Computadores Digitais, por Aríthissa Vitória, João Pedro de Andrade e Lucas Silva Neves.

Foi desenvolvida uma nova função que executa a operação lógica NAND, sendo esta responsável pela negação da operação lógica AND, já presente no Processador.
A partir desta ideia, foram implementadas no código do processador as definições e operações necessárias para o funcionamento da função, utilizando como parâmetro as funções já existentes.

*Vídeo Explicativo: https://drive.google.com/file/d/1l9sSNHG-KI2eRLRL4cDh3ndIizlBbho_/view?usp=sharing

## Alterações:
**•	Defs.h**
*Linha 104:* Foi implementada a definição de NAND_CODE através de um define com valor 98;
*Linha 136:* Definição do valor binário “010111” para LNAND;
*Linha 217:* Definição de NAND_STR, para que o montador reconheça o comando NAND.
**•  Montador.c**
*Linha 207:* Definição da instrução NAND_CODE;
*Linha 845:* Desenvolve as instruções do case NAND_CODE;
*Linha 2300:* Se a instrução inserida for NAND_STR, a instrução NAND_CODE é retornada.
**•	Mneumonicos.h**
*Linha 22:* Define LNAND com o valor 23.
**•	View.cpp**
*Linha 239:* Executa o comando sprintf para a instrução LNAND.
**•	Model.cpp**
*Linha 565:* Desenvolve a instrução LNAND.
**•	Simple_simulator.c**
*Linha 80:* Insere a definição da instrução lógica LNAND com valor 23;
*Linha 952:* Se a operação for LNAND, executa a instrução armazenando o resultado.

## Funcionamento:
O funcionamento da função de operação lógica NAND ocorre de maneira semelhante às demais funções lógicas já presentes no Processador (AND, OR e XOR), que percorrem os mesmos caminhos apesar de executarem diferentes tarefas.
Dentre os 7 registradores presentes na arquitetura do processador, a função NAND utiliza 3 deles para funcionar corretamente, sendo estes, por exemplo, RX, RY e RZ. A partir dos valores armazenados nos registradores RY e RZ, selecionados a partir dos multiplexadores M3 e M4, a função NAND executa e armazena no registrador RX o valor resultante retornado pela mesma, após a chamada da função ser reconhecida pelo MC e sua operação feita pela ULA (Unidade Lógica Aritmética). Este valor passa pelo multiplexador M2 antes de ser armazenado no registrador RX, e o processador também utiliza o multiplexador M6 que é responsável por controlar as passagens para o FG (Flag-Register). A execução da função NAND é encerrada quando o registrador RX recebe o valor resultante da operação.
