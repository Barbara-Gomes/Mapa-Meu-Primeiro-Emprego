# :globe_with_meridians: [Mapa de Unidades de Ensino [Qualifica-SP | Meu Primeiro Emprego]](https://www.google.com/maps/d/viewer?mid=12RUAzUv6WmHTARlDRou9O-hRUbQZXlw&ll=-22.48585463669992%2C-48.19047089999999&z=7)
<div align="justify">
  
## Qualifica-SP | Meu Primeiro Emprego
O Meu Primeiro Emprego é um programa de qualificação profissional gratuito, destinado a jovens entre 16 e 24 anos com Ensino Fundamental Completo. Uma iniciativa do Governo do Estado de São Paulo para impulsionar este público a alcançar sua primeira oportunidade no mercado de trabalho. Os cursos acontecem em instituições técnicas públicas e privadas de todo o estado, alcançando todas as Regiões Administrativas de São Paulo.

## Necessidades do Projeto
Devido à amplitude do programa, era necessário criar uma ferramenta de busca das unidades, de modo que os candidatos pudessem visualizar quais estavam mais próximas de seu endereço. A direção técnica do programa decidiu utilizar a ferramenta Google Maps, para que o mapa interativo pudesse ser armazenado em uma pasta pública, junto aos demais materiais sobre o programa.

## Objetivos
* Manipular dados extraídos via SGCP da base de dados da Coordenadoria de Ensino Técnico, Tecnológico e Profissionalizante (CETTPRO).
* Criar um arquivo .xlsx com os dados formatados e realizar o upload no Google Maps.

## 📝 Solução
**:white_check_mark: Conferimos os dados, verificando possíveis lacunas e erros.**
* Nessa fase, optamos por localizar e substituir as células que indicavam o turno das turmas, que estavam apenas indicadas pela primeira letra Manhã (M); Tarde (T); Noite (N); Integral (I).

**:white_check_mark: Criamos uma tabela (BASE MAPA) com três colunas, indicando (I) Nome da Unidade; (II) Nome e horário dos cursos ofertados na Unidade; (III) Endereço.**

**(I) Nome da Unidade:**
* Copiamos a coluna com os nomes das unidades em uma nova planilha (BASE MAPA) e excluímos as duplicatas.

**(II) Nome e horário dos cursos ofertados na unidade:**
> Era necessário unir todos os cursos ofertados na unidade, junto aos seus turnos, em uma só célula. Os dados estavam separados em 3 colunas: (i) Nome da Unidade, (ii) Nome do curso e (iii) Turno.
* Reunimos nome do curso e o turno em uma célula, utilizando a função CONCAT.
  > =CONCAT(F5, " -", " Período: ",G5)
* Geramos uma tabela dinâmica em nova planilha (UNIÃO TEXTO), indicando o resultado do nome + turno nas linhas e nos valores (contagem); e, nas colunas, o nome das unidades.

* Copiamos a tabela dinâmica e colamos somente os valores abaixo.

* Com a função SE, substituímos os valores "1" pelos nomes dos cursos;
  > =SE(B5=1,$A5,"")
* Após, unimos todos os valores correspondentes à Unidade de Ensino em uma célula, com as funções CONCAT e UNIRTEXTO.
  > =CONCAT(UNIRTEXTO("; ",,B72:B135),".")
* Nomeamos a tabela com os textos reunidos como "uniaotexto".

* Por último, utilizamos a função PROCH para localizar o resultado correspondente à Unidade de Ensino e fazer referência na planilha BASE MAPA. 
  > =PROCH(A3,uniaotexto,67,0)
  
**(III). Endereço:**
* O endereço estava separado em 4 colunas: Rua, Número, Bairro e Cidade. Por isso, utilizamos em uma só fórmula as funções CONCAT e UNIRTEXTO, para simplificar o processo de formação da frase, introduzindo a pontuação necessária simultaneamente à união do texto. 
 > =CONCAT(UNIRTEXTO(", ",,I5,K5),". ",UNIRTEXTO(", ",,J5,L5),".")

**:white_check_mark: Copiamos apenas os valores de BASE MAPA em uma nova pasta de trabalho, e realizamos o upload da base no Google Maps.**
<div>
  
<div align="right">

  [Acesse aqui](https://www.google.com/maps/d/viewer?mid=12RUAzUv6WmHTARlDRou9O-hRUbQZXlw&ll=-22.48585463669992%2C-48.19047089999999&z=7)
<div>
