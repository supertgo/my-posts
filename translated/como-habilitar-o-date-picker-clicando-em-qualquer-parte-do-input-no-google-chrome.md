Alguns dias atrás recebi uma sugestão de melhoria em uma tela que usava HTML puro. Após solucionar o problema, decidi compartilhar caso alguém passe pela mesma situação.

Basicamente, o usuário do chrome só habilitava o date picker quando o ícone de calendário fosse clicado, gerando uma má impressão no layout e possivelmente o confundindo.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671572602774/DkErdJKUL.gif align="center")

<center>Exemplo do funcionamento do input nativamente</center>

Como o ícone não era muito importante para a aplicação, ele foi utilizado como solução. Com o css abaixo, o calendário ocupa toda a largura e altura do input, dessa maneira, qualquer lugar clicado irá acionar o date picker.

```css
input[type="date"] {
    position: relative;
}
/* css para que modifica o layout do calendário */
input[type="date"]::-webkit-calendar-picker-indicator {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: auto;
    height: auto;
    color: transparent;
    background: transparent;
}
```

É importante se atentar com as propriedades de largura(**width**) e altura(**height**). É possível que ambas em **100%** funcione dependendo da presença de bordas no input. Outra tag que também pode influenciar no comportamento é a **box-sizing**.

Para mais informações, recomendo a leitura [dessa resposta](https://www.quora.com/What-does-width-100-do-in-CSS) que explica sobre a porcentagem aplicada aos elementos css.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671574716202/MqeC5ymWu.gif align="center")

<center>Funcionamento após as alterações css</center>
