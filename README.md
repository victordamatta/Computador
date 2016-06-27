# MAC0329
## Computador de 16 bits no Logisim  
Victor Aliende da Matta          9298145  
Daniel Alves Rodrigues           9298083  
Andre Victor dos Santos Nakazawa 9298336  
Victor Domiciano Mendonca        8641963  

### O computador possui 9 módulos:
RAM - módulo principal do computador, armazena o programa a ser executado, assim
como os dados.  
  
PC - Program Counter. Indica o endereço da próxima instrução a ser executada.  
  
Flags - Circuito combinatório que guarda em um registrador de flags as propriedades
do número guardado no acumulador, é usado para as operações de jump condicionais.  
  
ACC - Acumulador. Registrador usado principalmente para a realização das operações
binárias aritméticas e transporte de dados.  
  
IR - Instruction register. Registrador que armazena a instrução a ser executada 
nessa fase.  
  
Control - Circuito combinatório que ativa as flags necessárias para a execução da
instrução armazenada em IR.  
  
ALU - Módulo responsável pelas operações aritméticas.  
  
IO - Pinos de input e output.  
  
Phase Counter - Contador de fase, usado para organizar a ordem das operações do 
computador.  
  
### O computador funciona usando duas fases:  
1- A instrução apontada pelo PC é carregada no IR.  
2- A instrução no IR é decodificada pelo Control e executada, caso ela não mude 
o PC, ele é incrementado.  

### A decodificação da instrução é feita através de 10 flags:  
* run - quando a instrução de encerramento do programa é encontrada, ela é desligada.  
* select-pc - seleciona de onde vira a atualização do PC (incrementação ou inserção
de um novo valor). Note que o PC sempre é atualizado.  
* select-acc - seleciona de onde vira o valor para atualizar o acumulador.  
* select-ram - seleciona de onde vira o valor para atualizar o local da ram de endereço A.  
* store-ram - habilita que a instrução escreva alguma coisa na RAM.  
* store-acc - habilita que a instrução escreva alguma coisa no acumulador.  
* load-ram - habilita que a instrução leia alguma coisa da RAM.  
* print - indica que a instrução é de impressão.  
* alu - indica que a instrução é uma operação aritmética.  

O módulo Control também determina o endereço (address) associado as instruções e, no caso,
das operações aritméticas, ele indica qual operação será feita (op). Ele foi implementado
identificando padrões que englobam todas as intruções relevantes para uma determinada flag.  

### Conjunto de instruções:

11 0x0B {LDA} XX    `[XX] -> Acc`  
12 0x0C {STA} XX    `[Acc] -> XX`  
  
21 0x15 {ADD} XX    `[Acc] + [XX] -> Acc`  
22 0x16 {SUB} XX    `[Acc] - [XX] -> Acc`  
23 0x17 {MUL} XX    `[Acc] * [XX] -> Acc`  
24 0x18 {DIV} XX    `[Acc] / [XX] -> Acc`  
25 0x19 {REM} XX    `[Acc] % [XX] -> Acc`  
  
31 0x1F {INN} XX    `in > XX`  
41 0x29 {PRN} XX    `[XX] > out`  
  
50 0x32 {NOP}  
51 0x33 {JMP} XX    `[XX] -> PC`  
52 0x34 {JLE} XX    `([Acc] <= 0): [XX] -> PC`  
53 0x35 {JDZ} XX    `([Acc] != 0): [XX] -> PC`  
54 0x36 {JGT} XX    `([Acc] > 0): [XX] -> PC`  
55 0x37 {JEQ} XX    `([Acc] == 0): [XX] -> PC`  
56 0x38 {JLT} XX    `([Acc] < 0): [XX] -> PC`  
57 0x39 {JGE} XX    `([Acc] >= 0): [XX] -> PC`  
  
70 0x46 {STP}       `.`  

