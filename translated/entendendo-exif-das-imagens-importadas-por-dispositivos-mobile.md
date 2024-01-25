Durante estes dias, eu estive desenvolvendo uma *feature* relacionada a importação de imagens. Estava tudo funcionando perfeitamente no computador, os conteúdos hospedados no amazon s3 estavam com as mesmas propriedades antes de serem redirecionados. **Aparentemente não havia nenhum problema....**

Quando essa *feature* foi testada no celular, surgiu um belo de um erro para o usuário, caso o mesmo estivesse utilizando um dispositivo móvel. 

A imagem simplesmente girava 90 graus para direita toda vez que uma foto fosse tirada com o celular na posição vertical.

Ou seja, uma imagem assim:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652826386778/SU5DZUzkq.png align="left")

Seria renderizada assim:


![gira.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1652826537385/LsPDU8l4O.jpeg align="left")


Bom, eu fui atrás de uma resposta e, como você está lendo isso, deve imaginar que eu consegui. Certo? 

Após esse evento, decidi compartilhar essa situação para servir de apoio e orientar o desenvolvedor para algumas soluções que acabei encontrando no caminho.

## Entendendo o problema

A imagem foi rotacionada porque a maioria das câmeras de celulares são mantidas no formato paisagem. Então, por mais que o celular estivesse em uma posição vertical, a foto automaticamente seria rotacionada em 90 graus.

Para que a foto fique no mesmo formato de quando é tirada por um dispositivo móvel, é necessário que os dados da imagem sejam mutáveis para indicarmos a orientação correta.

## O que seria essa mídia mutável e como enviar os dados com a informação correta?

Quando alguma foto é extraída de uma câmera de um dispositivo móvel, são registrados alguns metadados que contém informações sobre essa mídia, que podem ser o tamanho, a dimensão, o local, orientação, etc. Esse conjunto de metadados é chamado EXIF (Exchangeable image file format).

Através do EXIF, é possível recuperar as informações da foto e alterá-las conforme o objetivo. É exatamente isso que precisamos fazer para solucionar o problema da orientação.


Existem diversas formas de conseguir a orientação da imagem e convertê-la para o alinhamento desejado. Abaixo, indicarei alguns links que podem te ajudar caso esteja passando pelo mesmo problema, pois cada solução depende muito da stack de tecnologias que você esteja utilizando.


### Primeira Sugestão  

Esse [post](https://medium.com/wassa/handle-image-rotation-on-mobile-266b7bd5a1e6) me ajudou muito a entender o que estava acontecendo e, além disso, o redator deixa a solução que ele resolveu em código. Inclusive, você pode utilizar alguma biblioteca que retorne a orientação da imagem  como [essa](https://www.npmjs.com/package/get-orientation) e combinar com código do post, tornando-o menor.

### Segunda Sugestão  

Existe também essa [solução](https://github.com/digital-flowers/loadimage-exif-example),  gerada através de uma resposta no stackoverflow. No arquivo "upload.html", existe um script que utiliza duas bibliotecas bem conhecidas para a função. 

### Terceira e Última Sugestão  

 Caso esteja utilizando alguma biblioteca que lide com operações em imagens, certifique-se que essa ferramenta não tenha alguma solução para a orientação. No meu caso, já estava utilizando a biblioteca    [sharp](https://sharp.pixelplumbing.com/) para fazer a compressão das mídias e, pesquisando um pouco mais, acabei percebendo que eles já lidavam com esse [problema](https://sharp.pixelplumbing.com/api-operation#rotate).


Espero que esse post tenha contribuído de alguma forma para o seu desenvolvimento!




