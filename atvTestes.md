##Questoẽs 

Exercício – Particionamento em Classes de Equivalência e Análise do Valor Limite

1) Considere uma função com duas variáveis de entrada: Cliente e Qtd, e uma variável de
saída, Desconto. Cliente pode ser do tipo A, B ou C e Qtd pode variar de 1 a 1000. A
função calcula Desconto de acordo com as seguintes regras:
a. Clientes do tipo A não recebem desconto se no de itens comprados for inferior
a 10; recebem 5% desconto para compras entre 10 e 99 itens; 10% de
desconto acima de 100 itens.

b. Clientes do tipo B recebem 5% de desconto para compras abaixo de 10 itens;
15% de desconto entre 10 e 99 itens; 25% de desconto acima de 100 itens.

c. Clientes do tipo C não recebem desconto se no de itens comprados for inferior
a 10; 20% de desconto entre 10 e 99 itens; 25% de desconto acima de 100
itens.
** Elabore os casos de testes necessários para testar a função acima

2) Desenvolva um caso de uso de incluir contato em uma agenda telefônica. Os dados de
um contato são: Nome, Telefone, email. A inclusão do contato deve seguir as
seguintes regras:
a. Todo contato deve possuir um número telefônico
b. Não pode haver dois contatos com o mesmo número telefônico
c. Um número telefônico deve ter entre 8 e 15 dígitos numéricos
d. Cada contato tem que possuir um email no formato alfanumérico e deve
seguir a regra: *@*.*
** Elabore os casos de testes necessários para este caso de uso.








##Respostas


# Questão 1

variaveis de entrada | Condições | classes validas| classes invalidas
:---------: | :---------: | :---------: | :---------:
|Cliente, qtd|Cliente deve ser do tipo A, B ou C|cliente.type == A ou cliente.type == B ou cliente.type == C| cliente.type != A ou cliente.type != B ou cliente.type != C
||Clientes do tipo A não recebem desconto se no de itens comprados for inferior a 10; recebem 5% desconto para compras entre 10 e 99 itens; 10% de desconto acima de 100 itens.| Cliente.type = A && qtd >= 10 && qtd <= 99 recebe 5%  de desconto ou qtd >= 100 & qtd <= 1000 recebe 10% de desconto| qtd < 0 ou qtd > 1000
||Clientes do tipo B recebem 5% de desconto para compras abaixo de 10 itens; 15% de desconto entre 10 e 99 itens; 25% de desconto acima de 100 itens.| Cliente.type = B && qtd < 10 && qtd > 0 recebe 5% de desconto ou qtd >= 10 && qtd <= 99 recebe 15% de desconto ou qtd >= 100 & qtd <= 1000 recebe 25% de desconto|qtd < 0 ou qtd > 1000|
||Clientes do tipo C não recebem desconto se no de itens comprados for inferior a 10; 20% de desconto entre 10 e 99 itens; 25% de desconto acima de 100| Cliente.type = A && qtd >= 10 && qtd <= 99 recebe 20% de desconto ou qtd >= 100 & qtd <= 1000 recebe 25% de desconto|qtd < 0 ou qtd > 1000
itens.


## Casos de teste Inválidos

Entradas: A, 0

Saída: "Quantidade Inválida"

Entradas: A, 1001

Saída: "Quantidade Inválida"

Entradas: B, 0

Saída: "Quantidade Inválida"

Entradas: B, 1001

Saída: "Quantidade Inválida"

Entradas: C, 0

Saída: "Quantidade Inválida"

Entradas: C, 1001

Saída: "Quantidade Inválida"

Entradas: D(ou qualquer outra letra do alfabeto), 250

Saída: "Tipo Inválido"

Entradas: D(ou qualquer outra letra do alfabeto), 0

saída: "Tipo e Quantidade Inválidos"

Entradas: D(ou qualquer outra letra do alfabeto), 1001

saída: "Tipo e Quantidade Inválidos"



## Casos de teste Válidos

Entradas: A, 8

Saída: "O cliente não receberá desconto"

Entradas: A, 50

Saída: "Desconto de 5%"

Entradas: A, 300

Saída: "Desconto de 10%"

Entradas: B, 8

Saída: "Desconto de 5%"

Entradas: B, 50

Saída: "Desconto de 15%"

Entradas: B, 300

Saída: "Desconto de 25%"

Entradas: C, 8

Saída: "O cliente não receberá desconto"

Entradas: C, 50

Saída: "Desconto de 20%"

Entradas: C, 300

Saída: "Desconto de 25%"










#Questão 2


| Variáveis de entradas | condições | Classes válidas | Classes inválidas | 
|:--------:|:--------:|:--------:|:--------:|
|Nome, Telefone, email | Todo contato deve possuir um número telefônico | Telefone !=  null && Telefone != ''  | Telefone ==  null && Telefone == '' 
| | Não pode haver dois contatos com o mesmo número telefônico | for contato in contatos: contato.Telefone != Telefone | for  contato in contatos: contato.Telefone == Telefone
| | Um número telefônico deve ter entre 8 e 15 dígitos numéricos | Telefone.length >= 8 && Telefone.length <= 15 | Telefone.length < 8 or Telefone.length > 15 |
| | Cada contato tem que possuir um email no formato alfanumérico e Cada contato tem que possuir um email no formato alfanumérico e deve seguir a regra: *@*.* | email.match( "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,64}") == true  | email.match( "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,64}") == false

## casos de teste invalidos

**Valor máximo do número**
entradas: predo, predo@.*predocom, 9988776655443322

saida: "Número inválido"

**Valor minimo do número**
entradas: predo, predo@.*predo.com, 99876543

saida: "Número inválido"

**Valor telefone  vazio**
entradas: predo, predo@.*predo.com,

saida: "Número inválido"

**número  já cadastrado**
entradas: predo, predopredo@.*com, 99553188

saida: "número telefone ja cadastrado"


**Email invalido**

entradas: predo, predopredocom, 99553188

saida: "email invalido"


entradas: predo, predo@predo.com, 99553188

saida: "email invalido"


entradas: predo, predo@.predo.com, 99553188

saida: "email invalido"


entradas: predo, predo@*predo.com, 99553188

saida: "email invalido"


entradas: predo, predo.*predo.com, 99553188

saida: "email invalido"

entradas: predo, predo.predo.com, 99553188

saida: "email invalido"

entradas: predo, predo@.*predo, 99553188

saida: "email invalido"


## casos de teste validos

**valor do número valido**
entradas: predo, predo@.*predo.com, 99553188

saida: "contato cadastrado"

**email valido**
entradas: predo, predo@.*predo.com, 99553188

saida: "contato cadastrado"


**telefone ainda não cadastrado**
entradas: predo, predo@.*predo.com, 99553179

saida: "contato cadastrado"






















