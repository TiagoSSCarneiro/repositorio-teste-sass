# Sass e Scss

- 1️⃣ INTRODUÇÃO
    
    ### 🎨 É um pré processador do CSS que usa:
    
    - Variáveis
    - Mixins
    - Nesting
    - Heranças
    
    <aside>
    💡 Cria menos código e gera um CSS de qualidade
    
    </aside>
    
    <aside>
    💡 SASS E SCSS são bem parecidos porem o SASS possui mais recursos e tem uma sintaxe mais simples. Ambos tem o mesmo papel: trazer funcionalidades novas ao CSS
    
    </aside>
    
    <aside>
    💡 Comandos para bildar o SASS. 🚨 importante criar duas pastas uma para o CSS e outra para o SASS.
    
    </aside>
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled.png)
    
    📝 comandos para bildar o sass: `sass sass/styles.sass css/styles.css`
    
    ⚠️ Tem que sempre fazer esse comando no terminal quando fizer alguma alteração e for mandar para o css
    
    📝 Para não precisar **sempre** fazer esse comando, escreva no Terminal:
    
     `sass --watch sass/styles.sass:css/styles.css` assim é só recarregar o navegador.
    
    <aside>
    💡 Comando para criar variável: `$nome-da-variavel` essas variáveis podem conter qualquer tipo de comando existente no CSS.
    
    </aside>
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%201.png)
    
- 2️⃣ DIFERENÇA ENTRE O SASS E SCSS
    
    Basicamente a diferença esta na sintaxe.
    
    Enquanto o SASS nao precisa de chaves, ponto e virgula e a identação é feita por TAB
    
    o SCSS usa chaves e dois pontos, como no CSS, com a diferença de identar outro seletor dentro de chaves.
    
    👇 Sintaxe do SCSS
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%202.png)
    
     👇 Sintaxe do SASS
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%203.png)
    
- 3️⃣ COMENTARIOS E COMPRESSÃO DO CSS
    
    existem  maneira de fazer comentário no SASS sem ele aparecer no css:
    
    👉 `//` comenta sem aparecer no css
    
    **dentro da das barras é**
    
    **possível fazer comentário em varias**
    
    **linhas**
    
    `//`
    
    `/*` aparece dentro do arquivo CSS 
    
    `/*!` Também aparece no CSS
    
    🚨 Dentro desses comentários é possível uma interpolação de valores
    
    👉 `#{ 1+3}`  irá aparecer a soma dentro do comentário
    
    ### Compressão do CSS
    
     `sass --watch sass/styles.sass:css/styles.min.css --style compressed` 
    
    💡 Adiciona o “.min” no nome do arquivo com o comando acima no final.
    
    ⚠️ Tem que modificar no index do HTML tbm
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%204.png)
    
    o código vai ser comprimido para diminuir o tamanho e carregar mais rápido a pagina.
    
- 4️⃣ NESTING
    - **POSSIBILIDADE DE ANINHAR SELETORES**
    - **DEIXA MAIS LÓGICA A ESTILIZAÇÃO DE ELEMENTOS POIS SEGUES O PADRÃO DE COMO O HTML ESTA DESENHADO PELAS TAGS**
    - 🚨 TOMAR CUIDADO COM O USO EXESSIVO DE NESTING, PODE CONFUNDIR EM VEZ DE AJUDAR
    
    ⭐ Exemplos:
    
    Aqui o sass esta estilizando somente as tags <p> dentro da div. 
    
    ```html
    <div class="container" >
            <h1>Titulo da pagina</h1>
            <p >Paragrafo 01</p>
            <p>Segundo Paragráfo</p>
        </div>
        <p>
            Paragrafo Tres
        </p>
    ```
    
    ```sass
    div
        background: #494747
    
        p
            color: lightblue
    //Percebe-se que o p esta dentro do escopo da div
    ```
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%205.png)
    
- 5️⃣ NESTING COM LISTA
    
    <aside>
    💡 Nesting em lista é quando vc quer aplicar o mesmo estilo em varios elementos
    
    </aside>
    
    - É separado por virgula:
    
    ⚠️ No primeiro escopo do código as divs e mains e tudo que estiver dentro do escopo será adicionado os estilos
    
    ⚠️Para alterar um elemento especifico dentro de uma tag, após fazer uma lista, é criar um novo escopo.
    
    ```sass
    div, main
        background: #494747
    
        p, h2
            color: lightblue
    
    main
        .cor-vermelha
            color: red
    ```
    
    ```html
    <div class="container" >
            <h1>Dentro da div Container</h1>
            <p >Paragrafo 01</p>
            <p>Segundo Paragráfo</p>
        </div>
        <p>Terceiro Paragrafo fora de qualquer TAG</p>
        <div>
            <p>Quarto paragrafo</p>
            <p>Quinto paragrafo</p>
        </div>
        <main>
            <h2>Dentro da Tag Main</h2>
            <p class="cor-vermelha">Teste Paragrafo</p>
            <p>Segundo Teste</p>
        </main>
    ```
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%206.png)
    
- 6️⃣ NESTING COM COMBINATORS
    
    Os símbolos de **combinators (+, >, ~)** também podem ser usados com o nesting
    
    O sass consegue interpretar corretamente o estilo que cada elemento vai receber por meio das combinações.
    
    ```html
    <ul>
            <li>Item1</li>
            <li>Item2</li>
            <li>Item3</li>
        </ul>
        <ol>
            <li>Item4</li>
            <li>Item5</li>
            <li>Item6</li>
        </ol>
    
        <ol>
            <li>Tiago</li>
            <li>Luis</li>
            <li>Roberto</li>
            
        </ol>
    ```
    
    ```sass
    li
        color: purple
    
    ol //Todos os Filhos de ol terao a cor azul
        > li //usando seletor de descedencia
            color: blue  
            font-family: sans-serif
            font-size: 2rem
    ```
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%207.png)
    
- 7️⃣ PARENT SELECTOR
    
    ### Um seletor especial que serve para se referir a um elemento externo/elemento pai
    
    ### Utilizando o símbolo &. Com ele podemos criar `hover` facilmente na mesma regra por exemplo, sem precisar criar uma nova para o efeito.
    
    - 👇 **Exemplo de como usar:**
        
        HTML:
        
        ![Untitled](Sass%20e%20Scs%20cc160/Untitled%208.png)
        
        Sass:
        
        ![Untitled](Sass%20e%20Scs%20cc160/Untitled%209.png)
        
        CSS:
        
        ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2010.png)
        
        💡 Resultado:
        
        ![Untitled](Sass%20e%20Scs%20cc160/Untitled.gif)
        
    
    ### Assim como no `hover`, também da para se referir ao elemento pai seguindo algumas regras de classes, como o primeiro nome da classe filho ser igual a o da classe do pai.
    
    👉 Exemplo: 
    
    No código abaixo, vemos que a div se chama “container” e as classes começam com o mesmo nome.
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2011.png)
    
    No sass fica assim:
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2012.png)
    
    `&-content` é o mesmo que `container-content`
    
    No css fica dessa forma:
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2013.png)
    
- 8️⃣ PARENT SELECTOR COM SUFIXO
    
    ### Podemos utilizar o parent-slector para adicionar sufixos também, desta forma criamos classes variantes e mais complexas de elemento alvo
    
    👉 Exemplo (os nomes das classe nas interfere):
    
    ```sass
    .btn
    	&-sucesso
    	&-perigo
    ```
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2014.png)
    
    Código do resultado acima ☝️
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2015.png)
    
    ![Untitled](Sass%20e%20Scs%20cc160/Untitled%2016.png)