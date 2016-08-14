---
layout: post
title:  "Mudar permissões com chmod somente em arquivos ou somente em pastas"
date:   2014-07-24 00:00:00 -0300
tags:
- Linux
- shell script

---
Definitivamente, tem comandos bem simples que quando precisamos, nos fogem à memória. Esses 2 casos são clássicos para mim, então para evitar de ter que procurar volta e meia, vou colocar aqui, e em português, pois só encontro em inglês(e infelizmente muita gente que trabalha com TI no Brasil ainda não aceitou que tem que saber inglês para trabalhar nessa área), para ajudar a mim e a quem mais resolver Googlar isso.

Ao entrarmos em uma pasta, se quisermos mudar a permissão de todas as pastas abaixo desse diretório, usamos o seguinte comando:

`find . -type d -exec chmod 755 \"{}\" \;`

Não preciso dizer que se não quiser 755, basta mudar, certo? Obs: precisa da contra-barra no final mesmo, e as demais contra-barras são para garantir que funcione quando o nome da pasta tiver espaço(por favor, evitem isso, inclusive).

E da mesma forma, para alterar todos os arquivos abaixo desse diretório, use o seguinte comando:

`find . -type f -exec chmod 644 {} \;`

<div>Tá, mas o que é isso, afinal?</div>

<div>O comando "find" serve para buscar arquivos, então você passa o parâmetro "-type f"(olha que incrível, "f" de file!) para indicar somente arquivos, ou "-type d"(olha que incrível again, "d" de directory!), e ai com o resultado dessa busca, executa um comando especificado pelo parâmetro "-exec", que no caso acima é "chmod 644" no caso dos arquivos e "chmod 755" no caso das pastas. O "{}" é para indicar ao "chmod" que ele deve executar em cima do conjunto que vier como output do find.</div>

A propósito, me baseei nesse post: [http://movabletripe.com/archive/recursively-chmod-directories-only/](http://movabletripe.com/archive/recursively-chmod-directories-only/)