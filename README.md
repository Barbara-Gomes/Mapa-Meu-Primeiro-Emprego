# :globe_with_meridians: Mapa de Unidades [Qualifica-SP / Meu Primeiro Emprego]

## Qualifica-SP / Meu Primeiro Emprego
O Meu Primeiro Emprego é um programa de qualificação profissional gratuito, destinado a jovens entre 16 e 24 anos com Ensino Fundamental Completo. Uma iniciativa do Governo do Estado de São Paulo para impulsionar este público a alcançar sua primeira oportunidade no mercado de trabalho. Os cursos acontecem em instituições técnicas públicas e privadas de todo o estado, alcançando todas as Regiões Administrativas de São Paulo.

## Necessidades do projeto
Devido à amplitude do programa, era necessário criar uma ferramenta de busca das unidades, de modo que os candidatos pudessem visualizar quais estavam mais próximas de seu endereço. A direção técnica do programa sugeriu a utilização da ferramenta Google Maps, para que o mapa interativo pudesse ser armazenado em uma pasta pública, que continha os demais materiais sobre o programa.

## Objetivo
* Manipular dados extraídos via SGCP da base de dados da Coordenadoria de Ensino Técnico, Tecnológico e Profissionalizante (CETTPRO).
* Criar um arquivo .xlsx com os dados formatados e realizar o upload no Google Maps.

## 📝 Solução
**1. Conferimos os dados, verificando possíveis lacunas e erros.**
* Nessa fase, optamos por localizar e substituir as células que indicavam o turno das turmas, que estavam apenas indicadas pela primeira letras Manhã (M); Tarde (T); Noite (N); Integral (I).

**2. Criamos uma tabela (BASE MAPA) com três colunas, indicando (I) Nome da Unidade; (II) Nome e horário dos cursos ofertados na Unidade; (III) Endereço.**

(I) Nome da Unidade:
* Copiamos a coluna com os nomes das unidades em uma nova planilha (BASE MAPA) e excluímos as duplicatas.

(II) Nome e horário dos cursos ofertados na unidade:
> Era necessário unir todos os cursos ofertados na unidade, junto aos seus turnos, em uma só célula. Os dados estavam separados em 3 colunas: (I) Nome da Unidade, (II) Nome do curso e (III) Turno.
* Reunimos nome do curso e o turno em uma célula, utilizando a função CONCAT. > =CONCAT(F5, " -", " Período: ",G5);
* Geramos uma tabela dinâmica em nova planilha (UNIÃO TEXTO), indicando o resultado do nome + turno nas linhas e nos valores (contagem); e o nome das unidades nas colunas;
* Copiamos a tabela dinâmica e colamos somente os valores abaixo;
* Utilizamos a função SE para substituir os valores pelos nomes dos cursos; =SE(B5=1,$A5,"")
* Após, unimos todos os valores correspondentes à unidade em uma célula, com as funções CONCAT e UNIRTEXTO; =CONCAT(UNIRTEXTO("; ",,B72:B135),".")
* Nomeamos a tabela com os textos reunidos como "uniaotexto";
* Por último, utilizamos a função PROCH para localizar o resultado correspondente à unidade e fazer referência na planilha (BASE MAPA). =PROCH(A3,uniaotexto,67,0)
  
III. Endereço:
*O endereço estava separado em 4 colunas: Rua, Número, Bairro e Cidade. Por isso, utilizamos em uma só fórmula as funções CONCAT e UNIRTEXTO, para simplificar o processo de formação da frase, introduzindo a pontuação necessária simultaneamente à união do texto. =CONCAT(UNIRTEXTO(", ",,I5,K5),". ",UNIRTEXTO(", ",,J5,L5),".")

**3. Copiamos apenas os valores de BASE MAPA em uma nova pasta de trabalho, e realizamos o upload da base no Google Maps.**
