# MAC0329
Computador de 8 bits no Logisim
Victor Aliende da Matta          9298145
Daniel Alves Rodrigues           9298083
Andre Victor dos Santos Nakazawa 9298336
Victor Domiciano Mendonca        8641963

O computador funciona usando duas fase:
1- A instrução apontada pelo PC é carregada no IR.
2- A instrução no IR é decodificada pelo Control e executada, caso ela não mude 
o PC, ele é incrementado.

A decodificação da instrução é feita através de 5 flags:
end - é ativada quando a instrução de encerramento do programa é encontrada
select-pc - seleciona de onde vira a atualização do PC (incrementação ou inserção
de um novo valor). Note que o PC sempre é atualizado.
store-ram - habilita que a instrução escreva alguma coisa na RAM.
load-ram - habilita que a instrução leia alguma coisa da RAm.
store-acc - habilita que a instrução escreva alguma coisa no acumulador.
